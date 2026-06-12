---
title: "install blocking problem - SATA disks not recognized"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by trollou on 2010-09-02
Hi,

I try to install ubuntu 10.04.1 on my pc but i fails at the very beginning because of HDD problem.

I get messages such as :
```
ataX.00: status {DRDY ERR }
ataX.00: error { UNC }
...
ataX.00: failed command: READ FPDMA QUEUED
ataX.00:
...
```
and after a while:
```
udevadm settle - timeout of 180 seconds reached, the event queue contains:
  /sys/devices/pci000............/block/sda
  /sys/devices/pci000............/block/sda1
  /sys/devices/pci000............/block/sdb
  /sys/devices/pci000............/block/sdb1
  /sys/devices/pci000............/block/sdb2
  /sys/devices/pci000............/block/sdc
  /sys/devices/pci000............/block/sr0
...
Kernel panic - not syncing: Attempted to kill init!

```

While these wierd messages appear, my hard drives do strange sounds.
(I am able to install windows XP without any problem)

What I have tried without success :
[LIST]
[*]I have unplugged each drives consecutively to see if it was an hardware problem
[*]bios updated to latest release
[*]changing in the bios my SATA config from IDE to AHCI mode
[*]setting the boot option pci=nomsi while in AHCI mode
[*]trying with another distro (debian 5.05)
[/LIST]

A friend lend me a SSD (a G.Skill 64Go) to test and big surprise... It was able to continue the install process with this drive only. I don't understand why my 3 samsung HDD are handled differently ! Any idea that can help me ? Its frustrating to be stuck with Windows at home while i am using linux at work every days :|

Hardware:
[LIST]
[*]motherboard: Asus P5E (northbridge: Intel X38, southbridge: ICH9R)
[*]3 hard drives : 3 x Samsung Spinpoint T166 400G
[/LIST]

Mathieu
(Sorry for the possibles english mistakes, not my mother tongue:)

---

### Post by trollou on 2010-09-06
up

Any idea please?

---

### Post by kelimi on 2010-09-18
I have a similar problem, and posted it as a new thread since it also happens with an existing Ubuntu system (not just with the installer):
[http://wwww.ubuntuforums.org/showthread.php?p=9859838](http://wwww.ubuntuforums.org/showthread.php?p=9859838)

---

### Post by trollou on 2010-09-20
Hi Kemili,

I solved my problem by doing a low level format with the Samsung utility: my 3 hard drives have been used in a hard fakeraid and some traces on the disks were causing the problem (a simple format was not sufficient).

---

