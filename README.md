# ASCII Aquarium CYD

A tiny animated ASCII fish tank for the ESP32-2432S028R "Cheap Yellow Display".

ASCII Aquarium CYD turns the common 320x240 CYD touchscreen into a living little
desktop aquarium with swimming ASCII fish, rising bubbles, swaying seaweed,
tap-to-feed flakes, occasional octopus and seahorse visitors, touch controls,
Wi-Fi time sync, persistent settings, and SD-card screenshot capture.

It is not a video loop. The aquarium is rendered live on the ESP32, with fish
that wander, school, turn around, change brightness, avoid each other, and chase
food when you tap the glass.

## Web Flasher

The easiest way to install ASCII Aquarium CYD is with the browser flasher:

[Flash ASCII Aquarium CYD](https://power-pill.github.io/ascii-aquarium-cyd/)

You will need:

- A supported CYD board connected by a USB data cable.
- Chrome or Edge on a desktop computer.
- The Arduino IDE Serial Monitor closed, if it was open.

Open the flasher page, click **Flash ASCII Aquarium**, choose the CYD serial
port, and let the installer finish.

## Supported Hardware

This firmware is built for the ESP32-2432S028R "Cheap Yellow Display" board:

- ESP32
- ILI9341 320x240 display
- XPT2046 resistive touchscreen
- Optional SD card support for BMP screenshots and frame capture

Other CYD-style boards may look similar but use different display, touch, or SD
hardware. They may need code changes before flashing.

## Features

- Animated ASCII fish with multiple glyph species, varied colors, depth shading,
  smooth wraparound, schooling, wandering, and separation behavior.
- Tap-to-feed flakes that nearby fish chase down.
- Configurable fish population from 6 to 36.
- Configurable bubble count from 0 to 50.
- Animated bubbles and seaweed with adjustable sway, length, and randomness.
- Visiting octopus and seahorse characters with selectable spawn rates.
- Fish steer around visitors and each other.
- Background styles: black, blue fade, purple fade, and randomized pixel-art
  flower backdrop.
- Touch settings menu with Tank, Seaweed, Clock, and Background tabs.
- Optional on-screen clock with manual time or internet time.
- 12-hour and 24-hour clock formats.
- Timezone selection, small top or bottom clock, large ASCII clock style, and
  clock color picker.
- Wi-Fi panel with network scan, saved credentials, on-screen keyboard,
  reconnect handling, and NTP time sync.
- Persistent settings using ESP32 Preferences.
- SD-card BMP screenshots and frame sequence capture.
- Hidden HUD controls for setup, capture, Wi-Fi, settings, quick creature tests,
  respawn, and randomize.
- Double-buffered sprite rendering for smoother animation.

## Basic Controls

- Tap the tank to drop food.
- Tap the top-left corner to reveal the hidden HUD.
- Use the settings panel to tune fish, bubbles, visitors, seaweed, clock, and
  backgrounds.
- Use the Wi-Fi panel to connect to a network and sync internet time.
- Use the capture panel or BOOT button to save BMP screenshots to SD.

## Build From Source

The main Arduino sketch lives here:

```text
ASCII_Aquarium/ASCII_Aquarium_CYD/ASCII_Aquarium_CYD.ino
```

The sketch expects the CYD display and touch configuration used by the included
TFT_eSPI setup files:

```text
ASCII_Aquarium/User_Setup.h
ASCII_Aquarium/User_Setup_Select_CYD.h
```

To build manually:

1. Open `ASCII_Aquarium_CYD.ino` in the Arduino IDE.
2. Select the same ESP32 board/settings used for your CYD.
3. Make sure TFT_eSPI is using the included CYD setup.
4. Compile and upload through the Arduino IDE.

For browser flashing releases, use Arduino IDE's **Export Compiled Binary** and
publish the generated merged firmware binary.

## Release Firmware

For GitHub Pages / ESP Web Tools flashing, use the merged binary exported by the
Arduino IDE:

```text
ASCII_Aquarium_CYD.ino.merged.bin
```

Rename it with the release version, for example:

```text
ascii-aquarium-cyd-v1.66.bin
```

Then place it under the web flasher firmware folder and point the ESP Web Tools
manifest at it with offset `0`.

## Project Notes

ASCII Aquarium CYD is part clock, part screensaver, part tiny art object, and
part excuse to make fish-shaped punctuation swim around like it has somewhere
important to be.

No water changes. No tank cycling. No surprise snails. Just plug it in and let
the current take care of itself.
