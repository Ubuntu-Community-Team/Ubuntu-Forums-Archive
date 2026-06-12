---
title: "Please tell me its not trashed"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by rosenrosen on 2008-05-27
I have a system running XP and I was trying to install 8.04 to an external USB drive.  I had some issues and decided to do a reinstall using the Live CD.  I installed to the USB with no problem and it asked me to reboot.  When I did all I get is:

Boot from CD :
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

There is no CD in the drive.  If I disconnect the external drive I installed to I get the same as above but with Error 21.    In my previous install I ran into trouble when it asked me where to install GRUB but this time it never asked.  I think I was using the Alternate CD the first time.

Please tell me I can get XP and all my data back.  For extra credit I'd love to get Ubuntu working on the external drive as well.  My plan was not to install GRUB on the MBR but rather manually interrupt the normal boot process when I wanted to boot off my external.  Thanks.

---

### Post by Pumalite on 2008-05-27
Use Super Grub to fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by rosenrosen on 2008-05-28
Initially the WIN => MBR option and removing GRUB via Super Grub Disk worked but caused my system to boot directly into the Dell recovery partition every time.  I eventually figured out how to edit the WIN => MBR command to get my system to boot into the second partition on the primary disk which is where XP is.  Using info from this thread:
[http://ubuntuforums.org/showthread.php?t=808994](http://ubuntuforums.org/showthread.php?t=808994)
I was also able to get Ubuntu to boot from an external disk by maually interupting the boot process.  Hooray!

---

