---
title: "kernel panic on reboot"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by dsmars on 2005-05-08
I'm trying to install umbuntu on a usb scsi portable drive which is connected to a toshiba laptop.  I get through the initial insatallation fine then on reboot I get this message:

starting umbuntu...pivot_root: no such file or directory
/sbin/init:428: cannot open dev/console: no such file
kernel panic - not syncing: attempted to kill init!

I saw elsewhere on the forums that someone had a similar message at the same point but he was installing on a mac g4.

all help and suggestions appreciated.  I'm still a bit of a noob when it comes to the inner workings of software.  If you wish you may email me at : [email]dsmars@cableone.net[/email]

thanks
DSMars

---

### Post by defkewl on 2005-05-08
I think you've got a mistake in your /boot/grub/menu.lst

Try getting in to linux with grub command line

---

### Post by dsmars on 2005-05-09
[QUOTE=defkewl]I think you've got a mistake in your /boot/grub/menu.lst

Try getting in to linux with grub command line[/QUOTE]


I looked around in there, but was afraid to change anything.  I think the GRUB thinks the umbuntu is on the main drive.  I am going to try changing the drive parameters.  Hopefully I won't screw it up even worse.  I'll let you know how it turns out.

---

### Post by dsmars on 2005-06-01
well, that didn't work.  ended up erasing and reinstalling the only working os on my system and lost al my data.  I'm such a noob.  Finally got rid of grub, but still don't have a working version of umbuntu.  will do more research and try to install it again without using that damn grub.

---

