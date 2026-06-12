---
title: "UNMOUNTABLE_BOOT_VOLUME after Ubuntu installation on a T61p (XP/Ubuntu dual boot)"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by flexible1 on 2008-05-17
Hi,

I'm trying to set up a dual boot system (Windows XP/Ubuntu 8.04) on a new T61p but am experiencing some difficulties doing so.

The Windows XP installation works just fine right after a fresh install, but unfortunately stops working after the Ubuntu installation.

I started with the XP installation and continued with Ubuntu. Rebooting the system then (when the Ubuntu installation is done) provides me with a proper list of boot-options to choose from. Booting into Ubuntu works, however a couple of seconds into the XP startup screen I get an UNMOUNTABLE_BOOT_VOLUME bluescreen.


Partitions on the system are:
1. WinXP (NTFS, primary)
2. swap
3. /boot (ext3, primary)
4. Ubuntu / (ext3, primary)
5. Ubuntu /home (ext3, logical)

Several forum posts I stumbled upon suggested different solutions for the problem, so I tried fixmbr and fixboot in the Windows Recovery Console, ntfsfix, chkdsk /r, everything without success. fixboot couldn't even find the partition, checkdisk found 'at least one problem that cannot be resolved' and ntfsfix didn't have any effect at all.

Has anyone encountered similar problems? At this point I'm grateful for even the slightest hint that could point me towards a solution for the problem.

Thanks!



[

my menu.lst

[http://ubuntuusers.de/paste/216889/](http://ubuntuusers.de/paste/216889/)

my Boot.ini

[http://ubuntuusers.de/paste/216897/](http://ubuntuusers.de/paste/216897/)

]

---

### Post by teaker1s on 2008-05-17
yes sadly I have had issues with xp and vista with this.
Sometimes the ntfs file system corrupts.(even vista can´t repair itself)

The way I´ve cured it is to use knoppix live cd and use the correct fixntfs command after finding out the partition with windows on by issuing
f```
disk -l
```

---

### Post by flexible1 on 2008-05-18
already tried = doesn't work. 

"failed to determine whether sda is mounted: no such file or directory. Mounting volume... error opening partition device: no such file or directory. Failed to startup volume......"

---

### Post by teaker1s on 2008-05-18
stupid question but you did use sudo? and example below
```
sudo fixntfs /dev/sda
```

---

### Post by flexible1 on 2008-05-18
yes, i have used sudo. 
now i have found out the right code:

sudo ntfsfix dev/sda1

it worked! but still if booting windows = bluescreen

---

### Post by teaker1s on 2008-05-18
possibly using the xp cd you could try repair option?

---

### Post by flexible1 on 2008-05-18
already tried, but it didn't help

---

### Post by qlimax on 2009-02-04
same situation, same error.

I am now trying to reinstall window and then ubuntu....

tryed all, chkdsk /r in the recovery console, was the solution proposed by many,... but for me doesn't work:(

good luck:popcorn:

---

### Post by qlimax on 2009-02-04
ps : thinkpad t40

I have seen many have this error with thinkpad...

MAH....

now installing ubuntu

---

### Post by qlimax on 2009-02-04
two hours lost...

again the same error, after fresh install...


now i'm suspecting that is the install procedure


next try:

install window on the whole hard drive

install ubuntu resizing windows partition


suspects:
ibm laptops seems to have an hidden partition (5 gb)

---

### Post by qlimax on 2009-02-06
:popcorn::popcorn::p


solved,

I had to disable the hidden partition (for recovery purpose of IBM), in the bios under the security menu.

then normal xp+ubuntu dual boot installation works.


CYA

---

### Post by enigmatichus on 2010-10-18
Thank you very much, qlimax, I just had this problem installing ubuntu on a friend of mine's thinkpad T40!!

---

