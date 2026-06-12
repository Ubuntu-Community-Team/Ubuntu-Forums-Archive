---
title: "no boot menu after installing grub"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by pk12 on 2014-10-06
So, the story is that I installed windows 7 after ubuntu 14.04, and after succesfully doing a boot-repair, the grub2 menu was indeed present at the beginning but without an option for ubuntu ( only for windows). 
I tried some other things found on this forum, and now the grub2 in the beginning doesnt show me a boot menu only a "minimal bash-like line editing".
So, now I have 2 problems, one that I should fix the grub2 the way it was, and then show the ubuntu option. 

This is what fdisk-l shows: 

Device Boot      Start         End      Blocks   Id  System
 /dev/sda1            2048    58593279    29295616   83  Linux
 /dev/sda2        58595326   223633407    82519041    5  Extended
 /dev/sda3   *   223633408   223838207      102400    7  HPFS/NTFS/exFAT
 /dev/sda4       223838208   976771071   376466432    7  HPFS/NTFS/exFAT
 /dev/sda5        58595328    59570175      487424   83  Linux
 /dev/sda6        59572224   215820287    78124032   83  Linux
 /dev/sda7       215822336   223633407     3905536   82  Linux swap / SolarisAnd this my gparted:
[[IMG]http://i.imgur.com/yHAMGlU.png[/IMG]]("http://i.imgur.com/yHAMGlU.png")

---

### Post by yancek on 2014-10-06
If you used the boot repair it would be useful if you could post the output of the script.  See the link below.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by pk12 on 2014-10-06
This is the boot info:

[http://paste.ubuntu.com/8507435/](http://paste.ubuntu.com/8507435/)

and thank you for your help!

---

### Post by pk12 on 2014-10-06
Solved it.. Thanx!

---

