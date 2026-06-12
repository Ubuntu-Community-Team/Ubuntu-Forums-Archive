---
title: "Persistent USB installation"
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-05-15
-----SOLVED------

I was just wondering if any of you use a persistent USB installation for testing the unstable Ubuntu versions.

I'll probably prepare one once I get out of bed in the morning.

---

### Post by Gina on 2009-05-16
There's only the Alternate version available in Alpha 1 so you can't run off the USB stick - only install to HD. They say the Desktop (Live CD) version won't be available until Alpha 2.  (I don't know what the Server version does)

---

### Post by awam66 on 2009-05-16
> **excogitation said:**
> I was just wondering if any of you use a persistent USB installation for testing the unstable Ubuntu versions.

I'll probably prepare one once I get out of bed in the morning.

Yes I have another installation on a USB hard drive which I use to test new versions. Usually wait til alpha 3 or 4 though. At the moment running 9.04 xubuntu on it just for fun.

The alternative CD should let you install on such a device. Don't know about USB sticks though.

---

### Post by excogitation on 2009-05-16
The alternate install CD is exactly what you want (for a persistent, not the live install), Gina.

So I installed Karmic to a 8GB USB stick.
(just make sure to chose the right device and also install the bootloader on the USB stick, not your first hdd (and set your bios to boot from it))

The only problem I noticed - when partitioning the USB stick the installer tries to use the swap partition of the hdd and if you tell it not to use it - it wants to write the changes to that hdd's boot sector ... luckily I somehow managed to get around that.

As to using the Alpha 1 ... my input devices (mouse, touchpad, keyboard) don't work, so I can't test it.

---

### Post by jfernyhough on 2009-05-17
Meh, I'm running Karmic on my laptop and have a Jaunty install on a USB HDD as backup (actually, I have it on two). :D

If you want, install using a Jaunty LiveCD - just change the install location, make sure the bootloader is installed to the USB drive, and afterwards delete any references to internal swap devices in /etc/fstab . Then edit /etc/apt/sources.list and change all jaunty to karmic, aptitude update, aptitude full-upgrade, you're running Karmic. ;)

---

### Post by Reiger on 2009-05-17
No the only Linux distro I have on USB is called PuppyLinux which I used to replace an XP install for someone who saw it thoroughly broken when the USER32.dll file was removed by the anti virus [AVG, mistaken definitions, schedule AV checks and little computer savvy].

---

### Post by Taiebot65 on 2009-05-17
There is a really good software on the french forum which will give you the possibilty to create a live-usb persistent  and do some upgrades 
they have started to do translation so maybe english is available now..

[http://forum.ubuntu-fr.org/viewtopic.php?id=276821]("http://forum.ubuntu-fr.org/viewtopic.php?id=276821")

You can not update your live usb from the update manager but directly from the software...

Edit it s a script

---

