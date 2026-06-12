---
title: "Windows 7 Dual Boot Problem"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by PadawanGeek on 2009-11-19
I have had Ubuntu running on my laptop for a while now, and decided to dual boot Windows 7 RC on my laptop. The installation worked great, and the Ubuntu partition was preserved, but I can't get to Ubuntu because the grub doesn't come up when I boot. It just goes straight to "Starting Windows" screen.

How do I get the grub back so I can get into Ubuntu?

---

### Post by frriction on 2009-11-19
This link will help you
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by raymondh on 2009-11-19
@ frriction .....GRUB2 works on a Karmic install so it'll depend on what version ubuntu the OP is using :)  

@ OP ..... Your ubuntu ID box says you are running 9.04 Jaunty.  Is that so?  When you installed win7, it overwrote its' bootloader in the  MBR.  

IF YOU ARE RUNNING JAUNTY, you need to re-install GRUB (legacy).  Here's one of the many links/tutorials:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

IF YOU ARE RUNNING KARMIC, then you need to re-install GRUB2.

Happy ubuntuing.

---

### Post by PadawanGeek on 2009-11-19
Oh, sorry, I haven't updated my info in a while. Yes I am using 9.10. We'll see if this works...

---

