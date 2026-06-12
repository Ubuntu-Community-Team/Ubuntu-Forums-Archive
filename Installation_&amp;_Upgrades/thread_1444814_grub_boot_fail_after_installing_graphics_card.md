---
title: "grub boot fail after installing graphics card"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by vkunkel on 2010-04-01
**Background:**
I installed a new graphics card (Nvidia GeForce GT240 1 Gb, 128bit DDR3) on my gigabyte VA900M motherboard, with my computer running a dual boot of windows 7 (64 bit) and ubuntu 9.10 (64 bit). The computer would not boot past the memory test stage. To solve this, i flashed the BIOS with the latest upgrade for the motherboard from the Gigabyte website. This still did not work, so, doing the usual "testing hardware combinations by unplugging and replugging", I removed 1 Gb of RAM, which solved the problem of booting past memory test (a case of too much memory?) 

**Problem:**
The problem now is, GRUB wont boot from the HD, unless I have the Windows 7 disk (or Ubuntu Live) in the DVD drive. If i dont press a key to boot from the disk, Grub will then load.
Any suggestions on how to make GRUB boot from the HD? Do I need to redirect/reinstall GRUB?  Im pretty sure it is not a BIOS problem.

---

### Post by oldfred on 2010-04-01
Just to see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


How much memory did you have? I have not heard of too much.

---

### Post by vkunkel on 2010-04-01
I have just now followed a suggestion from the gigabyte website, to restore the failsafe defaults in the BIOS setup. I had noticed the defaults changed my modification, of the VGA only seeing the PCI graphics card slot, to seeing both onboard and graphics card, but using the more "important" VGA input.

Im not sure if this was the reason, but my computer is now able to boot into grub!:D

Thanks anyway, oldfred, for your prompt reply. (PS I had one slot of 2Gb, and 1 slot of 1GB, I had removed the 1 GB stick. I plan to upgrad it anyway to have 2x2 Gb.)

---

