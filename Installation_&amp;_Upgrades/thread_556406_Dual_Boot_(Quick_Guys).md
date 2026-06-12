---
title: "Dual Boot (Quick Guys)"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by paneas13 on 2007-09-21
Hello there,

I am going to install Ubuntu Feisty Fawn to my friend. He has 2 hard disks ( SATA both). In the first SATA he has install Windows XP, and I am going to install Feisty Fawn in the second SATA. He wants dual boot.

As far as I am concerned, I grub disables every operation system that is installed in different disk. Right ?

So, how should I install Feisty with dual boot ?

PS: I have 30 minutes to go... answer quickly (if you can).

Thanx!

---

### Post by MrHippocampus on 2007-09-21
grub should pick up all other operating systems on all disks in the system. So you should just be able to install feisty as normal and it will work fine.

One word of warning though, make the feisty drive is secondary and keep the windows drive as the primary boot drive, if windows is on the secondary drive it wont boot with the default grub set up (you have to add a few commands in to get it to work, no big problem, but annoying if you don't know about it).

---

### Post by paneas13 on 2007-09-21
> **MrHippocampus said:**
> grub should pick up all other operating systems on all disks in the system. So you should just be able to install feisty as normal and it will work fine.

One word of warning though, make the feisty drive is secondary and keep the windows drive as the primary boot drive, if windows is on the secondary drive it wont boot with the default grub set up (you have to add a few commands in to get it to work, no big problem, but annoying if you don't know about it).

Do you mean to install Ubuntu Feisty Fawn in the SLAVE sata and Windows XP on MASTER sata ?

---

### Post by dptxp on 2007-09-21
I think that you set primary and secondary in bios (maybe in auto detect) and this is different
from master and slave. You can have two as master.
Check in your bios, I do not remember well.

---

### Post by paneas13 on 2007-09-21
There is a option about Boot Devices:
1st Boot Device: DVD
2st Boot Device: SATA1
3rd BOot Device: SATA2

SATA1 = Windows XP
SATA2 = Ubuntu Installation (forthcoming)...

Is this configuration, ok ????

---

### Post by MrHippocampus on 2007-09-21
yep that should be fine.

---

### Post by paneas13 on 2007-09-21
> **MrHippocampus said:**
> yep that should be fine.


My friend has ATI Radeon X*** series. Is it wise to install Dapper Drake or Feisty Fawn ?

---

### Post by MrHippocampus on 2007-09-21
in my opinion, when graphics cards are involved you should always install the latest version. So go for feisty

---

### Post by LaRoza on 2007-09-21
> **paneas13 said:**
> My friend has ATI Radeon X*** series. Is it wise to install Dapper Drake or Feisty Fawn ?

Try live CD.

---

### Post by paneas13 on 2007-09-21
Thank you all of you, I am on the way to go to my friend. Thanks!!!!!!!!!!!!!!!!!

---

