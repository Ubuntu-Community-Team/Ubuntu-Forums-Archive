---
title: "Linux PXE winpe boot"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by tipalm73 on 2007-07-17
Hello,

I am trying to set up a pxe on a linux machine to install winpe on clients.

Having read a few tutorials I have a question. First, I'd love any other links to read how to do this.Now my question, one of the tutorials used samba to access the files for the winpe boot, can I just copy the files that winpe creates into the pxe folder on the linux box?

I basically have a winpe setup on a disk, I have 6 machines(with no cdrom) per rack and as it is now someone takes a usb-cdrom and installs to each machine individually. I proposed a PXE setup to do the 6 machines at once, but they need to put winpe on it.

Thanks in advance!

Tipalm

---

### Post by tipalm73 on 2007-07-17
Well I figured out why you use samba =] It's to provide a "familiar" environment for the client machine that will run WinPE.

I proposed to do it on a deb server, but they'd prefer a IIS setup with RIS. I think its dumb.. the RIS basically needs Active Directory(always a work-around)... and of course a WS2003 license is not free =]

Any references would still be appreciated.

---

### Post by D8TA on 2008-02-05
Did you ever figure this out? I am also trying to PXE boot WinPE using Xubuntu and can't get it to work.

---

