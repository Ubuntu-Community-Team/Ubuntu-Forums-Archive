---
title: "Problems instaling anything higher than 7.04...HALP"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by Akeroh on 2010-01-04
Well, I've been trying to install 9.10,8.10,8.04, and even 7.10 on an old-ish laptop (dell latitude, Pentium III, 30 gig hd) and it refuses. It will not. Installations of all of the above, pioneer basic and Debian hand at 15% or I get an I/O error partway through. It's starting to get infuriating, because i'm stuck on unsupported 7.04, so I can't install anything.
I've tried apci=off and other kernel commands, but I still get the same I/O errors....

---

### Post by Final Version on 2010-01-04
Non Oldish? Pentium 3?

---

### Post by Akeroh on 2010-01-04
Well, from what I've gathered in about a week of web searching, 'old' seems to be considered 256 megs (At best) of ram and maybe a Pentium I processor. Mine's a bit newer than that, with a Pentium III processor.

---

### Post by prshah on 2010-01-04
> **Akeroh said:**
> hang at 15% or I get an I/O error partway through. 

Please run a media check. If you have burnt the CD on a newer system, your old CD drive may not be able to handle the speed at which the CD has been burnt.

If the media check fails, please burn a CD at a lower (16x-4x) speed. If that CD too fails, then perhaps your old drive is giving out and you may need to consider a USB install or so.

---

### Post by Akeroh on 2010-01-04
I've already tried all of that. I know the hard drive is fine and that the cd drive is as well. The disk integrity is fine and i've burned it at the slowest possible write speed, 0.2x.

---

### Post by kellemes on 2010-01-04
> **Akeroh said:**
> Well, I've been trying to install 9.10,8.10,8.04, and even 7.10 on an old-ish laptop (dell latitude, Pentium III, 30 gig hd) and it refuses. It will not. Installations of all of the above, pioneer basic and Debian hand at 15% or I get an I/O error partway through. It's starting to get infuriating, because i'm stuck on unsupported 7.04, so I can't install anything.
I've tried apci=off and other kernel commands, but I still get the same I/O errors....

Have you tried some other distribution of Linux?
Just to rule out some issue with the Ubuntu installer?

---

### Post by Akeroh on 2010-01-04
Yes, I have. I've tried absolute, which worked, but very poorly, as it took over 30 minutes for x to start, and I have tried debian and pioneer basic. I do belive that it's a problem with the new ubuntu installer lacking older hardware support, and the threads with the same problem that i've found say to add the kernel commands apci=off. I've done that, along with noapci at the same time, but that hasn't worked either. I'm still getting hang-ups and I/O errors.

---

### Post by oldos2er on 2010-01-04
> **Akeroh said:**
> Well, from what I've gathered in about a week of web searching, 'old' seems to be considered 256 megs (At best) of ram and maybe a Pentium I processor. Mine's a bit newer than that, with a Pentium III processor.

The LiveCD requires 384MB RAM. You might want to try the alernate CD installer.

---

### Post by Akeroh on 2010-01-04
I do have 546 megs of ram, but I tried the alternate as well.

---

