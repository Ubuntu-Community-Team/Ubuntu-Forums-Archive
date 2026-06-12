---
title: "Black screen on boot - HP Envy 17 peculiar issues"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by pkchips on 2012-01-26
Previously I had Ubuntu working great, but have recently bought a new laptop, the HP Envy 17.

When running Ubuntu demo version from the CD, it works perfectly. However, when using wubi, I've tried 2 approaches with different results:

1. Using a downloaded image of Ubuntu 32-bit: Installation all completes perfectly, but then when booting into Ubuntu, after choosing kernel version, I get an odd screen with purple coloured fuzzy lines, and then a black screen. 

2. When installing without an image, wubi downloads 64-bit Ubuntu and installation proceeds smoothly, and this time Ubuntu boots up from my harddrive and **works perfectly**. However, after testing for about 5 minutes, I decide to reboot the system to make sure it really is working. When the menu shows up and I select Ubuntu, the same error as before occurs with the corrupted splash screen and then black.

Clearly, Ubuntu is working on my hardware otherwise the 64-bit wubi install wouldn't work even once, and the liveCD shouldn't work either. 

I was wondering how I can find out what the source of this problem is and/or how to fix it?

---

### Post by pkchips on 2012-01-26
The problem is fixed :D. In case anyone experiences similar issues, I'm not sure what exactly fixed it, but it's one of these 2 things:

1. I re-installed the wubi 64-bit downloaded Ubuntu and after installing, I installed the ATI/AMD FLGRX drivers.

2. I permanently added the nomodeset command on grub (whatever that means). [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

