---
title: "Grub problems after installation"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by I3roknI3ottle on 2007-07-28
alright i partition'd my hardrive into 3 partitions, one 11GB for ubuntu, 1GB for swap, & the rest of a 80GB for windows xp.  I already had windows xp installed, and I installed Ubuntu on the 11GB partition.  When my computer starts up tho it goes straight to windows w/o any evidence of grub..  I dl'd the iso from the website the 7.04 32bit one.

---

### Post by Pumalite on 2007-07-28
Use Super Grb: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Re-install Grub to MBR (hd0,0)

---

### Post by MQMike on 2007-07-28
You may need to re-install GRUB, as suggested above.

First, you need to get a grub prompt (grub>) somehow.  Your two choices are: (1) Use a rescue disk, like Super Grub Disk, from which you can boot into your OS, or press the “c” key to get a GRUB prompt.  Or, (2) Use your Live Kubuntu CD.  Let's assume (2) here.  

Put your Live CD in the CD tray, re-boot your PC, startup your Live Kubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hdx,y)          # (hdx,y) is the partition of your "main" Linux OS--SEE NOTE BELOW
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

NOTE:  From what you said, Windows was there first, probably on (hd0, 0) – the first hard drive hd0, the first partition (partition 0).  (Note that the bootloader GRUB starts numbering drives and partitions from zero).
And then Ubuntu is on the second partition?
If so, 
root (hdx, y) 
would then be
root (hd0, 1).

---

