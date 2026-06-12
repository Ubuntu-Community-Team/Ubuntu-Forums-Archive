---
title: "Best way to repair (terminal mode?) bootloader causing boot: gfxboot.c32 error msg"
date: 2022-01-14
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2022-01-14
Ok, I just jumped from Ubuntu 14.04 LTS to 20.04 LTS after an extended hiatus from my Linux PC. I used a Live USB zipdrive to install the new OS. Everything went wonderful til the end of the install when I was asked about my partition layout. I wanted to keep my existing partitions with a SWAP file area, etc but screwed up when I told the installer I wanted the mounting point for two of the disk partitions at '/'. The installer locked up on me unfortunately. When I rebooted I had big issues with the BIOS and bootloader. No surprise, huh.

To make a long story short I stumbled around and now have got the PC to boot up and hang at the [boot: gfxboot.c32 not a com32 image] point. 

I can hit the "tab" key and type in "live" (enter) and get to the LiveUSB zipdrive and it finishes booting up in live mode.

Do I need to access terminal mode and make the necessary repairs to the bootloader? Is the "Boot-Repair" utility a good route to proceed with? I just want to clear up this issue in the cleanest fashion possible. 

One more question: If I download software off the web, like Chrome Browser, before I fix this issue will the software be located on the zipdrive or on the hard drive where the install took place? 

thanks for your advice....

---

### Post by ozark_hillbilly on 2022-01-14
Boot-Repair corrected bootloader problem.

---

