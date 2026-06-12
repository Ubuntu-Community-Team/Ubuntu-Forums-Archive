---
title: "Ubuntu 7.10 will not load"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by Rings on 2007-12-01
I just tried installing ubuntu on my computer

AMD 64 4400
Nvidia GeForce 8500GT 512
1024 Megs of Ram

I had to use the alternate CD to get the initial install working.

When booting normally the screen turns off.
When booting in recovery mode I get the command prompt. I already adjusted my settings using

sudo dpkg-reconfigure xserver-xorg

When I enter startx the screen goes blank and nothing happens. I read about something called Envy, but I don't have a internet connection setup on this machine yet so I can not download it.

---

### Post by scrawford on 2007-12-01
I'm a Linux noob, but I have found that you will need an internet connection in order to get 7.10 to load properly.

You may want to try dual-boot with another OS to ensure you have an internet connection first, and then try the Ubuntu install.

There's lots of good stuff on these forums about loading a dual-boot system.

---

### Post by Lagos on 2007-12-01
You dont need an internet connection for it to boot up.

It sounds like your monitor is not being detected correctly. I had the same issue and worked around it by turning off the monitor after the first time ubuntu tried to initialize the graphics card. When I did that, it defulted into 800x600 mode, and I got into the desktop.

---

### Post by steverido on 2007-12-01
Hi, I am having the same problem. I have downloaded the 64 bit operating system and burnt to a bootable file on CD. I have configured my bios to boot from CD and I have configured my hard drives (4) so that it boots to an empty hard drive. The Ubuntu logo comes up with options to load. I have tried it with the first option and the safemode for graphics.

What happens is it looks like it is loading and then my screen goes black.

Does anyone have any solutions?

---

### Post by Rings on 2007-12-01
My monitor still went into standby. I can hear the hard drive working like it is loading.

I am using a Sharp LL-173C-B LCD monitor

I checked the refresh rate and the horizontal scale on the back of the monitor and they match up with my xorg.conf file.

---

