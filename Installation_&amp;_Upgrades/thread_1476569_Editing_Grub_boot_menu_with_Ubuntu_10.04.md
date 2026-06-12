---
title: "Editing Grub boot menu with Ubuntu 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by billiusmaximus on 2010-05-07
He everyone,

I used to be a pro at editing Grub's menu.lst file so I could have my menu look clean, simple, and easy to read. Now that I have set up 10.04 (Working beautifully now after a couple setbacks) the menu.lst file is no longer where it used to be (/boot/grub/menu.lst)

How do I edit my boot menu now?

Thanks,
Billius

---

### Post by kansasnoob on 2010-05-08
Look here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

and here:

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by kansasnoob on 2010-05-08
Oh, and if you want a really sweet custom menu:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

It takes a bit of work the first time around but the outcome is great.

---

### Post by oldfred on 2010-05-08
Grub2 is a change from grub. But it offers more features at the expense of some complexity. It is much better at finding other operating systems with sudo update-grub.

After you have reviewed Kansasnoob's links:

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom, parts copied from original grub.cfg.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

---

### Post by billiusmaximus on 2010-05-08
Thanks for the support. Appreciate it!

Billius

---

### Post by gavdari on 2010-08-19
I changed my grub menu to custom one a while ago. but then I wanted to try out BURG and I didn't like it so I removed it. now the custom menu won't work, although everything looks like exactly as told. what am I missing?

---

### Post by allanliu on 2011-12-14
**Just did it:**
dpkg -l | grep linux-headers-*

sudo apt-get remove linux-headers-2.6.32-25 linux-headers-2.6.32-25-generic

....

cd /boot
sudo rm -f *2.6.32-25*

....

sudo update-grub2

**[COLOR=Black]but better way should be:[/COLOR]**

dpkg -l | grep linux-headers-*

sudo apt-get remove linux-headers-2.6.32-25 linux-headers-2.6.32-25-generic


dpkg -l | grep linux-image-*

sudo apt-get remove linux-image-2.6.32-25 


sudo update-grub2

---

