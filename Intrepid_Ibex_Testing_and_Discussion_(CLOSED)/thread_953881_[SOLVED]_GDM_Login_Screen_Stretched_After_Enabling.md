---
title: "[SOLVED] GDM Login Screen Stretched After Enabling FGLRX"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hyper7 on 2008-10-20
I enabled the beta ATI driver for my Radeon Mobile card a while back and completely forgot about this problem.

After rebooting, the GDM Login screen was stretched so much so that I can't really see what I'm inputting for login infos.

It's been quite some time since I last rebooted, and when I saw it today I figured I should try and get it sorted.  Any help would be much appreciated.

---

### Post by hyper7 on 2008-10-20
Fixt.

I found this [Link]("http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/") and found that my xorg config had my resolution set to 2860*800.  No clue how that happened, but altering the rez fixed the issue.

---

