---
title: "Ubuntu 9.10 on USB, bootable but too big"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by rocklee on 2010-02-26
Hi folks,

I have managed to install Ubuntu on an 8GB USB flash drive using the usb creator, it boots up well no problem though it does seem to stop and idle a bit in the middle of the booting process.

I noticed that after installation I only have about 2GB of free space left, how much is Ubuntu chewing?!!!

I'd like to create a bootable Ubuntu system that doesn't take up that much space, and doesn't prompt me with liveCD stuff (ie. country, installation methods etc).

Is there an ISO for this?  I was thinking of Moblin remix.  I'd like the more basic Ubuntu configuration with the default device drivers to hook up to the internet, display and peripheral devices but not all the software if that would keep the size down.

Thanks!

---

### Post by wilee-nilee on 2010-02-26
The best way to use that Thumb is to do a full install, with the usb creator your only allowed about half the drive to use.

Use a Live Cd and install, use manual partition point it at the USB and make sure on the final screen to click advanced and make sure grub is pointed at the USB. Since it is on a USB a primary partition is okay you just wont have sleep.

---

### Post by C.S.Cameron on 2010-02-26
A full install takes a minimum of 2.3 GB and gets larger the more programs you install or download. A persistent install, (usb-creator, UNetbootin), takes about 700 MB plus what you select for persistence, The casper-rw file can be up to 4 GB.
Puppy and DSL are both small installs but not as slick as Ubuntu, there are a few other small ones worth investigating.

---

### Post by rocklee on 2010-03-01
Thanks guys, C.S.Cameron, what is a casper-rw file?

This is 4GB on my USB drive, is this something like a swap file?

I'm still unclear about persistent files.

---

### Post by C.S.Cameron on 2010-03-01
The casper-rw file is what some people call a loop file, (if I am not misunderstanding them). 
It stores all the stuff when you install or change things when you boot persistently. 
It can be found in the root directory of the flash drive. 
Usb-creator gives the option to make the install persistent, An UNetbootin install can be made persistent manually.

You can also make a partition labeled casper-rw that will do the same thing. 
You can even make a partition and label it home-rw if you want a separate home partition.
You don't need casper-rw if you do a full install.

---

