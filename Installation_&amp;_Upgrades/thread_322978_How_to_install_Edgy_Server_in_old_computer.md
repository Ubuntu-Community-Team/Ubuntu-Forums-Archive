---
title: "How to install Edgy Server in old computer"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by befused on 2006-12-21
I want to install The Edgy 386 server.  I have downloaded & burned it.    I have an Intel Marl motherboard that is too old (circa 1996) to support cdrom in bios.  I thought that tomsrtbt might provide the cdrom support that I need to install the server.   By copying a sample of of code to /etc/fstab, i was able to ls the cdrom.  I need to know how to autostart the cdrom, or some other method of moving the binaries to the hard drive

Thank you in advance,
Befused](*,)

---

### Post by az on 2006-12-21
> **befused said:**
> I want to install The Edgy 386 server.  I have downloaded & burned it.    I have an Intel Marl motherboard that is too old (circa 1996) to support cdrom in bios.  I thought that tomsrtbt might provide the cdrom support that I need to install the server.   By copying a sample of of code to /etc/fstab, i was able to ls the cdrom.  I need to know how to autostart the cdrom, or some other method of moving the binaries to the hard drive

Thank you in advance,
Befused](*,)

SBM or Smart Boot Manager is on the install disk - I think it's in the install folder.  You dd that to a floppy and then boot from it.  It should see your cdrom and allow you to boot from it.

Use the alternate cd, though, since the linux-server kernel will not work on anything less than  a 686.  If you have a pentium II or better, you are fine.

---

### Post by befused on 2006-12-21
I have a Ubuntu-6.10-alternate burned.  
SBM fails with an error code, continually and repeatedly,
is there some other method?
How do I instruct it NOT to install Xf86?

Thanks for the reply,
Befused

---

### Post by Sef on 2006-12-21
> SBM fails with an error code, continually and repeatedly,

What's the error code that you are getting?

---

### Post by treader on 2006-12-23
"Disk error! 0xAA" many times.

---

### Post by treader on 2006-12-23
I was thinking of compiling a new kernel, without gui, usb, and all the other stuff that this  motherboard predates.   What it MUST have is scsi, samba, and whatever it needs to present
a cdrom image to other linux systems.
  Why I am picking Edgy is the coding that it puts into /etc/fstab to uniquely identify each drive mounted--important when there are 21 five-disk Nakamichi cdrom scsi drives in this box.   The new method of user-space mounting is useless because it assigns the 105 disks at random, and I couldn't find any understandable description of taming it.
  This is the third iteration of trying to control this box.  The first was Win98, which ran out of drive letters before I ran out of disks.  Second was Dapper on a second motherboard, but that was a kludge, and too power hungry.  I am trying to use only the origional motherboard for it controls the power to the scsi system.

Yeah, maybe too much yap, yap, yap.

I am befused also but I keep forgetting passwords.

Thank you.
treader

---

