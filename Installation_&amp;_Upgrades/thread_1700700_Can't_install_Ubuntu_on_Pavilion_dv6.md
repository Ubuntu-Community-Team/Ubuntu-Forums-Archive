---
title: "Can't install Ubuntu on Pavilion dv6"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by m_zeid on 2011-03-05
Hey everyone,
first of all,sorry for the long post, trying to give you all the info.

OK I gave up after messing up with ubuntu for the whole day, and I'm wondering if anyone can help me.

So I have HP Pavilion dv6 with core i5 64bit.(btw can I install the AMD64 ubuntu version on it? ).

Currently I'm trying to install x86 ubuntu but with no luck, at first the installer and Gparted won't recognize the partitions correctly. From win7 I shrinked C in order to have an unallocated disk space, but when boot with live cd the installer recognized it as unusable !!

so returned back to win7, and tried to creat a partition from there, it gave me a warning about changing the drive from "**basic**" to "**dynamic**" with a possibility of an unbootable OS !!
after hours of hesitation, I did it, and it was ok. 

now I have the partition frmated with ntfs, and the win7 partition and one for system recovery. The problem now is win7 is dealing great with the partitions, but while using ubuntu installer/gparted, they are mixing the partitions with each other. 

[B]cant get a screenshot so I'll write them, what I really have:
1 mb -system
~200 mb- something for the systm also :S
65.7 GB - win7 (C:)
300 GB - storage -label:"My Drive"
80 GB - this one for Ubuntu Label:"Ubuntu"
20 GB - HP Recovery system drive
----
what I'm getting from GParted:
1 mb -system
~200 mb- something for the systm also :S
65.7 GB - here it gives the label "My Drive" which is incorrect
399.87 GB - label:"ubuntu"
1 mb unallocated[/B]
--------
You can see how it is all mixed up, I'm very worry about loosing my hp recovery drive.
how can I get it right??
Again,sorry for the long post, trying to give you all the info.

---

### Post by m_zeid on 2011-03-05
got some screenshots, I will post one for gparted as soon as possible

---

### Post by m_zeid on 2011-03-06
[CENTER][SIZE=3][COLOR=DarkOrange]**still waiting any help..**
[/COLOR][/SIZE][/CENTER]

---

