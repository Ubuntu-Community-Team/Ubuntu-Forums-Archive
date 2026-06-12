---
title: "How to wipe MBR on an external HD?"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by ycason on 2007-11-09
I need to completely erase the MBR of an external HD....  Remnant of a Kubuntu install.

Grub is installed on there right now, so if I boot with the HD plugged in I just get a grub error screen.

---

### Post by logos34 on 2007-11-09
[dd if=/dev/zero of=/dev/sda bs=446 count=1]("http://www.tuxation.com/mbr-tricks-with-linux.html")

or maybe your external drive is sdb

---

### Post by buccaneere on 2007-11-12
> **logos34 said:**
> [dd if=/dev/zero of=/dev/sda bs=446 count=1]("http://www.tuxation.com/mbr-tricks-with-linux.html")

or maybe your external drive is sdb

What will this entire code entry be for a external (USB-connected) HDD (sdb) ???

Thanks

---

### Post by logos34 on 2007-11-12
> **buccaneere said:**
> What will this entire code entry be for a external (USB-connected) HDD (sdb) ???

dd if=/dev/zero of=/dev/sdb bs=446 count=1

basically same command, doesn't matter whether it's internal or external drive

---

### Post by buccaneere on 2007-11-12
> **logos34 said:**
> dd if=/dev/zero of=/dev/sdb bs=446 count=1

basically same command, doesn't matter whether it's internal or external drive

Thanks log...

I'm not understandin' the part about not matterin' tho', about internal vs external. I wanna clean the external drive, not the local drive.

What part of the code designates the external drive?

---

### Post by buccaneere on 2007-11-13
> **buccaneere said:**
> Thanks log...

I'm not understandin' the part about not matterin' tho', about internal vs external. I wanna clean the external drive, not the local drive.

What part of the code designates the external drive?

bumpintodatop...

---

### Post by logos34 on 2007-11-13
if sdb is your usb external drive, as fdisk sees it

sudo fdisk -l

then that is your output file, i.e.  'of=/dev/...'

dd if=/dev/zero of=/dev/sd**b** bs=446 count=1

it will erase the first 446 bytes of info (the mbr) on whatever disk you designate as the target...

---

### Post by ycason on 2007-11-27
Thanks for the help!  My external drive no longer hijacks my grub when it's plugged in!

---

