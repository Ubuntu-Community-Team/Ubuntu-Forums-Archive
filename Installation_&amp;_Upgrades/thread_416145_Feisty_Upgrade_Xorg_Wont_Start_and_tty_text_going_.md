---
title: "Feisty Upgrade Xorg Wont Start and tty text going off screen"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by herrkutt on 2007-04-20
Hi all.
I did the upgrade using an alternate CD (my internet sucks and I got it from a friend) the installation went fine until the reboot.
Now X doesnt want to start, I know this is a common problem but ive tried the basics so far. Reinstalled X from the CD and from the net and did the dpkg-reconfigure and I even tried using an old xorg file that I had still backed up from before the update. 
BUT 
Thats not the only thing now when I try to boot into regular ubuntu and it brings me to the tty console after X fails the console text goes off the bottom of the screen...I have to blindly type clear every once in a while to see whats happening. (This doesnt happen in recovery mode)

Ive included my xorg.conf and the X.0.log file as attachments, hoping they will be of some use. 
Im running it on an Acer Aspire 3613WLMI with 1gig Ram with the Intel 915 Chipset.

Any help is appreciated thanks :-D

---

### Post by herrkutt on 2007-04-21
Bump Post.
Sorry but I still cant get it.
Now Ive somehow uninstalled xorg-air-core and it doesnt want to reinstall.
Thanks again

---

### Post by mhansen on 2007-04-21
Try the i810 driver.


Regards,
Mike

---

### Post by deviantintegral on 2007-04-22
If you're having problems at the console, perhaps your framebuffer is set up incorrectly? It could be two seperate problems.

---

