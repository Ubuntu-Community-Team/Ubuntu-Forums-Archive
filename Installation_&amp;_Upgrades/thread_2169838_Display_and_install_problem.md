---
title: "Display and install problem"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by Matt_Sharpe on 2013-08-23
[LEFT][COLOR=#424244]First, the basic system information:[/COLOR]

[COLOR=#424244]Toshiba Satellite A135-S2386 laptop[/COLOR]
[COLOR=#424244]CPU: Dual Intel Pentium Pro, 1733 MHz [/COLOR]
[COLOR=#424244]Mainboard: Toshiba IAYAA[/COLOR]
[COLOR=#424244]BIOS: Phoenix Tech Inc. Ltd (03/06/07)[/COLOR]

[COLOR=#424244]I unearthed an "old" laptop and have been trying to make it usable again. The problems that led to it being replaced in the first place was that it was running too slow, a couple keys came off the keyboard and the battery wasn't holding a charge. The keys I can fix or live without and I can order a new battery but to speed it up, I removed Windows Vista and tried to install a Linux distro (Fedora)...[/COLOR]

[COLOR=#424244]The problem is that it boots fine, shows the splash screen, goes to the initial Linux screen but then it goes to the grey screen (with strands of other colors in both vertical and horizontal lines...hard to describe). [/COLOR]

[COLOR=#424244]What I've tried:[/COLOR]

[COLOR=#424244]1. Restore Vista - wouldn't restore. Tried using the Vista CD to re-install but the code was for a Vista "upgrade" and since there wasn't already a version of windows already installed it wouldn't let me install Vista.[/COLOR]

[COLOR=#424244]2. Since Fedora Linux didn't install, tried a couple other distros booted from either CD or USB. The menu came up (perfect picture) but regardless of whether or not I chose to run from USB or install, the choice led back to the gray screen and stays that way...[/COLOR]

[COLOR=#424244]3. Tried Damn Small Linux (DSL)...it worked! No problem with screen or running programs...even able to get on internet (with Ethernet)...I would like to be able to run an operating system other than DSL (Ubuntu or Lubuntu preferably). [/COLOR]

[COLOR=#424244]4. Connected laptop to a separate monitor and the gray screen came up on Laptop as usual but the picture was just fine on the attached monitor. [/COLOR]

[COLOR=#424244]5. Ran some tests from a bootable USB ("ultimatebootCD")...the following information was obtained, much of it I don't understand but think is possibly relevant: [/COLOR]

[COLOR=#424244]CPUID: 06EC Feature: BFE9FBFFh[/COLOR]
[COLOR=#424244]Memory Size: 1903 MB[/COLOR]
[COLOR=#424244]Memory Bandwith: 3400.12 MB/s[/COLOR]

[COLOR=#424244]VESA OEM Radeon Xpress 200M series[/COLOR]
[COLOR=#424244]VESA memory: 131072 KB (49270 KB/s)[/COLOR]

[COLOR=#424244]Hard drive 0: 74.53 GB[/COLOR]
[COLOR=#424244]Hard drive 1: 7.54 GB (I think this is USB I booted from)[/COLOR]

[COLOR=#424244]CD drive: HL-ST-ST DVDRAM GM-4082N (62x) [/COLOR]

[COLOR=#424244]Mainboard: Toshiba IAYAA[/COLOR]
[COLOR=#424244]BIOS: Phoenix Tech Inc. Ltd (03/06/07)[/COLOR]
[COLOR=#424244]OS: FDh DOS 7.10[/COLOR]

[COLOR=#424244]FPU Type: Built in[/COLOR]
[COLOR=#424244]CPU is in v86 mode: No[/COLOR]

[COLOR=#424244]Processor Benchmark: 1143.57[/COLOR]
[COLOR=#424244]Hard Drive Speed: 733.66[/COLOR]

[COLOR=#424244]CPU stress test: passed several passes[/COLOR]

[COLOR=#424244]AIDA16: [/COLOR]
[COLOR=#424244]Flash ROM: No[/COLOR]
[COLOR=#424244]Intel BIOS Upgrade: Not supported[/COLOR]
[COLOR=#424244]Intel BIOS PNP Auto-Config: Not supported[/COLOR]

[COLOR=#424244]SVGA VESA: Supported [/COLOR]
[COLOR=#424244]v. 2.00 [/COLOR]

[COLOR=#424244]XGA: Not supported[/COLOR]
[COLOR=#424244]SOLLEX: Not supported[/COLOR]

[COLOR=#424244]Video memory: 512 KB [/COLOR]
[COLOR=#424244]SVGA VESA memory: 0 [/COLOR]

[COLOR=#424244]VESA Accelerator Function: Not supported[/COLOR]
[COLOR=#424244]VESA Cursor Interface: Not supported[/COLOR]
[COLOR=#424244]VESA Graphics Sys Config: Not supported[/COLOR]
[COLOR=#424244]VESA OEM Extensions: Not supported[/COLOR]
[COLOR=#424244]VESA XGA BIOS Extensions: Not supported[/COLOR]

[COLOR=#424244]Display Data Channel: Supported[/COLOR]
[COLOR=#424244]Flat Panel Interface: Supported[/COLOR]
[COLOR=#424244]Power Management:Supported[/COLOR]
[COLOR=#424244]SVGA BIOS Ext: Supported[/COLOR][/LEFT]

Someone suggested that I enter "vga=791" in the command line but I don't know how to get to a command line (edit GRUB file? Do I even have a GRUB file if I can't install anything?).

---

