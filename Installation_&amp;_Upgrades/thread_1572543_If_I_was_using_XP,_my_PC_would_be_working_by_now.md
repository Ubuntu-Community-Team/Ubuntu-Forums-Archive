---
title: "If I was using XP, my PC would be working by now"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by rbrauns on 2010-09-11
Morning All,

Lsst year I tried Ubuntu 8.04 on my old P4 PC and it kept crashing (kernel crash) so I loaded XP on it.  Now I have a brand new HTPC with AMD 64 Athlon, 2TB HD and installed Ubuntu 10.4.

Like last year, I got the system 95% working and learned to use the terminal to get it perfect. Today, I've spent 4 hours already looking through the forums and editing files and still no wireless.  With Windows XP, I'd be surfing the web by now.  Before I install XP, I'm posting to the forum.

Issue is that the WUA-2430 external USB wlan stick is not working.

I installed ndiswrapper, installed the Vista 64 drivers and the device driver is loaded.  The command ndiswrapper -l produces this output:

All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in future versions agux64 installed.  Device (07d1:03a8) present.

Edited the /etc/modules/interface file and added auto wlan0, iface ... as per one of the posts. Added ndiswrapper to the kernel and did what the various posts instruct.

dmesg produces a pile of ndiswrapper errors followed by a few lines of "cannot find the frequency at ep 0x84".

Why is it so difficult to install a simple USB wireless stick and get Ubuntu to work with it? Can anyone help before I go back to XP?

Thanks, Rob

---

### Post by Simon_WM on 2010-09-11
Hi Rob,

Just woundering have you tired the Hardware Drivers Applications?

Under: System --> Administrator --> Hardware Driver

i hope this can help you wth your problem

---

### Post by rbrauns on 2010-09-11
Hi Simon,

Thank you for responding to my rant. Sorry for ranting but Ubuntu looks so good and yet it is not working. I went to system -> admin -> hardware and get this eror:
 Downloading package indexes failed, please check your network status.

I also just disabled the floppy in the BIOS because somehow that affects the USB.  BTW, the USB stick is connected to my Acer LCD which has a USB hub.  The webcam is on the same hub and it seems to be working. 

I'm going to try the older XP drivers for the USB stick to see if that makes a difference.

Cheers, Rob

---

### Post by efflandt on 2010-09-11
Normally if Ubuntu has a driver for your wireless that is not installed by default (proprietary) you would either need to temporarily connect wired ethernet, or insert install CD and add that CD to the repository (checkbox) of Synaptic, then go to System > Hardware Drivers and see if there is a driver for it that you could **activate**.

I have never had to use ndiswrapper, so cannot offer any suggestions for that.

---

### Post by Simon_WM on 2010-09-11
> **rbrauns said:**
> Hi Simon,

Thank you for responding to my rant. Sorry for ranting but Ubuntu looks so good and yet it is not working. I went to system -> admin -> hardware and get this eror:
 Downloading package indexes failed, please check your network status.

I also just disabled the floppy in the BIOS because somehow that affects the USB.  BTW, the USB stick is connected to my Acer LCD which has a USB hub.  The webcam is on the same hub and it seems to be working. 

I'm going to try the older XP drivers for the USB stick to see if that makes a difference.

Cheers, Rob

Hi Rob,

It sounds like, it could be a load error with your linux install...
what i've found in the past is that, if you burn the linux disk at 8X

it works better, as i've had the same problem but with the update manager

---

### Post by rbrauns on 2010-09-11
@Simon,

Thank you for taking the time to try to help me.
I think you may be onto something.  I burned Ubuntu 10.04 again to a CD but the slowest speed was 10X.  I installed it over the last version and recall seeing a lot of sector errors.  It ends with "will halt". I recall seeing those last time and rebooted.  Ubuntu started fine. I can't play a simple avi file, either so I'm going to scan the HD for errors.

Cheers, Rob

---

### Post by dmp2010 on 2010-10-18
You may also want to try to download from different machine. I had burned live cd using my home machine couple times but dint't work until I downloaded from different machine.

---

