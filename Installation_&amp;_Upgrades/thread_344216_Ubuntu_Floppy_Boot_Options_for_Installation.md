---
title: "Ubuntu Floppy Boot Options for Installation"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by guyver on 2007-01-22
The reason why I'm wanting to see if I can do a floppy boot in order to do a Ubuntu Installation is because I'm trying to install Ubuntu on my GF's notebook and it has the following limitations:

1.  CD-ROM drive that came with laptop no longer works.

2.  Although there is an external USB CD-ROM drive available, the laptop's BIOS does not support booting from a USB storage device.

A floppy boot (hopefully identifying the prescence of the external CD drive) seems to be the only way for me to go, but I do not know if this has been done before or explained.

---

### Post by logos34 on 2007-01-22
You can try [this]("https://help.ubuntu.com/community/BootFromUSB"), but if your lappy bios can't even detect a usb cd drive then i'm not sure it'll work.

---

### Post by guyver on 2007-01-22
Unfortunately that is not an option.  Otherwise, I'd be able to use the external USB CD-ROM drive.

Another possibility may be to install via an ethernet jack, but it would have to start from a floppy.

---

### Post by guyver on 2007-01-22
I forgot to mention that I want to totally repartition and format the HDD, so I would rather do this from a boot... the system is currently set up with Win2K & XP.

---

### Post by logos34 on 2007-01-22
How about this?
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by guyver on 2007-01-22
I just glossed over it... I will see if there is a floppy boot from one of these options.  Thanks.

---

### Post by logos34 on 2007-01-22
here's another
[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

---

### Post by guyver on 2007-01-22
Bingo!  Thanks... I'll have to figure out how to do the "debootstrap".   This looks like a winner.  

Very much appreciated.

---

