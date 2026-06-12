---
title: "creating a duel boot system HELP"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by storky on 2007-04-15
so i have ubuntu installed on my laptop and i love it. But i do need a small windows portion (for certain windows applications and school) and i have no idea how to do this. There is nothing overly important on my system so i am OK with wiping everything if i need to. I want like a 10 gig or so windows xp partion and the remaining 120 gig to ubuntu (just hypothetically) I have a ubuntu live disk and a Xp home disc ready to go but would prefer adding a windows partion to my system rather then installing windows to the whole system and then partioning ubuntu back in. thank you in advance if u can help me with this (keep in mind i am a linux newb)

---

### Post by rsambuca on 2007-04-15
If you don't mind reinstalling, it is pretty easy.  I would use gParted on the ubuntu liveCD to partition the drive prior to loading any OS's.  Put your 10Gig ntfs drive as the first partition, and then your ubuntu partition(s) - I use the default ext3.

Install XP first, and then install ubuntu as grub should detect XP and give you a choice of OS at boot-up.

---

### Post by storky on 2007-04-15
are there any good tuturiols on this.....i dont know much about partioning and such....

---

### Post by rsambuca on 2007-04-15
> **storky said:**
> are there any good tuturiols on this.....i dont know much about partioning and such....

Here is a good place to start.  [[COLOR="Red"]Link[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning")

---

