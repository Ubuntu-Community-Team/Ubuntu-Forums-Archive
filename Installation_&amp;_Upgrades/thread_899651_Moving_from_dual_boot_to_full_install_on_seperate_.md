---
title: "Moving from dual boot to full install on seperate drive"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by kronprinz311 on 2008-08-24
I've been dual booting 8.04 and XP for a couple weeks now, just to get used to Ubuntu, and I love it. My machine is a 733Mhz Pentium with 512Mb Ram. MY H.D.D. only has a gig left. Ubuntu runs fine, but XP is WAY slow.

So I just put in a second hard drive in my machine and would like to do a full, proper install of Ubuntu on that drive and keep XP on my other and clean it up a bit.

So basically I have 3 questions:

[LIST=1]
[*]Is it possible to install Ubuntu (full installation) and XP on separate hard drives and still have the little boot menu at the beginning?
[*]Is there a way to copy the Ubuntu installation I have now, because I have it set just right and I just got my Rails environment working properly, onto this new full install?
[*]If doing all this is possible, would it be worth it performance-wise or would I just be better of cleaning out my main H.D.D.?
[/LIST]

What do you folks think?

Thanks!

---

### Post by Patb on 2008-08-24
> 1. Is it possible to install Ubuntu (full installation) and XP on separate hard drives and still have the little boot menu at the beginning?
Yes. See [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

> 2. Is there a way to copy the Ubuntu installation I have now, because I have it set just right and I just got my Rails environment working properly, onto this new full install?
I don't know the "Rails environment" but after a new install you can easily copy most things from your old /home folder to a new one to update settings from the defaults. Just make sure your old /home folder is not on a partition which is formatted during the new install.

> 3. If doing all this is possible, would it be worth it performance-wise or would I just be better of cleaning out my main H.D.D.?
Cannot say - it depends on what "performance" you are getting now. Why not try it and see? 

Cheers, Pat

---

### Post by Sef on 2008-08-24
[Clonezilla]("http://www.clonezilla.org/") and [partimage]("http://www.partimage.org/Main_Page") will both clone your os.

---

### Post by kronprinz311 on 2008-08-25
Many thanks to both of you! Can't wait to get home and try it out!

---

