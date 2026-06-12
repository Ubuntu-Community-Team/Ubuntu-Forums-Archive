---
title: "Install - Flashing cursor regardless of options"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by myth1914 on 2010-01-19
I've been a Ubuntu user since a flip from FC5, so I've installed it quite a few times.  My current install is somewhat troubling...

Here are the facts:
1. Install on a brand new Via Nano (Isaiah) ITX motherboard
2. 512mb ram (DDR2)
3. 2TB WD (green) HDD

I am attempting to install the OS; however, when I choose anything in the main disk menu, the install hangs with a flashing cursor in the upper left corner.  The disk spins down shortly there after.  I don't know if it's related, but the initial CDrom I used was painfully slow (5 min to load the disk menu)  

Similar hanging happens when trying a disk containing 8.04LTS alternate, 9.10 desktop 32, 9.10 desktop alternate 32 and 64, 9.10 server (preferred) 32 and 64, and while not Ubuntu may contain useful troubleshooting info:  FreeNAS loads but doesn't support long mode even though it is a 64b proc, FreeNAS 32 states "killed" from any menu choice, open filer, and even Fedora 7 fails after any disk menu choice.

What I have attempted to resolve the issue:

1. Boot from USB CDrom
2. Boot from DVDrom (1&2 load the CD normally, but still have the same result)
3. Swapped RAM out
4. Attempted noacpi, nolacpi, expert mode, safe video, etc in every combination I could think of
5. Various bios settings including disabling all controllers not in use (serial etc), fail safe defaults, optimized defaults etc.
6. passing vga=770 to the install, which prompts for a valid video mode, but anything chosen = same result. (640x480 8 included)

I am to the point I think I may have gotten a defective board, but wanted to ask here first.  Thanks in advance for any help!

---

### Post by myth1914 on 2010-01-19
Additional info:

Info on the processor states it has an "out-of-order" processor architecture.  Is there an alternate install mode to accommodate?[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by myth1914 on 2010-02-25
For anyone that runs across this, I never found a solution, so I swapped the motherboard for a different model.

---

