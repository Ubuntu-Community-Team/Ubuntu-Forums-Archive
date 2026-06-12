---
title: "Dual boot with windows on a RAID 0 array"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2008-01-10
Hey all,

Is this possible? At the moment I have to switch between the single drive and the RAID array in the BIOS to choose which OS to boot.

Is it possible to either:
1. Have the RAID 0 array as primary and install GRUB on it and boot to either drive from that

OR (more likely)

2. Use the single drive as primary, istall GRUB onto that but get it to recognise the RAID array as a RAID array (possibly using dmraid) and be able to boot Windows?

I've already tried adding Ubuntu into the Windows boot.ini and had no luck.

Kevpatts

---

### Post by kipling100 on 2008-01-10
Hi,

I got as far as installing Ubuntu on my RAID 0 set using dmraid following these instructions:

[http://ohioloco.ubuntuforums.org/sho...d.php?t=630644](http://ohioloco.ubuntuforums.org/sho...d.php?t=630644)

Interestingly, those instructions detail how to dual boot to XP on a RAID 0 set.

But after following those instructions, Ubuntu works fine, but I'm no longer able to boot into Vista.

Here is the thread I started regarding the GRUB error I get when I try to boot the Vista partition:

[http://ubuntuforums.org/showthread.php?p=4108081#post4108081](http://ubuntuforums.org/showthread.php?p=4108081#post4108081)

I love ubuntu so far, but I really need to get my Vista partition loaded for my games :)

Best,

Dennis

---

### Post by kipling100 on 2008-01-10
UPDATE:

I fixed the GRUB problem as follows:

[http://ubuntuforums.org/showthread.php?p=4108081#post4108081](http://ubuntuforums.org/showthread.php?p=4108081#post4108081)

Best,
Dennis

---

### Post by kevpatts on 2008-01-11
Got it sorted anyway from you're post. Thanks man.

---

### Post by JonnyBlazexx on 2008-03-19
> **kevpatts said:**
> Got it sorted anyway from you're post. Thanks man.

Hey Kevpatts, how did you end up getting your install to work?  You have windows on your raid zero and ubuntu on another harddrive right?  I'm still lost!

---

### Post by ThePorthos on 2008-03-21
Link the the instructions described doesn't work. Is it in any other threads?

---

