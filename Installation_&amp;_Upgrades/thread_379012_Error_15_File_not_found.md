---
title: "Error 15: File not found"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Sturm on 2007-03-08
Well, I finally installed Ubuntu 6.10 (Edgy Eft) onto a spare PC.  It's an Intel 2.8GHz box with 2GB RAM, a 75GB IDE HDD and a 120GB SATA HDD.

I don't want to mess up the IDE drive, so I have told Ubuntu to install onto the SATA drive.  I also made sure to pick (hd1) as the place for GRUB to be installed, since I tried it earlier with (hd0) and it didn't get me anywhere except a "reboot and select proper boot device" error message.  At least with GRUB on (hd1), GRUB works.

However, it wants to automatically start into Ubuntu, but I get an error message:  "Error 15: File not found, Press any key to continue..."  If I do so, I am taken to the GRUB menu, I presume.  Still, I cannot choose any of the boot options there as I am always given either an "Error 15" or "Error 13" (for "Other operating systems") message.  What does this mean and how can I fix it? :confused:

---

### Post by Herman on 2007-03-08
Hello Sturm,
You should be able to boot up from [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") or else a [Super Grub Disk.]("http://supergrub.forjamari.linex.org/")
If you boot up from Grub's Command Line Interface, take note as you do so, because grub's CLI is interactive and gives good feedback which can be useful to you later. The same commands you need to boot from CLI mode will be needed to add to menu.lst to make booting automatic after that.
Once you boot into Ubuntu successfully, you can edit your /boot/grub/menu.lst file. 

If you need specific help with that, please post a copy of the bottom portion of the file and  copy of the output from 'sudo fdisk -lu here.
```
sudo gedit /boot/grub/menu.lst 
``````
sudo fdisk -lu
```A look at your /boot/grub/device.map might also be handy,
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#device.map"]**Editing Grub's device.map** (when you have SATA and IDE hard disk drives in the same machine, and Grub won't boot anything.
[/URL] ```
sudo gedit /boot/grub/device.map
```Regards, Herman :)

---

### Post by Sturm on 2007-03-08
Thank you, Herman!

Turns out, for some odd reason, my menu.lst file had a bunch of (hd1,0) as for the root, kernel, and initrd entries.  Using GRUB's CLI, however, I was able to find out that all three were actually on (hd0,0), so I booted into linux from the CLI, then modified the menu.lst entries to show (hd0,0) instead.  Hopefully, my future reboots won't return this error message anymore.  Thanks again!
:D

---

### Post by Herman on 2007-03-08
Well done Sturm, and thank you for the feedback, You were able to solve the problem yourself, that's very good. Most people would have still needed some help. 
Happy Ubuntuing,
Regards, Herman :)

---

### Post by Sturm on 2007-03-08
> **Herman said:**
> Well done Sturm, and thank you for the feedback, You were able to solve the problem yourself, that's very good. Most people would have still needed some help. 
Happy Ubuntuing,
Regards, Herman :)

Don't give me too much credit, now—I was about two minutes away from coming back here to say that your links weren't of much help.  Hehehe...  It did take a bit of trial-and-error for me to remember what the hard drive was called when I installed Ubuntu.  (I forgot that I put it on sda1, not hda1, for example).

---

### Post by richardjones on 2007-03-17
I've just got the same error after installing using the release 5 Kubuntu installer. When I select the "Ubuntu..." line from the grub menu, I get a screen just saying "Error 15: File not found".

My root / boot partition is on /dev/sdb3.

My menu.lst has "root (hd1,2)" and the device.map has "(hd1)  /dev/sdb". I think that means it should be looking at /dev/sdb3 ...

Ideas?

---

### Post by richardjones on 2007-03-17
I believe my problem is related to this bug report on grub: [https://launchpad.net/ubuntu/+source/grub-installer/+bug/33106](https://launchpad.net/ubuntu/+source/grub-installer/+bug/33106)

Indeed once I change the setting to use hd0 (which, according to device.map is actually /dev/sda) then the system boots.

---

