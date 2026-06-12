---
title: "[SOLVED] Intel DP965LT Installation Issues"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by cprofitt on 2007-07-18
I have searched the forums and not found anyone having a problem that sounded similar to mine.

I have:
[LIST]
[*]Intel BOXDP965LTCK LGA 775 Intel P965 Express ATX Intel Motherboard - Retail
[*]2gb of ram (per Intel specs), Mushkin DDR 800
[*]2 ST3250620AS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive
[*]Samsung 18X DVD SH-S182M/BEBM
[*]EVGA 320-P2-N811-AR GeForce 8800GTS 320MB GDDR3 PCI Express x16 HDCP Video Card
[/LIST]

I had to hit F6 on the liveCD and remove the quiet-splash and replace it with break=bottom. When it got me to a  prompt I had to:

chroot /root nano /etc/X11/xorg.conf

edit out the NV driver with vesa

cntl+o - hit enter to save
cntl+x

type exit at the command prompt.

The Live CD then booted fine and I proceeded with the install - which completed and asked me to restart.

Upon reboot the system comes up and I see the Grub menu, immediately after it goes to a black screen and the monitor states that there is no signal. At this point there is also no HD activity.

I will be trying the alternate CD, but suspect that will not resolve the issues.

I have tried both the AHCI and IDE setting in bios for the SATA controllers.

I have been able to load both Windows XP and Windows Vista with no issues.

If anyone has any suggestions that might assist me when I try once again after work please let me know.

---

### Post by Pumalite on 2007-07-18
See all this:

[http://kerneltrap.org/node/7020](http://kerneltrap.org/node/7020)

[http://kerneltrap.org/node/7077](http://kerneltrap.org/node/7077)

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

[http://www.linuxquestions.org/questions/showthread.php?t=569682](http://www.linuxquestions.org/questions/showthread.php?t=569682)

[http://www.desktoplinux.com/news/NS6838631144.html](http://www.desktoplinux.com/news/NS6838631144.html)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61342](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61342)

Good luck.

---

### Post by cprofitt on 2007-07-18
What Kernel is in Feisty?

From what I can tell -- all those articles deal with not being able to have the CD drive recognized during an install -- my install runs and completes, but on reboot of the machine -- to run the actual install I get the grub menu and then a quick flash of one line of text -- then a black screen. I have not been able to read that one line as it goes away so fast.

As a side note if I ask it to boot into recovery mode it boots just fine -- hope that moves the discussion along as to resolving the issue.

---

### Post by Pumalite on 2007-07-18
Sorry, I missed that. Do you have a Raid array?

---

### Post by cprofitt on 2007-07-18
> **Pumalite said:**
> Sorry, I missed that. Do you have a Raid array?

Nope, no raid array -- just using the on-board SATA controllers.

I am curious if this might be a grub.conf issue. Perhaps the splash screen is an issue with the frame buffer -- found some stuff talking about this on google, but have not yet found any details on editing the grub.conf.

---

### Post by cprofitt on 2007-07-18
I changed my grub menu.lst

from:

> 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f0a01578-d1e4-44bd-835f-f58ea47f81b3 ro quiet splash


to

> 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f0a01578-d1e4-44bd-835f-f58ea47f81b3 ro quiet


I am now booting... what would cause that...?

---

### Post by rbmorse on 2007-07-18
The "splash" you removed is a graphic file of a specific type at a specific location that displays while the system gathers itself as the O/S loads.  Yours may be missing or corrupt.  Removing "splash" from the boot line means GRUB won't look for it/try to load it. 

GRUB is unfortunatley brain dead, even by geekware standards. This particular error ought to have a handler

RBM

---

### Post by cprofitt on 2007-07-18
> **rbmorse said:**
> The "splash" you removed is a graphic file of a specific type at a specific location that displays while the system gathers itself as the O/S loads.  Yours may be missing or corrupt.  Removing "splash" from the boot line means GRUB won't look for it/try to load it. 

GRUB is unfortunatley brain dead, even by geekware standards. This particular error ought to have a handler

RBM

Is there anyway to verify or replace the splash screen? I have seen some topics on specifying a splashimage, but was not sure if they applied to the Grub included with Ubuntu.

---

### Post by Pumalite on 2007-07-18
Why don't you check your menu.lst against: code: ls -l /dev/disk/by-UUID, to be sure?

---

### Post by cprofitt on 2007-07-18
> **Pumalite said:**
> Why don't you check your menu.lst against: code: ls -l /dev/disk/by-UUID, to be sure?

Already did that... the uuid is accurate. Everything boots just fine if I remove the splash option... just not sure why that works.

---

