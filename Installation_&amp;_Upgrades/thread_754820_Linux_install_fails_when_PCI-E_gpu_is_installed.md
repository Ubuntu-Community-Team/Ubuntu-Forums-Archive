---
title: "Linux install fails when PCI-E gpu is installed"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by Kr!ztov on 2008-04-14
This is more of a general Linux problem, because it is happening across the board. I'm having trouble installing any Linux distro onto a hard-drive, most of the time the files wont be extracted properly, for example Ubuntu 7.10 continues to throw up [Errno 5] Input/Output error whenever I try to install, the livecd loads up fine and works great, but it wont install onto the pc. I also tried VectorLinux, with the same result. These problems stop however, when I remove the Sparkle 8600gt that I have in the PCI-E slot. However, as soon as I insert the card again, the whole thing fails once more. I have checked for bad burns and bad cd downloads, and have tried several distros with no luck. With the older live cds, there is always an Xserver problem, but I can fix that usually by switching it to the VESA drivers. At one point, I thought it was the Power Supply, because some case fans were also deactivating randomly, but upon upgrading to a 750 Watt PSU, the problems persist. I have also tried replacing the cable to the cd drive, but that too helps none. My current guess is that the 8600 is sucking too much power from the board, because it does not take a direct from PSU input. Any ideas? My PC stats are:

Intel Pentium D Dual-Core CPU 3.2 Ghz X86
1 150 Gb Western Digital HDD IDE
1 500 Gb Western Digital HDD SATA
LG DVD drive
2 GB RAM (Dual Channel)
Sparkle SF-PX86GT256D3 (gpu)
Gigatech 945GZM-S2 motherboard

---

### Post by warp99 on 2008-04-14
Did you try any boot options during the installation process:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I would add the acpi=off and irqpoll kernel line options to see if this helps. Once Ubuntu is installed you may need to add one or more of these to your kernel line, but wait and see.

---

### Post by Kr!ztov on 2008-04-14
I hadnt tried any boot options yet, I will have to try them. Thanks.\

Edit: Ok, tried the ones you suggested, they returned the same result unfortunately.

---

### Post by warp99 on 2008-04-14
Well where in the install process are you getting these error messages and what are they? The reason is if you can boot to the LiveCd then everything is loaded and running on your machine, so it's not the GPU. It may be a configuration setting that needs to be easily changed, but I need some more information to help you.

---

### Post by Kr!ztov on 2008-04-14
Well, I can go through the regular setup steps, Keyboard Layout, Partitioning and so forth, the problem strikes when it gets to copying the files to the partition in question. Namely around the 25% to 40% region.

The error msg for 7.10 is always [errno 5] Input/output, and if it helps, I have been able to install and work linux while this gpu has been removed before.

Also, what I didnt notice before, a /target icon appears on the desktop after the install failure

---

### Post by warp99 on 2008-04-14
Did you try the alternative install CD? If you go to ubuntu.com you can download the CD by ticking the box "Check here is you need the alternate desktop CD." 

If you still can't get that to install then you can install the OS first, change the graphics drivers, install the card then boot to the desktop with the new graphics drivers, but first try the alternative CD.

Edit:
The alternative CD doesn't have a GUI, but is menu driven.

---

### Post by mwilliamsr on 2008-04-14
Try using "F6" in the startup menu and remove -quit -splash from the boot line.  This will stop the splash screen from hanging during boot up.  once the system is installed, modify you menu.1st file the same by removing the -quit -splash from the menu entries...l

---

