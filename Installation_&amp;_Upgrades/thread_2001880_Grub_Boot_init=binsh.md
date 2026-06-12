---
title: "Grub Boot init=/bin/sh?"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by scrop on 2012-06-11
Hey, I want to boot directly into bash to fix a problem with my system. I used to do this all the time by editing the grub command line and adding init=/bin/sh to the kernel parameters. 

With the current Ubuntu and GRUB2, I don't see able to do this. I've added init=/bin/sh but I never see output from the kernel.

---

### Post by scrop on 2012-06-11
Also, is there any way to boot in all text? The framebuffer stuff is nice, but it's just obscuring what's actually happening - I'd much rather see what's going on

---

### Post by wilee-nilee on 2012-06-11
[COLOR=White].[/COLOR]

---

### Post by drs305 on 2012-06-11
Do you want to boot into Recovery mode? If so, there should be an option on the Grub menu. If you don't see the menu during boot, hold down the SHIFT key.

If you don't have the recovery option on your menu but that is what you want to boot to, highlight the main entry, then press 'e' to edit it. 
Cursor to the end of the "linux" line. Remove "quiet splash" and the vt handoff entry and add "single"

ctrl-x  or F10 to boot.

If you want to boot to a non-recovery normal text login, remove  the same as above but add "text" then F10. "text" is an Ubuntu kernel option which allows booting to a non-GUI login.

---

