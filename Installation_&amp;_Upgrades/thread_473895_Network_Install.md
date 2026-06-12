---
title: "Network Install"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Kilo1 on 2007-06-14
I see that Ubuntu can be installed over a network, but don't see documentation on how to do this.  I have an old laptop that does not have a CD.  It does have a floppy and a PCMCIA slot.  I'd like to install Ubuntu by booting (from a floppy maybe?) and accessing the install CD from a shared drive on the network.  I have an old version of RedHat that has that install option.  Can Ubuntu do this?

---

### Post by Pumalite on 2007-06-14
> **Kilo1 said:**
> I see that Ubuntu can be installed over a network, but don't see documentation on how to do this.  I have an old laptop that does not have a CD.  It does have a floppy and a PCMCIA slot.  I'd like to install Ubuntu by booting (from a floppy maybe?) and accessing the install CD from a shared drive on the network.  I have an old version of RedHat that has that install option.  Can Ubuntu do this?

I can tell you the way I do it in my home LAN. Install Konqueror, bring it up ( you'll find it under Applications>Internet>Konqueror. At the command line ( where you usually put the URL ) type 'fish://<username>@IP'. This means you have to know the username and the IP and the password of the box you are connecting to. I you have firewalls, you have to enable port 22. You can then access anything you want in the other box.

---

### Post by Kilo1 on 2007-06-14
> **Pumalite said:**
> I can tell you the way I do it in my home LAN. Install Konqueror, bring it up ( you'll find it under Applications>Internet>Konqueror. At the command line ( where you usually put the URL ) type 'fish://<username>@IP'. This means you have to know the username and the IP and the password of the box you are connecting to. I you have firewalls, you have to enable port 22. You can then access anything you want in the other box.

Install Konqueror?  The laptop I am installing to has nothing on it.  No OS.  The box I am accessing that contains the install CD is an XP machine with the CD drive shared.

So to summerize:

Box 1: No OS, Floppy, PCMCIA slot with a NIC card.
Box 2: XP, Ubuntu CD in shared drive.

I want to install Ubuntu to Box 1 off the share on Box 2.

---

### Post by Gagle on 2007-06-14
You can try a Network install if your BIOS is PXE boot capable.  Althought I only tried with Ubuntu 6.10 , it may be possible to install newer version using this method.  Is it a bit of hassle to set up the other computer that will serve as a "server" (it's not server but I don't recall the exact term).

Here is a good start : [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)
And : [http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

(Sorry for the Blog Spam....)

Also, go check out the VectorLinux homepage.  This lightweight distro has nice alternative install methods.

Hope it Helps,

Gagle

---

