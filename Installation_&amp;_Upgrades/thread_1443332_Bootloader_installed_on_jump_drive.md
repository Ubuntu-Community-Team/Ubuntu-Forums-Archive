---
title: "Bootloader installed on jump drive"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by a_z1_9scores on 2010-03-30
Okay, so I just finished installing lucid lynx netbook to my jump drive (full install) to save room on my hard drive. It's working fine except the bootloader was installed to the jump drive as well, meaning I can't boot my computer without the jump drive. Is there any way to correct it so that the computer boot from the hard drive while keeping my install on the jump drive?

---

### Post by a_z1_9scores on 2010-03-31
bump

---

### Post by oldfred on 2010-04-01
ARe you sure its not installed to the  hard drive. If you remove the jump drive your hard drive should boot. You probably just need to reinstall grub to the MBR of the internal and the newest grub from lucid to the jump drive. Install may depend on what version you have on your internal drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If unsure of configuration run this script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

for grub2
reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

---

