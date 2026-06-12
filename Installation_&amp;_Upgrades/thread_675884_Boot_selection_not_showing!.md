---
title: "Boot selection not showing!"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by milentie on 2008-01-23
I have just installed Ubuntu 7.04 for 64bit-PC, but I cant access it (I have AMD 64bit processor). I cant see boot menu on any kind of menu at all. it just loads up my windows as usual. How can i load/install/solve the boot selection problem? I want to have boot selection between Xp and Ubuntu and start each when i need? 
I have Sata and Ide drives on my mb, but both ubuntu and xp are installed on the SATA hd.

---

### Post by bwtranch on 2008-01-23
I have Sata and Ide drives on my mb, but both ubuntu and xp are installed on the SATA hd.

I think that might be your problem.

---

### Post by milentie on 2008-01-23
u just removed the ide hd but still no results.

---

### Post by bwtranch on 2008-01-23
But, both OS's are on the SATA. Windows looks at the first boot part and then doesn't see anything else. You have to put Linux on the IDE and partition your drives, either yourself or with a utility..

---

### Post by bwtranch on 2008-01-23
Okay, I went and did some brushing up on SATA. I knew it wasn't something that I cared about, so I forgot it. What it is, is supposedly gives you up to a 3Gig transfer speed. HA. That's really funny and if you believe that, I've got some great homes for sale that people couldn't make the payments on. 

But, seriously folks, Linux does support the protocol for this so-called blinding speed. How it's implemented, I don't have a clue. Nor, like I say, do I care. Because you are never going to get that kind of transfer rate. There are too many things involved that will slow things down and there's not room on the forum to list them all.

Best thing to do, with the smallest effort, is hook up your regular IDE HDD in the regular way. Back up your system and install Linux with GRUB bootloader. If you want to spend upwards of $5000 on a smomkin' system that SATA might give you a speed benefit, but, unless you are into high end graphics production---you'll never see the diff anyway.

---

