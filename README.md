**Pre-Requisites:**
- git installed
- vscode installed, with plugins "Remote Containers", "Cortex-Debug"
- docker installed
- Segger JLink GDB Server

**How to use:**

***Build binary (for the nrf52840dk) ***
1. "git clone git@github.com:stemschmidt/renode-eval.git"
2. "cd renode-eval"
3. "code ." or open renode-eval in VSCode
4. in VSCode, select "reopen folder in container"
5. after docker container has started, go to "TERMINAL" tab:
6. "west init -l application"
7. "west update"
8. "source zephyr/zephyr-env.sh"
9. "cd application"
10. "west build -b nrf52840dk/nrf52840" and wait for the build to finish...

***Flash and debug on board***
1. on the host, launch the JLinkGDBServer (e.g "JLinkGDBServerCLExe -if swd -device nRF52840_xxAA -vd")
2. Select "Run and Debug" icon in activity bar in VSCode --> Download binary and start debugging by launching "JLink"

***Run binary in Renode***
1. "cd .." in the terminal in docker (return to root directory)
2. enter "renode scripts/renode/blinkingLed.resc" -> this uses the nrf52840dk_nrf52840 board
3. at (machine-0) enter "start"
4. to terminate, enter "pause" and then "q"

NOTE: There is an issue with the order in which the plugins are loaded. A warning appears asking you to reload the window. After reloading the window you will have to launch bash again: '$ bash'