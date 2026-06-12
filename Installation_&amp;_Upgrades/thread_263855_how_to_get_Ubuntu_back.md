---
title: "how to get Ubuntu back"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by howardepgco on 2006-09-23
I have a hundred gig h.d and until this afternoon Ubuntu had all of it.I wanted to try PCOSlinux so I partitioned the drive so both systems shared the drive about 50/50.I loaded the PClinux on the newly created partition no problems,however,now on bootup I get a menu with XP and PClinux.Ubuntu is not on the boot menu.How do I get it back? I can't format the drive as most of my music is on Ubuntu and it is still my preffered OS. I don't mind that Ubuntu still shares the drive as I would still like to toy with PCOSlinux.Any suggestions?

---

### Post by K.Mandla on 2006-09-23
It sounds like PCLinux overwrote Grub and omitted Ubuntu from it. Is that possible?

Try booting into PCLinux and giving it *sudo fdisk -l* (I don't know if PCLinux uses sudo or not. ;) )

From there you should be able to see if the Ubuntu partition is still there. If so, you should be able to edit Grub and add the Ubuntu partitions again. There's a good [primer on Grub]("https://help.ubuntu.com/community/GrubHowto") in the wiki.

---

