# Ace Combat 3: Electrosphere Recompiled

A native recompilation project for the **original Japanese PlayStation release of *Ace Combat 3: Electrosphere***, powered by **PSXRecomp**.

> **Target version:** Ace Combat 3: Electrosphere (Japan)
> **Platform:** Sony PlayStation
> **Region:** Japan
> **Discs:** 2
> **Status:** Work in Progress

## About

This project aims to bring the original Japanese version of **Ace Combat 3: Electrosphere** to modern PCs through static recompilation.

Rather than emulating the PlayStation CPU in the traditional sense, **PSXRecomp** translates the game's original MIPS R3000A code into native code that can be compiled and executed on modern hardware while recreating the PlayStation hardware environment through the PSXRecomp runtime.

This project specifically targets the **original Japanese two-disc release**.

It does **not** target the North American version of Ace Combat 3.

The Japanese release is important because it contains the game's original two-disc structure, story, characters, cinematics, branching narrative, and other content that was substantially changed for the international release.

## PSXRecomp

This project is built using **PSXRecomp**, created by mstan and maintained as part of the RetroPortingToolKit project.

PSXRecomp provides the PlayStation static recompilation framework, runtime, hardware implementation, project tooling, and other infrastructure that makes projects like this possible.

Upstream project:

https://github.com/RetroPortingToolKit/psxrecomp

Huge credit goes to **mstan** and the **RetroPortingToolKit contributors** for developing and maintaining PSXRecomp.

## Target Game

**Ace Combat 3: Electrosphere**

* Developer: Namco
* Publisher: Namco
* Original platform: Sony PlayStation
* Original release: 1999
* Region: Japan
* Media: 2 CDs
* Target language: Japanese
* Target release: Original Japanese version

Both discs belong to the same recompilation project.

The project is designed around PSXRecomp's multi-disc support rather than treating Disc 1 and Disc 2 as separate games.

## Multi-Disc Support

Ace Combat 3: Electrosphere is a two-disc game.

PSXRecomp's multi-disc configuration is used to register both original discs with the project.

The expected media consists of:

```text
Ace Combat 3 Electrosphere (Japan)[Disc 1].cue
Ace Combat 3 Electrosphere (Japan)[Disc 2].cue
```

Each CUE file must have its corresponding BIN/track files available.

The CUE files are important because they describe the actual CD layout, including tracks and other information required to reproduce the original PlayStation discs correctly.

### Disc Switching

Multi-disc support is still being tested as part of this project.

The project will distinguish between:

* selecting Disc 1 or Disc 2
* booting from the correct disc
* recognizing each disc correctly
* preserving saves between discs
* actual in-game/live disc changes

Do not assume that every form of live disc swapping is functional until it has been tested and documented.

## Current Status

🚧 **Work in Progress**

The initial goals are:

* [ ] Probe and verify Disc 1
* [ ] Probe and verify Disc 2
* [ ] Verify both discs as one game set
* [ ] Generate PSXRecomp project
* [ ] Generate recompiled game code
* [ ] Compile native executable
* [ ] Boot successfully
* [ ] Reach intro
* [ ] Play FMVs correctly
* [ ] Reach main menu
* [ ] Start a new game
* [ ] Reach gameplay
* [ ] Verify aircraft rendering
* [ ] Verify terrain rendering
* [ ] Verify HUD
* [ ] Verify controls
* [ ] Verify audio
* [ ] Verify mission scripting
* [ ] Verify memory-card saving
* [ ] Verify story progression
* [ ] Verify Disc 2
* [ ] Verify multi-disc progression
* [ ] Complete a full playthrough

Compatibility information will be updated as development progresses.

## Development Priorities

The first objective is **accuracy**.

The initial recompilation will target the game's original behavior before enhancements are considered.

The baseline target is:

```text
Original Japanese release
        ↓
Original game behavior
        ↓
4:3 presentation
        ↓
Correct graphics
        ↓
Correct audio
        ↓
Correct timing
        ↓
Correct FMV playback
        ↓
Correct mission behavior
        ↓
Correct save behavior
        ↓
Correct two-disc progression
```

