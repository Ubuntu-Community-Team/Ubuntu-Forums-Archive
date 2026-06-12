---
title: "Hard Drive Partitions and Ubuntu"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by taurks on 2009-12-13
Hi. Just a question: 

I put Ubuntu onto a laptop which was originally a Vista laptop. I didn't partition my hard drive or anything for Ubuntu, I just installed Wubi and that program did the rest. Right now I know I have a 200GB hard drive, and I know that I have most of it free - however, Ubuntu says I only have 12 gb left (see attached files)... Does anyone know why this is?

Thanks in Advance

Taurks

---

### Post by staf0048 on 2009-12-14
I'm guessing that in your second screen shot, Ubuntu is referring to your Ubuntu partition only  Did you set a specific partition size for Ubuntu or did the Wubi installer not give you that option?

Also, is the 1st screen shot more reflective of your actual total drive usage?  Or does that seem off as well?

---

### Post by Madasamy on 2009-12-14
Hi All, 
 I am also facing this issue. Have installed Windows XP first and then Ubuntu later just like the questioner done. But i guess the cause is as follows.. 
1. We did partitioning initially using Windows Xp. There whatever we are giving for C, is not coming in the Ubuntu .. I think in order to make the C Drive reflect in Ubuntu , we need to uninstall the Windows ( take back up before that, and then install the Ubuntu again.

If any more suggestions for our phroblems, Please let us know friends.

Have a good day ahead.

---

### Post by darkod on 2009-12-14
> **taurks said:**
> Hi. Just a question: 

I put Ubuntu onto a laptop which was originally a Vista laptop. I didn't partition my hard drive or anything for Ubuntu, I just installed Wubi and that program did the rest. Right now I know I have a 200GB hard drive, and I know that I have most of it free - however, Ubuntu says I only have 12 gb left (see attached files)... Does anyone know why this is?

Thanks in Advance

Taurks

When you install wubi it asks you how much space you want to dedicate to it. wubi is sort of virtual ubuntu working inside that space. The free space shown depends on the space you allocate for it, not on what percentage of your hdd is free.
I'm not using wubi but it should work as I said.

---

### Post by taurks on 2009-12-14
Hi All,
 
I think I have the answer: Wubi doesn't partition a hard drive, it just uses however many gigs it is allocated in the main screen (where it says "installation size"):
 
 
[IMG]http://wubi-installer.org/images/wubi.png[/IMG]
 
 
So to change this to allow Ubuntu more space, do I have to uninstall and reinstall Ubuntu? 
[]("http://wubi-installer.org/images/wubi.png")

---

### Post by raymondh on 2009-12-14
> **taurks said:**
> Hi All,
 
I think I have the answer: Wubi doesn't partition a hard drive, it just uses however many gigs it is allocated in the main screen (where it says "installation size"):
 
 
[IMG]http://wubi-installer.org/images/wubi.png[/IMG]
 
 
So to change this to allow Ubuntu more space, do I have to uninstall and reinstall Ubuntu? 
[]("http://wubi-installer.org/images/wubi.png")

you remove a wubi-installed ubuntu like any windows program .... throught he ADD/REMOVE utility in windows.

---

