---
title: "Booting from USB"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-05-18
[BootFRomUSB]("https://help.ubuntu.com/community/BootFromUSB") describes a way to boot from a USB drive.

I was going to attempt tp implement this, but I noticed that it was necessary to extract the stage2_eltorito file from the GRUB source code.

I downloaded the Grub source code from the link given and could not find stage2_eltorito.
I did find start_eltorito.S.

How to proceed?

---

### Post by pebo on 2007-05-18
I had this problem - see [this]("http://ubuntuforums.org/showthread.php?t=237022") thread. In the end I found a copy in my SuSE installation.
I can send you a copy if you pm me.
BTW I never did get it to work...

---

### Post by Bablefish on 2007-05-18
If anyone has one I am sure the guy who runs [http://portableapps.com](http://portableapps.com) would gladly post it for download

---

### Post by Howard Kaikow on 2007-05-18
> **pebo said:**
> I had this problem - see [this]("http://ubuntuforums.org/showthread.php?t=237022") thread. In the end I found a copy in my SuSE installation.
I can send you a copy if you pm me.
BTW I never did get it to work...

I am going to try the approach in [putting /boot on a hard drive, leaving rst on USB drive.]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=21;t=5731;st=0;&#entry39924")

---

### Post by jerrylamos on 2007-05-18
Other approach is to put Grub on a diskette which boots to the USB.  There are some hints on [http://www.openbg.net/sto/os/xml/grub.html#fs_floppy](http://www.openbg.net/sto/os/xml/grub.html#fs_floppy)

Cheers, Jerry

---

