---
title: "ALERT! /dev/disk/by-uuid/... does not exist. running on vmware"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Bimme on 2010-11-12
I tried to upgrade my ubuntu 10.04 to 10.10 on my virtual machine using vmware workstation 5.5.
After the upgrade grub can't find my hard drives with the message:
ALERT! /dev/disk/by-uuid/... does not exist.

After this I downloaded the live dvd to check the uuid of my disc, but sudo fdisk -l does not list any devices at all.
Also tried sudo blkid with the same result.

The virtual machine has 2 virtual discs connected, and everything was working before the upgrade.

---

### Post by Bimme on 2010-11-16
Is there anyone that have any suggestions on how to investigate this problem?

---

### Post by drs305 on 2010-11-16
I can't speak to VMware, but if you get the Grub menu you can press "e" to get to the grub terminal.

Type "ls" to list the drives, partitions which G2 sees. If you find your OS partition - for instance, (hd0,1) - then explore the contents: "ls (hd0,1)/"

If it sees the files, press ESC to return to the Grub menu, then "e" to edit the menuentry. Remove the entire "search" line and in the "linux" line change the "root=UUID=<someuuid>" to "root=/dev/sdXY" (probably root=/dev/sda1).

This may allow you to boot, after which you need to run 'update-grub'.

---

### Post by Bimme on 2010-11-16
I press "c" to get the command line, but the "ls" command is not recognized as a command. Could it be an old version of grub that is installed? (I have been running older versions of Ubuntu and do not remember if I have upgraded grub, although I think that I have done so).

---

### Post by drs305 on 2010-11-16
> **Bimme said:**
> I press "c" to get the command line, but the "ls" command is not recognized as a command. Could it be an old version of grub that is installed? (I have been running older versions of Ubuntu and do not remember if I have upgraded grub, although I think that I have done so).

Yes, that is possible. You can check the version by looking at the top of the grub menu. 0.97 is Grub legacy, Grub 1.96 or later is Grub2.

---

### Post by Won1der on 2010-12-22
Thanks, this solved it for me.

---