Features such as widescreen, PGXP, higher internal resolutions, texture replacements, increased frame rates, and other enhancements are secondary.

Getting the original game working correctly comes first.

## Areas of Interest

Ace Combat 3 makes extensive use of PlayStation hardware and streaming systems.

Development will pay particular attention to:

* MIPS R3000A execution
* GTE operations
* GPU rendering
* aircraft rendering
* terrain rendering
* HUD and target indicators
* CD-ROM streaming
* XA audio
* SPU audio
* MDEC video decoding
* FMV playback
* DMA
* interrupts
* mission scripting
* dynamic code loading
* executable overlays
* memory cards
* branching story progression
* Disc 1 / Disc 2 differences
* disc transition behavior

## Dynamic Code and Overlays

PSX games can load executable code from disc into RAM while the game is running.

PSXRecomp supports techniques such as **Ahead-of-Time overlay sharding** to identify and compile this dynamically loaded code.

During early development, PSXRecomp's interpreter may temporarily handle code that has not yet been statically recompiled.

The long-term goal is to identify these areas and compile as much of the game's executable code as possible.

The interpreter should be a development safety net rather than the final solution.

## Building

Detailed build instructions will be added as the recompilation becomes stable.

The project uses the modern PSXRecomp game-project layout.

Typical requirements include:

* Git
* Python 3
* CMake
* Ninja
* supported C/C++ compiler or PSXRecomp toolchain

After project generation, PSXRecomp's generated build scripts should be used to configure and compile the project.

On Windows this will generally involve:

```powershell
.\build.ps1
```

Exact instructions may change as development progresses.

## Providing Game Discs

**Game data is NOT included with this repository.**

You must provide your own legally obtained copy of the original Japanese release of **Ace Combat 3: Electrosphere**.

Both discs are required for the complete game.

The recompilation project does not distribute the original PlayStation disc images.

## What Is NOT Included

This repository does **not** provide:

* Ace Combat 3 ROMs
* BIN files
* CUE/BIN disc dumps
* PlayStation BIOS dumps
* copyrighted Namco game assets
* copyrighted Sony firmware

You must provide your own legally obtained game media where required.

## BIOS

PSXRecomp supports its bundled open-source **OpenBIOS** implementation as well as compatible user-provided retail PlayStation BIOS images where supported.

No copyrighted Sony PlayStation BIOS is distributed by this project.

## Repository Structure

The exact structure may evolve during development, but the project follows the modern PSXRecomp layout.

```text
AceCombat3ElectrosphereRecomp/
│
├── game.toml
├── CMakeLists.txt
├── build.ps1
├── README.md
│
├── psxrecomp/
│
├── recomp-ui/
│
├── disc/
│
├── patches/
│
├── mods/
│
└── generated/
```

Local copyrighted disc data should remain excluded from Git.

## Legal

This is an unofficial fan-made preservation and recompilation project.

**Ace Combat 3: Electrosphere**, Ace Combat, and associated characters, artwork, audio, trademarks, and game content belong to **Bandai Namco Entertainment and their respective rights holders**.

PlayStation and associated trademarks belong to **Sony Interactive Entertainment and their respective rights holders**.

This project is not affiliated with, authorized by, sponsored by, or endorsed by Bandai Namco Entertainment or Sony Interactive Entertainment.

No copyrighted game disc images or PlayStation BIOS files are distributed with this project.

## Credits

### Original Game

**Ace Combat 3: Electrosphere**

Developed and published by **Namco**.

### PSXRecomp

Created by **mstan** and developed/maintained with the **RetroPortingToolKit** community.

PSXRecomp provides the static recompilation framework and PlayStation runtime used by this project.

### Recompilation Project

Ace Combat 3: Electrosphere Recompiled is an independent community recompilation project built using PSXRecomp.

## Special Thanks

Special thanks to:

* **mstan**
* **RetroPortingToolKit contributors**
* PSXRecomp contributors
* the PlayStation reverse-engineering community
* the Ace Combat community
* everyone contributing testing, documentation, research, and fixes

---

## Disclaimer

This project exists for software preservation, technical research, and compatibility work.

**Bring your own legally obtained copy of Ace Combat 3: Electrosphere.**

No game disc images are provided.
