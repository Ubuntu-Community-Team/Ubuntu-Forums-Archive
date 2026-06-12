---
title: "Installation and Grub"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by pauljb on 2007-04-03
Hello,

I been having a few problems and need some help. I myself am a newish to linux, and have switched to ubuntu and havent looked back. My friend recently said he was feed up with windows and wants linux, so naturally i said easy and came over to his house with ubuntu cd and was like give me 30min and i will have it installed. BUT things didnt work.

His system is a 3ghz pentium 4, 120gb ide HD (windows XP on here) and 250gb sata HD! (just storage drive) and wireless internet connection.

Firstly the partition wouldnt work, came up with errors, but got it sorted. Set up with 100 gb for windows now, and then 17gb for "/" of linux and 2gb for swap, these linux parts where on logical partition. Went on with installion and restart, and NO GRUB!

The odd thing is it detects the two hard drives as sdb1 and sdb2, on my linux which has two ide they are hda1 and hdb. I think it has something to do with the grub bit - it was hd0.

Well it installs just grub not working.

Also wireless not working either.

I felt so bad after i told him ubuntu and linux was so good, so come on i need to get my friend on the linux side again.if

---

### Post by Minn3h on 2007-04-03
Figure out which is the boot drive in the bios.  Boot to an ubuntu live cd, figure out which hard drive is the one the bios is booting to (/dev/hda1 for example), this is where the mbr is.

Then do:
(sudo) mkdir /mnt/temp
(sudo) mount /dev/hdx (or sdx, this is the linux partition, not necesarily the boot drive) /mnt/temp
(sudo) grub-install /dev/hdx (or sdx, this is the boot drive) –root-directory=/mnt/temp

---

### Post by pauljb on 2007-04-04
well am pretty sure it was sdb2 that is the main windows drive, so i use this one then?

Also what about my friends wireless. He has a wireless router which is connection to computer using a usb wireless connector. ubuntu doesnt detect this, it doesnt even light up, doesnt detect any wireless at all. What do i do?

Cheers
Paul

---

### Post by Minn3h on 2007-04-04
The easiest way to figure out which drive it is, is literally to open the bios, check out which hard drive it's booting to.  Then in linux do fdisk -l and find the disk that's the same size.

As for the wireless, I've never set up wireless in Ubuntu before, always plugged in my box, so I probably can't be of much help.  What I would do though, is include a little more information, especially the make and model of this usb wireless device.  Searching these forums for that information will almost certainly find you other people that have configured the same device.

---

