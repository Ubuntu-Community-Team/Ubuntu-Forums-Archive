---
title: "Dual boot on seperate hard drives"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2005-10-12
ok......after trying to install ubuntu 5.04 on the sata drive that contains my XP install, and failing miserably due to crashing and hanging......im gonna try and do the following

leave XP installed on SATA, and install  ubuntu on a partition on one of my IDE drives (i have two).

1. does it matter whether i install it on the master or slave IDE?

2. where will the MBR be written to when the boot loader is installed? i.e. should the install screw up again will a simple **recovery console** and **fixmbr** be sufficient to get me back into windows?

any other advice would be awesome too.....im a relative beginner here (only used xandros before and thats idiot proof)

---

### Post by jackmacokc on 2005-10-12
[QUOTE=renzokuken]ok......after trying to install ubuntu 5.04 on the sata drive that contains my XP install, and failing miserably due to crashing and hanging......im gonna try and do the following

leave XP installed on SATA, and install  ubuntu on a partition on one of my IDE drives (i have two).

1. does it matter whether i install it on the master or slave IDE?

2. where will the MBR be written to when the boot loader is installed? i.e. should the install screw up again will a simple **recovery console** and **fixmbr** be sufficient to get me back into windows?

any other advice would be awesome too.....im a relative beginner here (only used xandros before and thats idiot proof)[/QUOTE]


I would recommend doing it on the IDE master.

yes, recovery console should work - or at least it has for me...i'm running xp on an SATA drive and ubuntu on pri IDE, on my Dell Poweredge 400SC - no problem. I've uninstalled and gone back to XP as you've described once already and it was smooth as ice.

---

### Post by renzokuken on 2005-10-12
awesome, thanks for the reply Jack

i'll get on it tomorrow and let y'all know how it goes,

im gonna get ubuntu working on my box if it kills me

---

### Post by renzokuken on 2005-10-13
ok.......

install was going fine until i hit the bit where it says 

"Configuring Apt - Setting up primary installation repo"
 
....and then it hangs

this is exactly where it crashes everytime i try to install Ubuntu (and Kubuntu for that matter, both 64bit and 386 archs.) it seems odd that always the same place causes the problem and ive tried 4 different versions of various (K)Ubuntu CDs

could it be the way i'm burning the CDs? is there a specific/correct way to do it?

i'm using Alcohol 120% (in XP) and just using the settings it comes up with automatically (i.e. SAO/DAO, "customize" etc)

my hardware is

AMD 64bit 3500+
Asus A8V Deluxe
80gb SATA (Primary)
160gb IDE (master)
80gb IDE (slave)
512mb RAM

---

### Post by raublekick on 2005-10-13
I had a similar problem with 5.04 and I'm kinda weary about trying again with breezy. It worked fine with Fedora 2 when I tried it, but Ubuntu just got my Windows drive all messed up and fixmbr didn't work.

I'm thinking I messed something up in the partitioning part of the install though. If I'm installing Ubuntu to the IDE drive and GRUB to the Windows SATA drive, should I make the Windows partition active?

---

### Post by renzokuken on 2005-10-13
so its not just me then

ive been using Xandros 3 for the last year or so and never had any probs with that either.......

just seems to be Ubuntu

what do u mean by "making windows partition active"??? (new to alot of this)

i was really looking forward to trying out ubuntu too......i prefer debian distros, but by using Xandros i feel its too "pre packaged" for me to learn more of the inner workings of linux

---

### Post by raublekick on 2005-10-13
I'm not really sure what exactly an active partition is, to be honest. I really should though. I'm posting this from Ubuntu, but I have yet to test dual boot, I'll post if it worked or not.

---

