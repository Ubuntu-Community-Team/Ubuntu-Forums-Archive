---
title: "Dual booting advice required"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by ontik on 2008-07-09
Hi All,

I've got a box with 2x500Gb SATA II drives.  I have Hardy installed on one and the other is yet to be formatted.  I'm wanting to install XP on the other drive which I figure I could just stick the CD in the drive, boot from it and install onto the unformatted drive.  Pretty straight forward.

But I don't know what will happen when I restart, will Grub automatically figure it out or will the PC crap itself and not know what to do?  I have zero experience with this so was hoping for some guidance before I dive in.

Can I please ask that if you offer instructions on the use or set up of grub, treat me like I'm a 3yo:oops:

Cheers,
ontiK.

---

### Post by logos34 on 2008-07-09
In order to install windows you will have to change the Bios hard disk boot order so the target drive is first, instead of linux.  Windows will put the bootloader on that drive, leaving grub on the other one untouched.

Once windows is installed and running fine, switch the Bios boot order back and boot ubuntu.

add a [windows boot entry like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") to the bottom of /boot/grub/menu.lst.

---

### Post by ontik on 2008-07-09
Thanks logos,  That's just what I was looking for. Thanks clicked.


ontiK.

---

