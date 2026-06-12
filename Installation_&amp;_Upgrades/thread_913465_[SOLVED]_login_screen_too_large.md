---
title: "[SOLVED] login screen too large"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by clownbarf on 2008-09-07
on a fresh install of 8.04.1, got my voodoo3 card setup for 1280x1024 and all is well except...

the login screen is at the wrong resolution. the user/password entry is in the lower right corner of the screen rather than centered.

I tried the Startup-Manager tool and it did not help.

any ideas?

Thanks,
Dave

---

### Post by lost_soul on 2008-09-07
just edit the xorg.conf file by doing : sudo gedit /etc/X11/xorg.conf

find the Screen section at the end of it there is "Virtual" and next to it is a resolution just change it to the resolution u want it to be displayed in that should work.

---

### Post by clownbarf on 2008-09-08
That worked great!
Thanks

---

### Post by johntc23 on 2008-09-26
That solution solved my problem also Thank You:lolflag:

---

### Post by robc02 on 2008-10-06
Thanks, that solved my problem too.

---

### Post by snaggapuss on 2008-11-14
cool, screen sort of fixed, well at least i can log in with out quessing where the log in square is.  One question though I have a flat screen which i run at 1400/900 the log in screen is now at 1024/768 which as i said sort of fixed it.  If i set it at 1400 its way too large, any way to set the log in screen to right res.

---

### Post by jdkirker on 2008-11-14
I'm searching for an answer to the installation problems I'm having with 8.10. Currently running a Celeron 2.4 Ghz PC, 1 GB RAM and an older VooDoo video card. Whne I try to install from the CD, I get to the main menu page and when I choose to install Ubuntu, the screen goes blank and gives some type of screen resolution message. I successfully installed Edubuntu on an older laptop for my kids, so have been through this before. 

Thanks to all for any assistance.

---

