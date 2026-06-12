---
title: "Vista + Ubuntu 7.04"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by wconstantine on 2007-04-17
I don't think it can be because I have Windows Vista installed on my computer, but. When I try to install Feisty Fawn the installation never starts, instead I get into some kind of shell. Init something where I can write commands. I'm not an experienced linux user because I've never been able to install linux. 

That's because of my motherboard. MSI P965 Neo. The jmicron chipset is now supported in the new kernel I think. Anyways. Someone know what the problem is? I've tried boot in safegraphics mode and the usual one.

My comp:

MSI P965 Neo
E6600
1 SATA HDD 80gb
1 IDE HDD 80gb
Corsair Value Select 667 MHz 2gb

If required I can try again and write up exactly what kind of mode I get into and exactly what it says for further investigation.

---

### Post by zvacet on 2007-04-17
Posting that will make easyer to solve your problem.So,do it and somebody will help you.

---

### Post by fickleflame on 2007-04-17
Are you trying to install 7.04 over your Vista? or do you have a separate partition already created?

In my experience I found that clearing off the system drive, then installing Ubuntu to a 10g partition and then installing Vista works best. After that modify the GRUB and Vista loaders to for dual boot.

If you are attempting a clean install try booting into a live CD and open a command prompt. Mount the system disk then type ```
dd if=/dev/zero of=/dev/hda bs=1M count=1000
``` Then reboot and attempt the 7.04 install again. Only use this command for a clean install because it overwrites your hard disk with zero's.

Let us know how it's working out.

---

### Post by wconstantine on 2007-04-18
It says BusyBox v1.1.3

/bin/sh can't access tty; job control turned off'

I have no kind of wish to reinstall Vista again :P

I got Vista on the sata harddrive and want to use the IDE one for my Ubuntu installation.

---

### Post by kellemes on 2007-04-19
> **wconstantine said:**
> It says BusyBox v1.1.3

/bin/sh can't access tty; job control turned off'

I have no kind of wish to reinstall Vista again :P

I got Vista on the sata harddrive and want to use the IDE one for my Ubuntu installation.


I think this could be a bug really..
I think you should download and burn the official 7.04 as released today and try again.. By the way, the board is probably not the issue because I have the same board without this problem.

---

### Post by cogadh on 2007-04-19
This is still happening in the newest release:

[http://ubuntuforums.org/showthread.php?t=413675](http://ubuntuforums.org/showthread.php?t=413675)

If it is a bug, they never fixed it from the beta.

---

### Post by wconstantine on 2007-04-19
If it was a bug it was fixed. I downloaded the final version of feisty today and it works fine now. Atlast a Linux that works for me! :popcorn:

---

### Post by cogadh on 2007-04-19
Congrats! Enjoy your first cup of Ubuntu.

---

### Post by Lucifiel on 2007-04-19
> **wconstantine said:**
> If it was a bug it was fixed. I downloaded the final version of feisty today and it works fine now. Atlast a Linux that works for me! :popcorn:

Yay!!! Have fun!!! :D

---

### Post by wconstantine on 2007-04-19
Thanks! It's lovely. The drivers wasen't a problem at all, just needed to activate them. 

I tried to figure out how to do dual monitor for about 30minutes until I discovered all I had to do was to write sudo infront of aticonfig -dtop=horizontal. :P

---

