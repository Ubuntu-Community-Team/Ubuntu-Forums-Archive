---
title: "Installation lock before disk partitioning"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by stefanokan on 2013-04-04
Two days lost doing trials.
During a fresh installation starting from Ubuntu 12.04 (or Lubuntu 11.10) when the installer arrives to disk partitioning, it stops working and the waiting is endless.
It's the same with usb pen or CD-ROM.
i tried also with alternate cd but same result. Trying it in Live mode works flawless.
Starting installation from Ubuntu 11.10 (or Lubuntu 11.04) the installer works well and the installation is finished without problems. Then i've upgraded until last versions (12.10) without problems.
It is an HP Compaq nx6310 laptop with Celeron M 1,7 Ghz processor and 1 Gb ram, HD 80 Gb  divided in the following partitions:

Device  Boot Start End Blocks Id System
/dev/sda1 * 2048 35485695 17741824 7 HPFS/NTFS/exFAT
/dev/sda2 35487742 156301311 60406785 5 Extended
/dev/sda5 80543744 156301311 37878784 83 Linux
/dev/sda6 35487744 78444543 21478400 83 Linux
/dev/sda7 78446592 80541695 1047552 82 Linux swap / Solaris

So Windows is in sda1, Filesystem is in sda6, swap in sda7 and /home in sda5.
It appears a problem of the installer script, starting from Ubuntu 12.04 (or Lubuntu 11.10).
As it's very boring installing an old version and then upgrading 2-3 versions, is there a solution?
Thanks:)

---

### Post by gordintoronto on 2013-04-04
At one time, installation would stall if the computer name or user name had upper-case characters, perhaps only as the first character. Are you specifying the same computer and user names in instalations which work and the ones which don't?

By the way, you did a great job of including relevant information!

I'm puzzled how you positioned sda5 after sda6 on the hard drive. Do you tell the installer to format sda6, aka /

---

### Post by stefanokan on 2013-04-05
Hi gordintoronto,
yes, i specified the same user name in old and new installations, and yes i told the installer to format sda6.
About the partitions sda5 and sda6 positioning this strange position happened when i moved the partition in the past in order to create a NTFS partition (to insert Windows os, because at the beginning i had Ubuntu only). So Gparted made the job for me and it assigned the names. And also you can notice that sda3 and sda4 names are no more used.
Perharps the problem can dipend from this?
As i know it is possible to change partition label but not partition name. Do you confirm?
Thanks for your help.
S.

---

### Post by gordintoronto on 2013-04-06
I don't know what is causing the problem.

sda3 and sda4 are only used for primary or extended partitions. Since you only have one primary partition and an extended partition, sda3 and sda4 are not used.

---

