---
title: "LiveCD won't boot"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by thethimble on 2008-01-07
Hi-

I've been trying to install Ubuntu since Edgy.
After selecting "Install Ubuntu" from the initial menu, it loads the kernel, drivers, etc.

Then it hangs, with a flashing cursor at the top left....

I've been trying x64/x86 and server/desktop/alternate versions to no avail.

Motherboard: [Intel DG33FB]("http://www.intel.com/products/motherboard/DG33FB/index.htm")
Processor: Intel C2D E6600
Video Card: NVIDIA GeForce 7900 GT/GTO
RAM: 2gb ddr2 800
HD: [Samsung HD501LJ (SATA)]("http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=harddiskdrives&subtype=spinpointtseries&model_cd=HD501LJ")
DVD: HP DVD Writer 640c ATA Device


Thanks in advance

---

### Post by Sef on 2008-01-08
1) Have you md5summed the download?

2) Did you burn the iso as an iso?

3) Did you burn the iso at 4x or less?

4) Did you Check disk for errors? (go down the list instead of start/install click)

---

### Post by edw1nc on 2008-01-08
Same problem with me..My CDs were ordered from Ubuntu website and delivered to the post office..  i cant install it.. after splash screen appeared and the the cursor on the top left portion of the screen..the screen went black and nothing more

---

### Post by 64bits on 2008-01-12
I have the DG33FB motherboard working under Hardy Heron (alpha 2), but with the 2.6.22-14-rt kernel.

I previously had gutsy running, but could not get the correct resolution for my monitor (1280x1024).

First, it seems to be necessary to add this to the kernel options (in /boot/grub/menu.lst):
    pci=nommconf 

Then, if you have more than 4 GB of memory, you need to add something like this (in this case, I have 8 GB):
    mem=8832M

This worked for both Ubuntu and OpenSUSE-10.3. In OpenSUSE, I could also get the correct resolution by adding this kernel option (for 1280x1024):

    vga=0x31a

However, this did not seem to have any effect in Ubuntu. 

The new development version (Hardy Heron) has updated Xorg video drivers, which work with this board. I'm using the 2.6.22-14-rt kernel (Ubuntu Studio) and everything is working fine. I tried booting the newer 2.6.24-4-rt kernel, but the system hangs shortly after the desktop is displayed. VDR/DVB-S works with the 2.6.22 kernel, but not with 2.6.24 (can't load DVB firmware message in log).  (Where would be the best place to post a question about this?)

---

### Post by PmDematagoda on 2008-01-12
Your system hangs in the new kernel because your VGA drivers have to be recompiled. Reinstall or recompile your VGA drivers and you should be good to go:).

---

