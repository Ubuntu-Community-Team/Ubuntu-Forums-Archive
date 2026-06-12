---
title: "Installing XP from USB flash drive - dualboot"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by toolm on 2012-03-26
I am using edubuntu v 7.04 on a laptop without a HD. It has USB (obviously) and I have a USB flash drive with windows XP sp3 on it. I want to use both OSs. How do I do that? Do I just boot from USB and install XP, or do I need to free some space or make an empty partition before doing it. If so, how?

---

### Post by zvacet on 2012-03-27
First,I don´t know why are you using unsupported Edubuntu version.Maybe you can start from there.If you have some important files put in somewhere else ( external HD for example).After that install Windows ( that will erase your Edubuntu) but leave space for your new Edubuntu installation.That is one solution.Second is to shrink existing partition with Gparted ( you have it on Edubuntu but if not you can find it at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) ) After resizing partition install Windows on empty space.

---

### Post by toolm on 2012-03-28
I have it, but all options are unavailable for clicking. I tried logging in with root but still can't do any actions. 

What's the problem?

---

### Post by zvacet on 2012-03-29
Partition you want to resize have to be unmounted.You can achive that if you have edubuntu on usb or CD and run it in live mode.

---

### Post by toolm on 2012-03-29
What's the best way to do that? With unetbootin or what?

BTW, I need to mount that edubuntu on a USB FD and does it has to be the same version as the one that I'm using?


And can I do all of that on my XP and then just run edubuntu in live mode from the usb stick?

---

### Post by zvacet on 2012-03-30
For using gparted you can have other edubuntu verision on usb.Important thing is to boot from ubs and run gparted program to resize partitions.If you are running form usb  (or CD if it is possible) you are running live session and all partitions are unmounted and you can resize them.

---

