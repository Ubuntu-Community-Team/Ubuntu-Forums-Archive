---
title: "Some issues since Upgrad to 9.10"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by WadeH2o on 2010-01-04
I have been a Ubuntu user since 8.10. After my attempted update to 9.04 I was unable to boot, my machine would loop from the splash screen to restart.  I made a new partition and installed 9.04 and preformed the 9.10 upgrade last weekend. During the upgrade it did ask me five times what I wanted to do with menu.lst. Each time I choose to remain unchanged.To my surprise the machine would boot! However, my display has poor response (correct resolution), no audio, and  no touchpad. Not sure what else is missing behind the scenes.

Machine Details:
HP dv6000 (laptop)
Pentium Dual-Core 1.60GHz
Integrated video(?)

After reading for hours and hours, I believe one solution may be my Kernel. Does this sound right?

Here is some info that may be helpful. But I'm not sure which kernel I need to boot with, what are the deciding factors?
:popcorn:
```

wade@frog:~$ uname -r
2.6.28-17-generic
wade@frog:~$ apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image-2.6.31-14-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-14-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-14-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-14-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-302-ec2 - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-ec2 - Linux kernel image for ec2 machines
linux-image-2.6.31-9-rt - Linux kernel image for version 2.6.31 on Ingo Molnar's full real time preemption patch
linux-image-rt - Rt Linux kernel image
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
linux-image - Generic Linux kernel image.
linux-image-2.6.31-15-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-15-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-15-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-15-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-16-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-16-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-16-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-16-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-386 - Generic Linux kernel image
linux-image-generic - Generic Linux kernel image
linux-image-generic-pae - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image for virtual machines
linux-image-2.6.28-17-generic - Linux kernel image for version 2.6.28 on x86/x86_64

```

---

### Post by Jenkins1 on 2010-01-04
I am running a hpdv6799ea on karmic I have no problems I did how ever do a clean install, usually more likely to to work. I have a separate home partition to make things easier.

---

### Post by gabo.cr on 2010-01-04
I don't like upgrades, too many problems.
I always do a clean install also.

---

### Post by WadeH2o on 2010-01-04
> **Jenkins1 said:**
> I am running a hpdv6799ea on karmic I have no problems I did how ever do a clean install, usually more likely to to work. I have a separate home partition to make things easier.

I'm trying to avoid a fresh install but will do if its easier than fixing whats here...#-o

---

### Post by Jive Turkey on 2010-01-04
I would look into where your refresh rate is set fro you vga chip, historically it has been in /etc/X11/xorg.conf but more recently xorg.conf is not necessary.  If you have a proprietary driver installed use the config application for that.  If applicable, install the restricted driver.

I have an HP zv5460us and it has an nvidia chip so I use "sudo nvidia-settings" to get the config app going.

Otherwise look in System>Preferences>Display for the refresh rate.  It should be around 60Hz in most cases.  Note also that cold LCDs are not as responsive.

---

### Post by Jive Turkey on 2010-01-04
If this [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01375248&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3674077]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01375248&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3674077") is your model you should definitely install the restricted driver.  The video problem is very likely to go away.

---

### Post by WadeH2o on 2010-01-04
I did confirm my refresh rate to be 60Hz.  I'm in the house at approx room temp. The specifics on my machine are HP dv6226us, the only pripority driver is for my wifi card which is in use. Keep the ideas coming. Thanks guys :)

---

### Post by WadeH2o on 2010-01-05
Anyone else have any ideas?

---

### Post by WadeH2o on 2010-01-08
**GREAT NEWS!!**

Today I made a USB startup disk to do a fresh install of 9.10. But one last step I did before restarting was to check for updates, low and behold a Kernel update was available. As image was installing it asked me again what I would like to do with menu.lst, this time I picked USE PREFERRED BY MAINTAINER. This update fixed the touchpad, the audio, and the delay on display!

Hurray for UBUNTU.
:D:D:D

EDIT: As an FYI I thought it would be a good idea to put the kernel version number that fixed the problem, just in case another user finds the same problems with the same machine.
```
wade@frog:~$ uname -r
2.6.31-17-generic

```

---

