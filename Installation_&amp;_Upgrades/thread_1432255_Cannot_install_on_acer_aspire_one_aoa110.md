---
title: "Cannot install on acer aspire one aoa110"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by keth802 on 2010-03-17
i cannot install any ubuntu based system, or any system at all, on my acer aspire one aoa110. tried with a live usb, live cd, live dvd, all have the same result. i can boot the os, it works fine. when i actually hit install it goes to five percent and then hangs for 90 seconds and then says that it cannot format scsi1 to ext4. so i tried ext3. and reiserfs. and virtually every other format. none worked. i've been told it may be my ssd drivers, but i can't find any drivers for my ssdpamm0008g1 solid state.

---

### Post by conradin on 2010-03-17
I just checked newEgg, and they sell that model with Ubuntu pre-installed. Are you using the netbook remix?

---

### Post by blackmail on 2010-03-17
You could try [this]("http://www.ubuntu.com/GetUbuntu/download-netbook") link.
If the problem persists, just report back.:popcorn:

---

### Post by keth802 on 2010-03-17
i received it with xp home edition pre-loaded. right now trying to install linux mint

---

### Post by keth802 on 2010-03-17
UNR didn't work either. I have, so far, tried gentoo, openSuSE, UNR, Ubuntu, Xubuntu, Linux Mint, Puppy Linux, and Damn Small Linux. None of them would install to the SSD.

---

### Post by blackmail on 2010-03-20
Moblin shoul, oh and have you checked the links which appear in my previous post, that must be good for your netbook :D

---

### Post by sid1950 on 2010-08-02
You should download PartedMagic [from here]("http://partedmagic.com/"), and use it to check the drive. I always use PM to partition and format before installing. It is reliable and has some very good checks. You can also use TestDisk to test for bad sectors and faulty partitions.

I have an AOA110 16Gb SSD with 1Gb RAM. It came with LinspireLite, but I repartitioned and added first openSuse 11.1, then changed to Ubuntu Netbook Remix 9.10, and now Ubuntu NBR 10.04. Installations were no problem, and the NBR version of the Gnome desktop is very good for the small screen. Everything worked "out of the box" apart for the card reader slots which need a bit of fiddling.

---

