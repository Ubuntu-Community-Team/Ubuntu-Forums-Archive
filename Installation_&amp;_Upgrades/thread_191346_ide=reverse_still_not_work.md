---
title: "ide=reverse still not work"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by wfx on 2006-06-07
Thx and gratulation to "Dapper Drake"!!!
It is a real real good distribution.
but...
for a long long time ago i wrot a bug report about the problem that the install
system does not accept the bootoption "ide=reverse".
Some time later i get the answer it is fixed in dapper drake.
Hmm, but i must see it is not.

Anyway i was not in mood to remove the second ide controler.
So install dapper on hde1...n (in real it is hda1..n) why not i dont have any prob
 with the wrong device name only dapper have some prob. 
It thinks that the rootdevice  is "root (hd3,1)"  in menu.lst (tz tz hde ;-))
so the bootup fails -> file not found.

So i have to change root (hd3,1) to  groot=(hd0,0).
Ubuntu developer do what you like, fix it or let it as it is.

PS:
~$  cat /boot/config-2.6.15-23-386 | grep "BLK_DEV_OFFBOARD"
# CONFIG_BLK_DEV_OFFBOARD is not set

---

