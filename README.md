# OverDrive Unit OD-1

An analog guitar overdrive/distortion pedal built around a dual op-amp gain stage and diode clipping.

![Schematic](screenshots/schematic.png)
![Built prototype](screenshots/prototype.png)

## Circuit overview

The signal path follows a classic op-amp overdrive topology, similar in spirit to circuits like the Tube Screamer: an op-amp gain stage feeding a diode clipper, followed by a passive tone filter and a buffered output stage.

- **Input stage** - high impedance input (1 MOhm), AC-coupled with a 100 nF capacitor so the pedal doesn't load down the guitar's pickups.
- **Gain stage** - one half of a TL072 op-amp, with the GAIN pot (100 kOhm) in the feedback path. Gain is adjustable roughly from unity up to around 100x.
- **Clipping stage** - two 1N4148 diodes wired anti-parallel to virtual ground, symmetrically clipping the signal at about +/-0.7 V. This is what generates the overdrive harmonics.
- **Tone stage** - a passive RC low-pass filter with a 100 kOhm TONE pot, shaping the signal from dark to bright.
- **Output stage** - the second half of the TL072 as a buffer/gain stage with the VOLUME pot (100 kOhm log), followed by an output coupling capacitor and a low output impedance (under 1 kOhm) so it can drive an amp or the next pedal in the chain.
- **Power** - runs from a single 9V supply (battery or DC adapter). A resistor divider plus a third TL072 buffer generates a virtual ground at 4.5 V so the op-amps can work single-supply. Current draw is under 10 mA.

Full details, block diagram, and the BOM are in [docs](docs).

## Tools

- KiCad 9.0.5 for schematic capture and PCB layout
- Standard KiCad libraries only (Device, Amplifier_Operational, Diode, Connector, Connector_Audio, power) - no custom parts, so the project opens without missing library errors

## Status

- Schematic: complete, passes ERC with 0 errors and 0 warnings
- PCB layout: complete, 2-layer board, routed
- Physical build: not yet documented - no build photos in this repo yet
- Testing: not yet documented

The `screenshots/` folder is a placeholder for photos of the schematic, PCB render, and (once built) the physical pedal.

Designed in 2026 as a university electronics project.
