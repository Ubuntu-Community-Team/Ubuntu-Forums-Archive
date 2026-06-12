---
title: "Smart Boot Manager is being stupid - &quot;SBMK bad!&quot; error!"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by jordoex on 2006-10-28
Ahhhhhhhhhhhhhhhhhhh!
I was able to use smart boot manager to install xubuntu 6.06, and now I want to do a fresh install of edgy. when I first used sbm, it worked perfectly, at least 2 times, to load the xubuntu 6.06 alt. install.  Now I want to reformat the part with xubuntu 6.06 on it and install 6.10.  The computer i installed xubuntu on [has no internet]("http://www.ubuntuforums.org/showthread.php?t=277071"), btw. 

Info on computer:
Pentium 2, 96 MB RAM(i might be getting an extra 128 chip from my friend if he can find it), 2 old CDROM drives that can only read CD-Rs (no CD-RWs)(can't boot ISOLINUX without SBM), 2 USB ports(how i get stuff onto that computer), an old sound blaster card that xubuntu doesn't seem to recognize.
 
So, here's the confusing part: if I install SBM from a static release(sbminst-static or using dd to extract to a floppy) it will always pop up with "SBMK Bad!" when I start up.  If I use regular sbminst, the boot up sequence doesn't even seem to recognize that there even is a floppy, it just goes directly to grub without even saying "Non system disk error" or "SBMK Bad".  I have tried multiple exraction versions, sbminst and sbminst-static 3.7 R1 and 3.6 R4. I have also tried Gujin, with no luck(continually spat out Gujin2... GUjuin1 error, or something like that).Please help or I might have to resort to reinstalling Windows 98!

---

### Post by jordoex on 2006-10-28
I don't care if you don't like it, but I'm bumping.  I need this issue solved!

---

### Post by jordoex on 2006-10-28
I think I figured out a reason why SBM is screwing up.  The boot sector on the hard drive is full or screwed up in some other way.  does anyone know how to detect and or fix errors on the boot sector of the disk? I thought of this because I tried running SBM on my P3 with winXP and the BIOS thought there was a virus and so I Googled it and one of the things was [this]("http://blog.gmane.org/gmane.comp.boot-loaders.smart-boot-manager/month=20021201"),
which gave me that idea.
Someone PLEASE help me!

---

### Post by jordoex on 2006-10-28
Bump! Please, somebody help me!

---

### Post by jordoex on 2006-10-29
BUMP! Cmon, I need help!

---

### Post by jordoex on 2006-10-31
bump

---

### Post by jordoex on 2006-10-31
bump

---

### Post by confused57 on 2006-10-31
Maybe this will help:
[http://www.ubuntuforums.org/showthread.php?t=246486](http://www.ubuntuforums.org/showthread.php?t=246486)

---

### Post by jordoex on 2006-11-02
Nope, didn't work.  Same as all the previous 100 tries(probably more like 20).  Again I'm asking here: is it possible that the boot sector of the disk is corrupted? If so, how do I fix it? And if not, why won't SBM work?

---

### Post by jordoex on 2006-11-06
bump

---

### Post by jordoex on 2006-11-09
bump

---

### Post by QB89Dragon on 2007-12-20
I have this problem as well. I believe it could be a deteriorating bios (battery?) or you could try making the startup disk again.

---

