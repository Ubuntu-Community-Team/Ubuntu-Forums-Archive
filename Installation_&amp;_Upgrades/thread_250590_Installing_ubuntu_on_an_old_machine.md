---
title: "Installing ubuntu on an old machine"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by dapissarenko on 2006-09-04
Hello!

I have a computer without access to internet (it can be connected to a LAN and has a floppy disk drive) and want to install

a) ubuntu 6 and
b) GNU Cash

on it.

I have several questions:

1) How can I install ubuntu 6 on that machine, if 

a) it doesn't have a built-in CD-ROM reader and 
b) can't boot from an external CD-ROM reader ?

2) Where can I download the files, necessary to install GNU Cash (and other applications for ubuntu) on a machine without internet?

TIA

Dmitri Pissarenko

---

### Post by motin on 2006-09-04
I do not know how to install Ubuntu without a CD-ROM-reader, but I know that it is perfectly possible to install Linux without it if your computer can be connected to a LAN and boot via PXE or a floppy drive. With the floppy drive you could probably as well boot with a floppy that installs the necessary drivers for your external CD-ROM reader. 

My suggestion would be to install VMWare Server, which is free of charge, and install Ubuntu in a virtual computer there inside, although this will have a significant decrease in performance, especially if your computer has a couple of years history. Still, if no other options remain... (This was the way that I tried out GNUCash before I had Ubuntu as first choice OS)

---

### Post by the100thmonkey on 2006-09-04
if it's a low-end machine, you might also want to consider installing Xubuntu instead of vanilla Ubuntu - it's aimed much more at low end machines, using XFCE in place of GNOME - i got my laptop looking rather pretty with it.

---

### Post by dapissarenko on 2006-09-04
Hi!

Thanks for your answer!

> **motin said:**
> I know that it is perfectly possible to install Linux without it if your computer can be connected to a LAN and boot via PXE or a floppy drive.

And how does a PXE-based installation work?

Thanks in advance

Dmitri Pissarenko

---

### Post by dapissarenko on 2006-09-04
Thanks for your answer!

> **the100thmonkey said:**
> if it's a low-end machine, you might also want to consider installing Xubuntu instead of vanilla Ubuntu

GNU Cash works fine on the machine: Long time ago I installed Xandros Desktop on it and used several apps (TeXMacs, GNU Cash, OpenOffice) with sufficient performance.

Best regards

Dmitri

---

### Post by motin on 2006-09-04
> **dapissarenko said:**
> Hi!

Thanks for your answer!



And how does a PXE-based installation work?

Thanks in advance

Dmitri Pissarenko

You must come to meet the power of Google: [http://www.google.se/search?q=install+ubuntu+pxe](http://www.google.se/search?q=install+ubuntu+pxe) first hit for example: "Installing Ubuntu via PXE network boot is the way to go if you have no cd-r at hand or if you have no cdrom at all." - [http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

Edit: This one looks simpler to follow: [https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall](https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall)

---

### Post by dapissarenko on 2006-09-04
Thanks!

---

### Post by dapissarenko on 2006-09-04
Hello!

I've read the materials on PXE.

Before I do that I want to ensure that PXE is really the only option.

On the target machine I have a running Xandros Desktop 2.0 (linux), which works properly and can read/write to the external CD drive.

Can I use this existing linux to install ubuntu without PXE?

That is, can I do this:

1) First I boot (already installed) Xandros the machine from the hard disk.

2) From Xandros I access the external CD drive.

3) I launch the ubuntu installer.

4) Ubuntu is installed on the hard disk (Xandros and Windows on the hard disk are eliminated).

5) Ubuntu boots from the hard disk.

Is this possible?

TIA

Dmitri

---

