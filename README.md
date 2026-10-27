# Nuki Hub preview builds

Test builds from the `preview-all` branch of this fork: upstream master as of 2026-10-27 (9.19 code base) plus the web configurator refactor, the redesign with setup wizard and the Nuki Bridge HTTP API. Not a release. Settings, pairing and Wi-Fi survive flashing over 9.18 or 9.19.

Source commit: `278e97e8` (https://github.com/sjors-lemniscap/nuki_hub/tree/preview-all)

## Plain ESP32 (4 MB, PSRAM)

- Full set for USB flashing: [NukiHub-preview-all-esp32-278e97e8.zip](NukiHub-preview-all-esp32-278e97e8.zip), see `how-to-flash.txt` inside.
- Main firmware only, for an over-the-air update from a running 9.19: [esp32/nuki_hub_esp32.bin](esp32/nuki_hub_esp32.bin). On the hub open Advanced Configuration (`/get?page=advanced`), set "Custom URL to update Nuki Hub" to the raw link below, save and reboot.

```
https://raw.githubusercontent.com/sjors-lemniscap/nuki_hub/preview-binaries/esp32/nuki_hub_esp32.bin
```

USB flash command:

```
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 921600 --before default-reset --after hard-reset write-flash -z --flash-mode dio --flash-freq keep --flash-size detect 0xe000 boot_app0.bin 0x1000 nuki_hub_bootloader_esp32.bin 0x10000 nuki_hub_esp32.bin 0x270000 nuki_hub_updater_esp32.bin 0x8000 nuki_hub_partitions_esp32.bin
```

## Branches under review

1. https://github.com/sjors-lemniscap/nuki_hub/tree/refactor-split-web-configurator
2. https://github.com/sjors-lemniscap/nuki_hub/tree/refactor-ha-entity-tables
3. https://github.com/sjors-lemniscap/nuki_hub/tree/refactor-shared-command-handlers
4. https://github.com/sjors-lemniscap/nuki_hub/tree/refactor-settings-tables
5. https://github.com/sjors-lemniscap/nuki_hub/tree/redesign-web-configurator
6. https://github.com/sjors-lemniscap/nuki_hub/tree/add-nuki-bridge-http-api
