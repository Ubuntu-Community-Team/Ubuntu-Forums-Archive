---
title: "Partitioning problem"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by CAUSTICROUTER on 2006-09-13
Hello, I recently used an Ubuntu liveCD and love the feel of it, and how secure I feel, so naturally, I wanted to install it.  The only thing is, I'm an big gamer, and as you all know, not alot of popular videogames are out of the box compatible with linux, so, I need to keep XP.  I tried partitioning first with a tool I downloaded, but, it needed to be burnt to a disc, and, for some reason, my computer doesn't like booting from burnt discs.  The reason I didn't want to use the linux partitioning tool was I heard it has dodgy support for NTFS filesystem.  I said screw it and tried the linux tool anyway, but, it just gave me an error saying that the partitioning was not completed. I need to partition my hard drive, but cannot find a free tool that works. Thank you all, Ubuntu community.
BTW on the linux installer I clicked and used the last option "manual partitioning". If I should've used the second one (forgot it, had something to do with partitioning).

---

### Post by meng on 2006-09-13
I didn't experience any problems with the Ubuntu LiveCD partitioner myself, do you remember exactly what error you got? And I wouldn't choose the second option, I think it uses all the free space you have, which wouldn't leave you much room for installing future games on Windows.

---

### Post by CAUSTICROUTER on 2006-09-13
> **meng said:**
> I didn't experience any problems with the Ubuntu LiveCD partitioner myself, do you remember exactly what error you got? And I wouldn't choose the second option, I think it uses all the free space you have, which wouldn't leave you much room for installing future games on Windows.

Well, I think it just said partitioning failed, but, I'll try again later just to be sure.  Thanks.

---

### Post by meng on 2006-09-13
Thanks? I haven't even helped yet. I was going to suggest using the GParted LiveCD, but you said that your computer doesn't like burned CDs. Which, by the way, confused me, since isn't the Ubuntu LiveCD burned? Was it a Shipit CD? I wonder whether your problem with burned CDs would be resolved by burning at a lower speed.

---

### Post by CAUSTICROUTER on 2006-09-13
> **meng said:**
> Thanks? I haven't even helped yet. I was going to suggest using the GParted LiveCD, but you said that your computer doesn't like burned CDs. Which, by the way, confused me, since isn't the Ubuntu LiveCD burned? Was it a Shipit CD? I wonder whether your problem with burned CDs would be resolved by burning at a lower speed.

Well, the CD get's burnt, but, with startup with bootable discs, It says that there was an error loading DoS. It was a shipit CD btw. I burn CDs at 48x with CD burner pro XP with disc's set to bootable with no emulation. I said thanks because I appreciate your attemp to help me with my problem.

---

### Post by meng on 2006-09-13
Don't burn CDs as bootable! If you burn from an ISO, and create the filesystem packaged within the ISO, then it will be bootable by default.

---

### Post by CAUSTICROUTER on 2006-09-13
> **meng said:**
> Don't burn CDs as bootable! If you burn from an ISO, and create the filesystem packaged within the ISO, then it will be bootable by default.

So should I use Gparted to partition then? Thanks for possibly resolving my problem.

---

### Post by meng on 2006-09-13
That's what I would do. Mind you, I get the impression that pre-partitioning tends to cause more problems than partitioning "during the install", but you already have problems during the install, so you can't very well do worse. Is your hard drive massive? I sometimes wonder if that is the main problem.

---

### Post by CAUSTICROUTER on 2006-09-13
> **meng said:**
> That's what I would do. Mind you, I get the impression that pre-partitioning tends to cause more problems than partitioning "during the install", but you already have problems during the install, so you can't very well do worse. Is your hard drive massive? I sometimes wonder if that is the main problem.

My HD is 93GBS with 19GBs free.

---

### Post by CAUSTICROUTER on 2006-09-13
Ok, so I burned Gparted as nonbootable, but it just hangs on my computer manufacturs slpash screen.  I am using the LiveCD now, I was trying to install  again, but, I got the same error. The error said "Error while moving/resizing dev/hd1"(my HD(didn't actually say this)).  I don't know what to do.

---

### Post by CAUSTICROUTER on 2006-09-13
I'm sorry if triple posting is frowned at, but, this post needs a bump.

---

### Post by CAUSTICROUTER on 2006-09-14
I really hope this doesn't make me seem, well noobish, but, I am still having the same problem, I will list my Hardware just in case that information is useful.
P4 2.53 GHz
Nvidia GeForce 6600
Onboard audio (Avance AC97)
512MBs of RAM
Unspecified motherboard
95GB HD, with 21GBs free
Windows XP Service pack 1
The reason I am installing linux dual boot, is, I really, really, hate windows, it won't let me download the service packs, and all antivirus software for it slows my computer at boot, and it slows it down immensenly once it gets up.  I was getting virus, deleting them, then, got tired of doing this.
Unfourntinately, most video games don't work on linux, so I need XP.  Thanks if you guys could help.

---

