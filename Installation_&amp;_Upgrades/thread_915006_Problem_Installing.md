---
title: "Problem Installing"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by tkaed on 2008-09-09
Hey guys, 

I originally posted in the beginners section but wasn't getting much help there. Can you guys help me with my install problem.

I downloaded Ubuntu and ran a md5check, then burned the iso to a cd. I ran the cd and the loader seemed to launch fine. After about 2 minutes it went to a black screen and I got this error:

Buffer I/O Error on device fd0, logical block 0

It kept repeating that bunch of times so I just rebooted to windows.

I tried installing with the alternate cd but instead this time I got an error message saying it wasn't reading my cd drive.

Here is a list of my hardware:
ASUS P5Q Pro LGA 775 Intel P45 ATX Intel Motherboard
Intel Core 2 Duo E8400 Wolfdale 3.0GHz
G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1000 (PC2 8000)
SAPPHIRE 100245L Radeon HD 4850 512MB 256-bit
CORSAIR CMPSU-650TX 650W
Western Digital Caviar SE16 WD6400AAKS 640GB 7200 RPM SATA
SAMSUNG 22X DVD±R DVD Burner with LightScribe Black SATA 

I just built this machine a few days ago and installed Vista x64 with no problems. I'd like to try to figure out the fd0 problem, but if there is another way to install and fix that down the line I can do that.

---

### Post by Partyboi2 on 2008-09-09
>  Buffer I/O Error on device fd0, logical block 0 Normally relates to the floppy device.
If you have a floppy drive  try disabling it in the bios another thing you can try is to pass all_generic_ide as a boot option when booting the ubuntu cd. You would do this by pressing F6 at the main menu and adding ```
all_generic_ide
```

---

