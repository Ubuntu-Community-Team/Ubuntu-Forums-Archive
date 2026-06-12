---
title: "I have an unusual problem with multibooting"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by glenngds on 2010-04-07
I have two hard drives windows 7 is on one of them and Ubuntu 9.10 is on the other. Both drives are 320GB, but different models of drives by Seagate. Both drives are detected by the BIOS and both drives are detected by Windows, but only one drive is detected by Ubuntu during the installation process. I had to literally disconnect the Windows drive to get Ubuntu to recognize the drive I wanted it on. Now that Ubuntu is completely installed and a new Kernel has been downloaded and installed it finally recognizes both drives as existing. There is some kind of problem with the Installer and the original Kernel that kept it from seeing the second drive. I will literally have to manually edit Grub to get it to boot the Windows drive. How do I edit Grub????? and what kind of Grub command would do the trick?????

I searched for "multi-boot" and literally read them all, there was one thread about multi-boot on multi-drives, but it did not fit because the Installer recognized both drives with that thread.:confused:

I have to change the boot order in the BIOS to get the drive to boot that I want currently.

---

### Post by kr651129 on 2010-04-07
How did you install these two OS's?  My idea would be format your two drives from the windows installer, reinstall using all the space over both for windows, then reinstall ubuntu and use the partition program durring the install to set the hdd's to each os then it should boot up just fine

---

### Post by oldfred on 2010-04-07
If you set your BIOS to boot the Ubuntu drive and have a new install of Ubuntu you have grub2 which should find windows without any problems if the windows boot works. From a terminal run this:

```
sudo update-grub
```

---

### Post by glenngds on 2010-04-07
I got the following error.

 sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

---

### Post by glenngds on 2010-04-07
Found the solution to my problem. It was not a software problem after all at least not Ubuntu or Windows, but was most likely a problem that is part of my system BIOS. The way I had the two drives installed in my computer was that both were on different SATA channels and both were on the Master plug of that channel. When I moved one of them to a slave plug -- bingo, everything was fine. Something is screwy with either the BIOS on the MOBO or the SATA controller on the MOBO.:lolflag:

---

