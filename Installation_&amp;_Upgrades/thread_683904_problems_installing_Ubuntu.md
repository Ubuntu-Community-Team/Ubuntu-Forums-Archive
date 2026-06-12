---
title: "problems installing Ubuntu"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by zinzara on 2008-01-31
i've tried installing several versions of Ubuntu from 5.04 up to 8.04 and none are working. 8.04 freezes during the kernal loading when it starts up the live cd. 7.10 sometimes freezes while installing and sometimes comes up with the errno 5 error. 6.06 has the errno 5 error.  5.04 will install completely but when i try to boot up, it freezes right after i log in. i've used several discs, different burning programs. different locations for the downloads. nothing seems to work. i've even formatted the hard drive separate from Ubuntu and it still won't help. i'm trying to install ubuntu on the complete drive. i'm trying to install on my laptop. windows xp will install just fine on it. i even had freespire installed on it but decided to switch to Ubuntu. i'm somewhat new to linux and don't know many of the technical things about it. if anyone can help me i would appreciate it. and i hope i've given enough information. that's all i know so far.

---

### Post by overdrank on 2008-01-31
> **zinzara said:**
> i've tried installing several versions of Ubuntu from 5.04 up to 8.04 and none are working. 8.04 freezes during the kernal loading when it starts up the live cd. 7.10 sometimes freezes while installing and sometimes comes up with the errno 5 error. 6.06 has the errno 5 error.  5.04 will install completely but when i try to boot up, it freezes right after i log in. i've used several discs, different burning programs. different locations for the downloads. nothing seems to work. i've even formatted the hard drive separate from Ubuntu and it still won't help. i'm trying to install ubuntu on the complete drive. i'm trying to install on my laptop. windows xp will install just fine on it. i even had freespire installed on it but decided to switch to Ubuntu. i'm somewhat new to linux and don't know many of the technical things about it. if anyone can help me i would appreciate it. and i hope i've given enough information. that's all i know so far.

HI and could you tell us some specs on the system? You may also want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by dabl on 2008-01-31
Sounds like you have already tried to make sure you've got good CDs -- that's required, of course.

I would say there's probably a video driver issue behind some of the problems, if the CDs and CD ROM drive are working.

You might fare better with an Alternate Install CD -- download the ISO and burn it at 4X.  It provides a character-mode installation routine, and multiple options for video that might make it easier to get around the lack of a driver (for installation purposes).  When you boot it, look at the "boot options" for video, and try different ones like "VGA 640x480", "VESA" and so forth, and see if one of them appears to let the installer display reasonably on your screen.

Hope this helps.  :)

---

### Post by zinzara on 2008-01-31
the laptop is a Compaq Presario V5000. it has an AMD Sempron 1.8GHz, ATI Radeon Xpress 200M Graphics, upgraded to 2GB of RAM (shared with video card) i think 128 is shared. 60GB Hard drive, that's about all i really know about it. the checksum on the file checked out ok. but the disc had 1 error. so, what is a good program to use to burn image files? is that the problem? i've used Nero and InterVideo Disc Master 2 so far. oh, i'm on Windows XP right now. on my desktop.

---

### Post by dabl on 2008-01-31
Nero is a reasonable burner.  Make sure you "burn as ISO" on the choices for burning mode, and keep the speed down to 4X.

There is such a thing as a defect in the blank media, too -- that could account for the error you found.

---

