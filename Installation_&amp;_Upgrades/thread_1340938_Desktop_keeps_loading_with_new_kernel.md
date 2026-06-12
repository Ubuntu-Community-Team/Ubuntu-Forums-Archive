---
title: "Desktop keeps loading with new kernel"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by fredie007 on 2009-11-29
Hello,

A few days ago I installed the updates when I was prompted to do so, a kernel-upgrade was included (2.6.31-15-generic). Now when I boot with this kernel, I can get to my desktop, but a few strange things happen.

Whenever I mouse over the desktop, I get the 'loading'-cursor; all newly opened windows seem to open behind my top-panel and last but not least, mouse-scrolling seems to lag behind and is jerky.

I think it has something to do with Compiz, because my desktop isn't transparent and I can't switch to the other 3 desktops. I'm not sure however, because my keyboard shortcut to open a terminal doesn't work.


Anyone who had a similar issue or who has a possible solution?

---

### Post by dhavalbbhatt on 2009-11-29
Can't you just login to the older working kernal? You should get a grub prompt for 2.6.31-14 kernal, login to that kernal, till there is a fix for the problem that you are having or wait until the next version of the kernal is released.

---

### Post by fredie007 on 2009-11-29
Yes I can, as a matter of fact, I'm still working with the older kernel. But I figured I should get it working because it may be like that in all future kernel updates.

---

### Post by wojox on 2009-11-29
Reboot into .15-generic. On login screen, click user name, and enter password, but don't hit enter yet. Select "failsafe gnome" from the session list at bottom of screen, then login.

Go to System->Administration->Hardware Drive to install video driver.

Reboot.

See if that helps.

---

### Post by fredie007 on 2009-11-29
I wanted to do what Wojox suggested, so I uninstalled the driver(the one that was installed), restarted, but now I can't get past the white logo. I've tried in recovery mode, but as soon as I start 'X', I get the static white logo and thereafter a pitchblack screen. 

Anyone know how to install those drivers from the command-line or how to fix this?

edit: dpkg wants to install ubuntu-desktop, but doesn't succeed... I'd like to install it with internet-access from the live-cd, but how do I log in to my system from the live-cd?

edit2: I've gotten there using chroot, but apparently no internet connection when I'm logged in as root on my system.

---

