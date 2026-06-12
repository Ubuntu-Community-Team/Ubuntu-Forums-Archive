---
title: "No USB in ubuntu-19.10-preinstalled-server-arm64+raspi3.img.xz with Raspberry Pi 4"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by keyboarderror2 on 2019-10-17
I'm not able to get keyboard or mouse access or any USB at all on a Raspberry Pi 4 as far as I can tell. I can't investigate. The 32 bit ubuntu-19.10-preinstalled-server-armhf+raspi3.img.xz works ok, but I need 64 bit for some things. Please fix!

---

### Post by davis-a on 2019-10-18
Can confirm same issue on pi 4.  

Initially I thought it was not accepting keyboard input.  After seeing this post I plugged in a few usb sticks and none show up when using $lsblk

---

### Post by Kradenko on 2019-10-18
Hi,

Same problem here. Raspberry Pi 4 - 4GB. No keyboards response at first boot.

---

### Post by johnsarge on 2019-10-18
Same issue. Was so excited too...

---

### Post by icolumbro on 2019-10-18
Same problem here with 64 bit image. Raspberry Pi 4 (4 GB), I can connect via SSH but I can't use USB keyboard and mouse...

---

### Post by alexander-agnarson on 2019-10-18
Same issue here. No keyboard or mouse working with 64bit 19.10. Using a Raspberry Pi 4 (4GB).

---

### Post by uRock on 2019-10-18
Has anyone filed a bug report? [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by uRock on 2019-10-18
There's a bug report here. Jump in, look at it, and click affects me at the top. [https://bugs.launchpad.net/ubuntu/+bug/1848703](https://bugs.launchpad.net/ubuntu/+bug/1848703)

---

### Post by uRock on 2019-10-18
Does anyone know what package handles this so we can get the bugs assigned to it?

---

### Post by alexander-agnarson on 2019-10-18
> **uRock said:**
> There's a bug report here. Jump in, look at it, and click effects me at the top. [https://bugs.launchpad.net/ubuntu/+bug/1848703](https://bugs.launchpad.net/ubuntu/+bug/1848703)

Done. Thanks for the link.

---

### Post by deadflowr on 2019-10-18
[s]Here's an on-going thread over at snapcraft:
[https://forum.snapcraft.io/t/support-for-raspberry-pi-4/11970/14]("https://forum.snapcraft.io/t/support-for-raspberry-pi-4/11970/14")[/s]

Nevermind this isn't about the core images.

---

### Post by uRock on 2019-10-18
> **alexander-agnarson said:**
> Done. Thanks for the link.

Anytime! Hopefully the package it is pertaining to gets added to the report so they can get it fixed.

---

### Post by davis-a on 2019-10-18
> **uRock said:**
> Anytime! Hopefully the package it is pertaining to gets added to the report so they can get it fixed.

I filed the bug, but I'm not sure which package to flag it against.  Should I flag it against the kernel package?

---

### Post by alexander-agnarson on 2019-10-19
> **davis-a said:**
> I filed the bug, but I'm not sure which package to flag it against.  Should I flag it against the kernel package?

Another report here, under linux-raspi2 (Ubuntu): [https://bugs.launchpad.net/ubuntu/+source/linux-raspi2/+bug/1848790](https://bugs.launchpad.net/ubuntu/+source/linux-raspi2/+bug/1848790)

---

### Post by uRock on 2019-10-19
> **davis-a said:**
> I filed the bug, but I'm not sure which package to flag it against.  Should I flag it against the kernel package?

> **alexander-agnarson said:**
> Another report here, under linux-raspi2 (Ubuntu): [https://bugs.launchpad.net/ubuntu/+source/linux-raspi2/+bug/1848790](https://bugs.launchpad.net/ubuntu/+source/linux-raspi2/+bug/1848790)

Thanks both! The assignee on the one alexandar-agnarson linked has reproduced the issue, so I am hopeful they'll get it knocked out.

---

### Post by khowe on 2019-10-19
User on lingon on raspberry pi forum posted the following:

The USB-problem concerning the Raspberry Pi 4GB RAM model might be due to the issue seen earlier that using more RAM than 3072 MB breaks the USB:
[https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=246766&start=25](https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=246766&start=25)

The issue was solved by a kernel patch:
[https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=246766&start=50#p1517839](https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=246766&start=50#p1517839)

and the kernel patch was this one:
[https://github.com/raspberrypi/linux/issues/3093#issuecomment-520269280](https://github.com/raspberrypi/linux/issues/3093#issuecomment-520269280)

---

### Post by khowe on 2019-10-20
Work around until kernel is patched:

Setting total_mem=3072 in /boot/firmware/usercfg.txt 
If you mount the sd card in another computer the usercfg.txt is on the small vfat partition.

---

### Post by baqwas on 2019-11-09
As a newbie, may I ask if it is practical to have a naming convention for the image that specifies "minor" release changes too? Right now, I am aware of the issues with the 4 GB model and USB for the image. I also understand that the these have been fixed and patches tested by the user(s) who reported the issues originally.

When can we expect the image to be refreshed?

Kind regards.

---

