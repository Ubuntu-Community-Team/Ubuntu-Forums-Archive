---
title: "Install hang up loading ide-cd module"
date: 2006-03-31
forum: Installation &amp; Upgrades
---

### Post by Calrider on 2006-03-31
Went for the default install of Ubuntu 5.10 (latest distro) on an older IBM Thinkpad (300 MHz, MMX - 128 RAM). It hung up on "Detecting hardware to find CD-ROM drives". The progress bar is stuck at 86%. Message underneath says: "Loading module 'ide-cd' for 'Linux ATAPI CD-ROM' ".

Thoughts? 
Help??

Thanks in advance,
Calrider

---

### Post by Calrider on 2006-03-31
PS:
I waited for 45 minutes before power-cycling the box and re-starting the install. Repeat performance - stuck at 86% with same error messages.

---

### Post by Panhead Bill on 2006-03-31
I have had similar problems getting Ubuntu to install, The causes incuded a flaky stick of RAM, a Video board (very old) that somehow stopped the install), an incompatible CD-ROM (3 actually, I had to pull a drive out of a PC that already proved good to install Ubuntu in order to get further in the install).

The first thing I'd do is use the live cd but instead of hitting enter, type:
    memtest     
and then hit enter.  If it passes, go on to step 2.

The second thing I'd do are to see if the live CD will run Ubuntu on your PC; that helped me to diagnose the CD-Rom and Video issues.

These are very basic things, but since I didn't do them, Mr. Murphy got me.

---

### Post by Calrider on 2006-04-03
Thanks for the reply...I'll let you know if I find anything out.

---

### Post by alex1077 on 2007-11-20
same problem during instalation on NEC Versa FP520:
"Loading module 'ide-cd' for 'Linux ATAPI CD-ROM' "
:confused:

---

