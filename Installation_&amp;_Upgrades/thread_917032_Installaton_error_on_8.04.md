---
title: "Installaton error on 8.04"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by TechnoCoach on 2008-09-11
I get that same error message when I try to install any version of Ubuntu 8.04.1.  I boot from the CD, I choose the language, then select "Install Ubuntu" and it takes off.  However, after a few minutes of looking at the Ubuntu splash screen, I get a blank screen then the error message:
"Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) built-in shell (ash)

Enter 'help' for a list of built in commands ( I enter 'help' after (initramfs) ) and I get this:

(initramfs)"

type in 'help' then enter and I get the same list as you.

I just tried loading Ubuntu without making any changes, and I get the same error message.

HELP!

Gary

---

### Post by overdrank on 2008-09-11
> **TechnoCoach said:**
> I get that same error message when I try to install any version of Ubuntu 8.04.1.  I boot from the CD, I choose the language, then select "Install Ubuntu" and it takes off.  However, after a few minutes of looking at the Ubuntu splash screen, I get a blank screen then the error message:
"Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) built-in shell (ash)

Enter 'help' for a list of built in commands ( I enter 'help' after (initramfs) ) and I get this:

(initramfs)"

type in 'help' then enter and I get the same list as you.

I just tried loading Ubuntu without making any changes, and I get the same error message.

HELP!

Gary

Hi and welcome TechnoCoach,  You may try and use the F6 option from the install window on the live cd. this will allow you to edit the kernel line and remove quiet splash and add noapic before the --
Could you give us some system specs? Also have you checked the cd for errors?
Also I have moved your post to its own thread as to not highjack the other thread. :)

---

