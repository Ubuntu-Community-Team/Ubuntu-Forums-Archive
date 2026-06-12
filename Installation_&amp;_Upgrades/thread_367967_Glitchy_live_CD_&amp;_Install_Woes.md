---
title: "Glitchy live CD? &amp; Install Woes"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by digm on 2007-02-22
I was a bit of linux geek in college, and caught some Ubuntu vids on digg recently and decided to check it out.  Sadly, those days are long gone and it's amazing how much I've forgotten.  Anyway, I'm having a heck of a time getting Edgy to install and hope someone can help.

I had a functioning XP install, and decided to install Ubunto on a second drive I had laying around. I'll give a short recap of the events of last night through now:

There are three relevant drives: 

1.  80 gig sata (xp install)
2.  250gig external sata2 connected via usb (backup)
3.  60 gig IDE (ubuntu)

- Booted live CD, all drives recognized, partitioned appropriate drive and installed.  
- On reboot, XP loaded, and I figured grub had not been sucessfully installed
- Rebooted through live CD, and tried to force a grub install.  No dice.
- Rebooted, repartitioned drive, reinstalled.
- On reboot, Ubuntu finally loads.  Re-force grub.
- Grub screen on reboot.  Can't boot into XP.  Boot into Ubuntu and scan through menu.lst - everything seems to check out.  fdisk only shows my ide drive. Go to sleep annoyed.
- Boot with windows cd and use fixmbr to get back into xp and make sure everything is safe.  It is.
- Reboot into Live CD.  All drives recognized.  I try reinstalling again.
- On reboot, xp loads.
- Reboot final time into live cd, and fdisk outputs:

> ubuntu@ubuntu:~/ubuntu$ sudo fdisk -l

Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         523     4200966   83  Linux
/dev/hdc2             524         787     2120580   82  Linux swap / Solaris
/dev/hdc3             788        7476    53729392+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

I have no idea where the 80gig XP disk went, nor why the usb drive is flagged bootable.

Anyone have any guidance how to troubleshoot this one?  I used gentoo back then, and even though the install was a pig, I don't remember it being this aggrivating. It's one thing to have something not work, it's another to have it work randomly ;p

---

### Post by princemackenzie on 2007-02-22
Weirdly, I have a very similar situation and trying to figure it out as we speak.

It seems as if Ubuntu, (or GRUB) doesn't like to be on an IDE drive while another OS sits on a SATA drive.  I'd love to hear any answers.

---

### Post by digm on 2007-02-22
On a fluke, I just changed the boot sequence in the bios to use the ide first, and got grub.

Getting an Error 25 when I try to boot xp, Ubuntu boots fine and the sata drive is still nowhere to be found in fdisk..

I'm not sure if that's better or worse ;p

---

