---
title: "I believe I'm having trouble with my AMD A10-5800K Radeon HD 7660D"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by MaunderingMoose on 2013-03-03
With a new disdain for M$, I'm commited to making Ubuntu work on my freshly built PC.

So far, I've got ubuntu installed but I've had to insert "nomodeset" when booting or otherwise the screen becomes squished and jittery. I could edit the grub file in etc/default to fix that problem, but there's no resolution option for my display so I still wouldn't be able to use the default driver. I tried the two alternative drivers in the Additional Drivers tab in Software Sources; they didn't require nomodeset and had much more acceptable (but not perfect) resolution options, but they broke Unity. I tried installing AMD's latest stable Catalyst driver with an installation program I found online, but that didn't appear to do anything but "break packages" (not sure what that means, but it sounds bad).

Also, Compiz crashes multiple times when I first run Software Updater after an install.

I really need to get this thing running full-force with Ubuntu. Not only can I barely afford to buy a builder's edition of Windows, I would feel ****** every time I used it. I was first forced to use Windows when in elementary school 15 years ago. Now I might have to go back to it against my will as an adult because my hardware isn't compatible with anything else. Boo.

I just did a fresh install and did the nomodeset thing at boot, but have done nothing else.

Any help would be sincerely appreciated.

---

### Post by ronparent on 2013-03-03
I've been running the same MB both with the built in APU as well with a separate Radeon card with no problems for several months, and with the default drivers. My initial problems were with installing to a raid0 but subsequent install to an ssd was without issue. I run the system with dual hi res monitors at native resolution also without problem. Also I have had better success (less complications) without the ATI proprietary drivers.

Can you boot a 'live CD' without the nomodeset?

---

### Post by MaunderingMoose on 2013-03-03
I only have one HDD; if I understand what raid is. I don't have a cd  drive, I used a USB with the last install (I assume that counts as live  CD too). Come to think of it, I went ahead and used the nomodeset option  the first time I did a Live CD install, because I had to do it with the  wubi install. I'll try installing it again and see what happens.  Thanks.

---

### Post by Bashing-om on 2013-03-03
MaunderingMoose; Hi !

Have you booted via "nomodeset" and used the "Additiional Drivers" utility to install the recommended graphics driver ?[INDENT=2]
hope this helps

[/INDENT]

---

### Post by xlizarralde on 2013-09-12
I have same problems with same computer. did you fix it? how did you it?
thanks in advance

---

