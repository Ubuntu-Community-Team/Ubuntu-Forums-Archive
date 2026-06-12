---
title: "grub error 18 please help"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by five_tools on 2008-05-06
I'm getting a grub error 18 after I installed Kubuntu.  

My configuration already consisted of XP and Kubuntu.  But, I wanted to try Kubuntu KDE4 so I just re-sized the first Kubuntu partition to make room.  So now I have XP on the first partition, then Kubuntu on the second and another Kubuntu on the third.

In hindsight I wish I never even did it, because I can't use my computer at all now because of the grub 18 error.

Can anybody help?  I don't even care about either Kubuntu installation.  I would delete them if I knew how, and if it got rid of the error.  I just need to be able to use Windows again, because that's the one my family and I use regularly.

p.s. I know what the error means, but the only way I've read how to fix it is to put a boot partition at the beginning of the xp partition.  But that's way over my head.

---

### Post by Scheater5 on 2008-05-06
Bulldog once salvaged a borked grub of mine with [these instructions]("http://ubuntuforums.org/showthread.php?p=1587929").  YMMV, especially considering the problem could stem from the resizing of partitions.  For future reference, KDE 3 and KDE4 can easily coexist.  Just install the KDE4 metas from the ubuntu repos (kubuntu-desktop-kde4, I believe is what it is called) and you'll find KDE4 in your session menu.

---

### Post by five_tools on 2008-05-06
That's for reinstalling grub, right?

I don't think that's going to fix it, because even with a brand new install, grub is still going to produce that error.

Anyone else?

---

### Post by Pumalite on 2008-05-06
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
This implies you might need to make a /boot partition of about 200 MB.

---

### Post by five_tools on 2008-05-06
Pumalite: I'll try that.  It doesn't look easy, though.

---

### Post by Pumalite on 2008-05-06
Good luck.

---

### Post by five_tools on 2008-05-06
Well, I've been trying to access "setup" so I can check the bios version.  But even that is a challenge.  I'm pushing the keys Compaq told me to push (f1 or f10; I've also tried f2 and del to no avail).

I'm getting frustrated, so I think I'll pick this up tomorrow.

I'm still open to new ideas.

---

### Post by PhucilliJerry on 2008-05-06
> **five_tools said:**
> Well, I've been trying to access "setup" so I can check the bios version.  But even that is a challenge.  I'm pushing the keys Compaq told me to push (f1 or f10; I've also tried f2 and del to no avail).

I'm getting frustrated, so I think I'll pick this up tomorrow.

I'm still open to new ideas.

Don't give up, I'm a complete noob to linux and I managed to work around this.  I had to setup three partitions on my HD, 1. boot partition, 2. file system (or whatever you call it) and 3. a swap partition.  Once I did this and re-installed, the Grub error was gone.

Good luck.

---

### Post by five_tools on 2008-05-07
It's fixed.  I reinstalled kubuntu over top the first Kubuntu.  And at the same time, I deleted the third partition and swap.

Thanks, everybody, for responding.

*Scheater5
*Pumalite
*PhucilliJerry

It felt awful not being able to use my computer.

---

### Post by Scheater5 on 2008-05-08
No worries, glad you got it fixed.  Let us know if you have any trouble getting kde3 and kde4 installed.

---

### Post by Pumalite on 2008-05-08
Happy Ubuntuing!

---

