---
title: "Prevent grub installation on hda?"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by JimJones56 on 2006-03-04
Hi there. This is my first ubuntu installation and I've got a quick question before I begin:

I realise that ubuntu is newbie-friendly but is there a way to prevent grub (or similar) from being installed on the primary drive?

I've got an XP NTFS drive as my primary drive and I don't want to touch it! I was hoping to install ubuntu to hdb and use *bootpart *to add Linux to the NT boot loader. But, of course, this requires that grub isn't installed to hda but rather to hdb1. I know I can do this with Fedora but is this possible with ubuntu?

Thanks in advance

---

### Post by taurus on 2006-03-04
But of course.  Just point it to wherever you want GRUB to reside when you get to that screen.  You can also have GRUB boot from a floppy disk if you wish...

---

### Post by Ocxic on 2006-03-05
when the installer askes to install GRUB on your first hard drive, say no and type /dev/hdb as your choice. or you could even install onto a floppy disk and use that to boot so you don't have to fiddle with the windows boot loader.

---

### Post by cotcot on 2006-03-05
If you point to the floppy (/dev/fd0) do not formget to make the windows partition active again (fdisk).

---

### Post by JimJones56 on 2006-03-05
Great stuff, thanks guys. I wasn't sure that Ubuntu would give me any grub options since it's supposed to be utra-newb-friendly. Installation went perfectly, thanks again.

Floppy disk? FLOPPY DISK? What is this, like 1981?! :-P

---

