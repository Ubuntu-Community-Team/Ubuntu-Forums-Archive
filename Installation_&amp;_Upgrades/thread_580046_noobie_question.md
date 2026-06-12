---
title: "noobie question"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Foresthello on 2007-10-18
umm I was wondering when i update ubuntu, I have 32 bit processor I wonder if ubuntu 7.10 is 64 bit and if it is 32 and 64 and does it automaticly detect wether im 32 or 64.

sorry for not typing correctly im just in a hurry

---

### Post by Foresthello on 2007-10-18
Does anyone have any answers sorry I just dont want to screw up my computer

---

### Post by superyounan1 on 2007-10-18
you choose which version you need when yo udownload the iso. 

on the ubuntu site, choose "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)"

if you're downloading a torrent, choose x86 or i386 version

---

### Post by Foresthello on 2007-10-18
i mean upgrading from 7.04 it said there is a upgrade in update manager

---

### Post by ÜbuntuMensch on 2007-10-18
You can't go wrong updating from the official Ubuntu repositories. Go ahead and do the upgrade through update manager.

Both Feisty and Gutsy come in 32 bit and 64 bit. Update manager will update whichever you have already installed, which is probably the right one for you. It's easy, really. A 64 bit OS won't even install on a 32 bit machine. On the other hand, a 32 bit OS works on the current 64 bit hardware. SO you probably have 32 bit.

You can do in terminal

sudo uname -a 

to find 

If it says x86_64, you're running the 64 bit Ubuntu.

But go ahead and use the update manager to upgrade. It should be fine. In any event your problems won't be due to 32 bit vs. 64 bit.

---

