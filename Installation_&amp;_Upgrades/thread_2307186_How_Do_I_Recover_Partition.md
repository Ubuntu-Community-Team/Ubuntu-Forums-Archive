---
title: "How Do I Recover Partition?"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by Amr_Elseweifi on 2015-12-22
Yesterday I bought a new Asus K501U laptop (came with Windows 10) with a 256 GB SSD and decided to install Ubuntu dual boot through a USB flash drive. Unfortunately, I encountered a lot of bugs in Ubuntu (freezing on purple screen, touchpad not working, no wifi detection, etc.) and decided to uninstall it and just stick with Windows 10. Being the idiot that I am, I deleted the Ubuntu boot in the BIOS before recovering the partition. Now it says that I only have 134 GB of space, and I don't know what to do. I'm pretty sure I still have the Ubuntu boot on my flash drive since I deleted the boot when the flash drive wasn't plugged in. What do I do? Is it even possible to get that 122 GB back?

Thanks.

---

### Post by yancek on 2015-12-22
> Now it says that I only have 134 GB of space

What exactly is the "it" you refer to above?  If you used some software to create the bootable flash drive, nothing changed on the flash drive as it is a read-only filesystem.  Did you format the Ubuntu partition?  There are a number of questions that would need to be answered and the simplest way to get the info needed is to boot the Ubuntu flash drive, go to the boot repair site at the link below and install it and run it selecting the option to "Create BootInfo Summary" and post a link to it here.  Do not try to do any repairs. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sammiev on 2015-12-22
To add to the above,

I would also try the USB live to see how compatible the OS and its features are before thinking of any install.

---

