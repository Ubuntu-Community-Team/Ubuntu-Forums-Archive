---
title: "Dual boot Ubuntu and OpenSolaris?"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Gogeden on 2010-08-20
I installed Ubuntu 10.04 first and OpenSolaris 2009.06 second. Ubuntu does not appear in OpenSolaris' boot-loader. How do I install Grub and have the boot list come up so that Ubuntu AND OpenSolaris appear and are operational and such?


Thank you :) :lolflag:

---

### Post by oldfred on 2010-08-20
Have you  tried reinstall grub2 for Ubuntu and see if the osprober finds it.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda


I saved this but it assumes you have installed OpenSolaris boot loader into its boot sector, PBR or boot slice (like windows).
[http://ubuntuforums.org/showthread.php?t=1529658](http://ubuntuforums.org/showthread.php?t=1529658)
menuentry "OpenSolaris 2010.03 snv_134 64bit" {
    set root='(hd1,2)'
    chainloader +1

---

### Post by Gogeden on 2010-08-20
That actually really confuses me. Can you "Dumb it down" a little bit? :P Thanks ^_^

---

### Post by oldfred on 2010-08-20
Several links on reinstalling grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by Thomas Garman on 2010-08-20
If you installed Ubuntu and the Open Solaris and then you couldn't see Ubuntu anymore then you probably never had a chance to put any crucial data on the Ubuntu partition so the absolutely easiest way to fix it all so that grub reappears and Opensolaris and Ubuntu work is:

just reinstall Ubuntu again on the Ubuntu partition

this is easiest way to get it all back (it is a 700 MB way of reinstalling GRUB2 without having to do any of the work of figuring out how to reinstall grub2).

---

