---
title: "new install problem"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by davidillerj on 2005-05-11
I just downloaded the ubuntu linux software and installed it on my pc. I know nothing about linux "absolutely nothing" so i  installed the default setting. Everything seemed to have gone well. Got to the end of the installation and when it rebooted it got stuck on something called  starting hotplug subsystem... .

I am no programer or even close to it. so i really need some help. 
My machine is an INTEL CELERON D 2.40 GHz with 512 Ram and 40 GB hard drive.

I would appreciate any help given.

Thanks,
David

---

### Post by ringding on 2005-05-11
Hot Plug is: This package contains the scripts necessary for hotplug Linux support, and lets you plug in new devices and use them immediately. It includes support for PCI, Cardbus (PCMCIA), USB and Firewire devices and can automatically configure network interfaces.

I am wondering if you have any USB, Firewire, etc... devices not supported by Hot Plug or Ubuntu?????

Such as USB wireless adapter or Flash Drive, funky USB Mouse, etc...?

Just a thought?

---

### Post by davidillerj on 2005-05-11
I´ve got the common USB 2.0 connectors but nothing plugged in them. The only thing that might be conflicting in this case is the driver for the video card. It´s a RADEON 9000 with 128 MB RAM. The rest is just PS2 mouse and keyboard and an ethernet port and thats it. 

could it be the video card??? Should i plug it to the regular video port that the mother baord has???

Thanks.
D

---

### Post by ringding on 2005-05-11
Not sure if HotPlug has anything to do with video devices ...more to do with USB, PCMCIA, Firewire devices....but....

Is the on-board video disabled in the bios?   If not....this might cause the system to hang.

---

### Post by ringding on 2005-05-11
looks like your ATI 9000 card is supported..  [Check Here](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)

---

