---
title: "Dual Boot and Two SATA Drives"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by Thomeduk on 2007-10-07
I have been struggling to configure 'Grub' to dual boot with my machine that has only SATA drives.  I installed Ubuntu on one drive (hd0) and the other drive is dedicated to WINXP (hd1).  I added:to menu.lst

title   WINXP Pro
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

but Grub would return Error 11 when trying to boot to WINXP

The solution was in the device map.  The device map (cat /boot/grub/device.map)  only showed 
(hd0) /dev/sda

I added (hd1) /dev/sdb (the WINXP drive) and (hd2) /dev/sdc (third HDD) rebooted and tried to start WINXP that now gave 'GRUB BOOT DRIVE ERROR' (or words to that effect).  I returned to menu.lst and under WINXP changed root to (hd1,1) [(hd1,0) was extended partition whereas (hd1,1) was the Primary partition, don't know why!].  My machine now dual boots.

I don't know whether it is a 'bug' in GRUB that does not seem to map all SATA drives, or something specific to my installation.  I have asked many times for advice on this matter but no one yet has suggested 'drive mapping' may be the problem so perhaps it is something discrete to my installation.

---

