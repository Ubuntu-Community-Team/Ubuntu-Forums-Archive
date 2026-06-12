---
title: "Booting on an external HDD"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by nolongerlivecd on 2006-06-07
Has anyone managed to get this onto an external HDD without any problems?

I intend to use my external HDD 30GB for at the very least 25GB filestorage. Would 3-5GB do then for an install that can roam between different computers, with different processors and GFX cards?

---

### Post by glotz on 2006-06-07
Oh yes.

---

### Post by nolongerlivecd on 2006-06-07
I'm asking if there are any methods which enable me to use this disk to carry around, booting it with different computers?

---

### Post by nolongerlivecd on 2006-06-08
I'm asking this because in school, I would like to use Ubuntu, but they don't offer it as an option. There are several different configurations in my school for desktops, ranging from PIII 1GHz to P4 3.2HT. I might also be using this on an Athlon 64. Needless to say, the internal hard disks of these computers will also vary, so... any ways?

---

### Post by glotz on 2006-06-09
Can you access the BIOS of those computers? Can you change boot order? That's the only way. Then you can have live CDs and USB sticks (and maybe even external harddisks.)

---

### Post by nolongerlivecd on 2006-06-11
It's not a BIOS problem. I'm asking because the computers (i use "they" here) are running on PIIIs, P4s P4 HTs, PD, Celeron, A64, ATi, Nvidia and Integrated graphics. Is it possible to have one installation in less than 10GB that uses all these?

---

### Post by glotz on 2006-06-11
Sure. The processor type is irrelevant, only architecture matters. (PC (Intel x86) / 64-bit PC (AMD64) / Mac (PowerPC)) I'm not sure if you can have multiple video drivers installed at once, probably, but you'll still need to reconfigure which one to use if you switch from nvidia to ati to integrated. 10 gigs will easily do to install all that.

(2 full installs, for x86 and AMD64, ~2 gigs a pop and three video driver sets for all of them ~max 50 megs a pop would make just 2*2G + 2*3*0.05G = 4,3G )

---

### Post by nolongerlivecd on 2006-06-11
Hey, if I want to add in 64-bit as well? Would I have to have a seperate install or what?

---

### Post by nolongerlivecd on 2006-06-12
Can anybody tell me, so how do I have 32-bit and 64-bit Ubuntu coexist on a single hard disk?

---

### Post by glotz on 2006-06-12
Yes they can. There's nothing that'd restrict it. Simply to make separate partitions for each /. Swap they can share. And any data partition naturally. After install you'll possibly have to edit /boot/grub/menu.lst files on both partitions. (Dunno how the installer reacts to this situation, i.e. will it automatically make the appropriate boot entries) Or then you could possibly make a separate /boot partition for the latter install and then remove it and combine the space to some other partition. I'm not sure if you'll need two boot folders/partitions.

---

### Post by nolongerlivecd on 2006-06-12
I'm quite confused, I'm afraid I don't get you. When it boots, it would look for /boot right? So wouldn't that contribute to needing 2 /boot because of having two architectures and thus two different boots?

---

### Post by glotz on 2006-06-12
You will need separate kernels, sure, and maybe something else but maybe they can reside on a single /boot or maybe not, dunno.

---

### Post by nolongerlivecd on 2006-06-18
Is it possible to install Ubuntu on a computer that does not support booting from external HDDs but finish it on one that does?

---

