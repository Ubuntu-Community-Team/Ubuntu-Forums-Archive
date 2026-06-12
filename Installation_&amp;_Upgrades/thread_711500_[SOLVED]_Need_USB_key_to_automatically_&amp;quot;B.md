---
title: "[SOLVED] Need USB key to automatically &amp;quot;Boot from first Hard Disk&amp;quot;"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by jmikola on 2008-02-29
I recently upgraded my desktop with new hardware and decided to turn my old hardware into a storage server.  This storage server is now running with a 2.5-year-old DFI Lanparty nf4 Ultra-D motherboard (AMD 939) and a 3ware 9650SE RAID card connected to a bunch of drives (I'm not using the motherboard's IDE/SATA ports at all).  The RAID card is configured to provide me a carved 20gb volume and a second volume with the remaining space (much larger ^_^).

Much to my chagrin, it appears that the nforce4 motherboard simply cannot boot off of the RAID card on its own (despite the fact that I can select it as the primary boot device).  Oddly enough, however, if I boot off of the Ubuntu 7.10 alternative install CD and select "Boot from first hard disk", the system boots from the 20gb volume on the RAID card just fine.

I realize the underlying problem is an incompatibility between the nforce4 motherboard and RAID card, but I'd rather recycle old parts than throw unnecessary money at the problem by purchasing a server-class motherboard.

What I'd like to do is format a USB key to automatically execute whatever the Ubuntu install CD does when I select "Boot from first hard disk".  This way, I can set my BIOS to boot off the USB key all the time and 

I'm not sure if simply putting GRUB on a USB key will accomplish this, since I believe that would likely require the kernel be stored on the USB key itself (please correct me if I'm wrong).  If i'm not mistaken, the "Boot from first hard disk" command on the Ubuntu install CD operates at a lower level than grub, since it apparently ends up executing the GRUB bootloader stored on the first hard disk.

Is anyone familiar enough with Ubuntu install CD (or this method of booting in general) enough to provide some insight?

---

### Post by Herman on 2008-02-29
Grub, and Linux, are both very flexible and you can configure almost anything if you try.
For example, it would be quite possible to have a Linux Kernel in a device, and the / (root) file system in another device and boot them from GRUB in some other completely different device. 

If you want to try this, [How to add GRUB to your USB thumb drive]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive."), you can make your own GRUB in a USB drive and edit it yourself to do whatever you like.
You might need to experiment with [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") a little to see which hard disk your BIOS andGRUB 'sees' as number 1 when the USB stick is present in your system. It may turn out the your BIOS will give the USB drive first place, and you'll need to set GRUB to boot your internal hard drive as the second hard drive (hd1).

Another idea is just to download [Super Grub Disk]("http://sgd.benjamin-butschko.de/?section=download#usb") for USB and use that. It's up to you if you want to use it as it is or edit one of the GRUB menus in that to boot your first hard disk. adrain15, the developer of Super Grub Disk has added some special patches to Super Grub Disk for USB so it will get the hard drive numbers right.
If you take a look here in this how-to, [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it]("http://ubuntuforums.org/showthread.php?t=575406") you will see in the an example of how I edited the /boot/grub/menu.lst file in Super Grub Disk for USB to do exactly what it is you are talking about. Due to adrain15's patches, you just edit the menu in a staightforward manner, your first hard disk should be (hd0) to Super Grub Disk.
```
 title       Boot the First Hard Disk
root       (hd0)
chainloader +1
```

Regards, Herman :)

---

### Post by jmikola on 2008-03-01
Thanks Herman, this looks perfect.  I was unaware of the chainloader command in grub, but I just read up on it a bit and it's exactly the functionality that I was looking for. :)

---

