---
title: "grubb error 22"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by Rody on 2007-07-11
Hi guys and gals.

I just upgraded my computer to nearly bleeding edge setup and am relizing that i may have stabed myself in the foot.

system specs
Abit IP35 PRO
Intel e6600
2 gb crucil tracers
GeForce 8800 GTX

on the Jmicron ide controler
lighton dvd rw
samsug DVD

on the Intel SATA controller
2 36gb raptors in raid 0
1 320gb segate 


I tried to Install Gutsy Gibbon tribe 2 hoping that it would reconize all my new hardware but the live cd would not even boot up all the way, (dumb Jmicron controler) even when i used irqpoll it only booted up some of the time.

So i decided to use 7.04 feisty instead, shockingly it loaded up the live cd just fine but now i had to repartition my hard drives, I ended up seting my 320gb drive as two 78gb partitions, 1gb swap partition and the rest 140gb or so as root, ievery thing went fine till i rebooted and got error 22 on grub ( which after searching the net i can not seem to find any information about it).

I rebooted the live cd again and tried to modify grub but It would not let me have access. I have used linux for several years but i have had to mess with lilo or grub, they just worked. I ended up using windows vista recovery concol to fix my boot sector so i could get back to vista, but i really only use vista for gaming I do all my work in linux.

I would appreciat any help you all can offer
thanks,
rody

---

### Post by Pumalite on 2007-07-11
You will have to do a little reading:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://ubuntuforums.org/showthread.php?t=114519](http://ubuntuforums.org/showthread.php?t=114519)

Myself; I disabled the Raid 0 and worked with 3 independent SATAII drives. Had no problems after that.

---

### Post by fjf on 2007-07-30
Rody, did you get the ip35 pro working in ubuntu?.  I was thinking of purchasing this same board.

---

### Post by MQMike on 2007-07-30
The jmicron controller (added to this mix of IDE and PATA) maybe the issue here, could be the show-stopper.


[http://ubuntuforums.org/showthread.php?t=511772](http://ubuntuforums.org/showthread.php?t=511772)

---

