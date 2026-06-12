---
title: "Install from USB stick"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by VinzC on 2008-11-15
Hi.

I've just wanted to install Ubuntu 8.10 from a USB stick onto a Dell Latitude D420 laptop that has *no* cdrom. So I've mounted an iso **alternate** image (I need LVM) onto my Gentoo laptop, copied everything to a partition on my pen, run syslinux to make the pen bootable.

The pen boots fine with a Ubuntu text menu and the install process starts. However the install stops after the hardware detection step, telling me the CD cannot be used for the installation :confused:!

What do I need to change to make it recognize my USB stick properly?

EDIT: Let me add that I can't do a network install either since neither the Intel Pro/Wireless 3945 neither the Broadcom Gigabit Ethernet interface have a driver on Ubuntu install CDs I tried. BTW I have just tried installing Ubuntu from Windows using Unetbootin but the "alternate" version of the ISO image I used is started in network-mode install, i.e. the USB key is installed and boots but wants to setup the network, which can *NOT* be done so far!

Hence I need a network-less *and* CDROM-less install.

Thanks in advance for any suggestion.

---

### Post by VinzC on 2008-11-16
Is it possible at all or should I give up?

---

### Post by C.S.Cameron on 2008-11-16
Use Unetbootin to install the full Ubuntu iso.

---

### Post by VinzC on 2008-11-17
> **C.S.Cameron said:**
> Use Unetbootin to install the full Ubuntu iso.

Tried it but as I explain in my top post Unetbootin »transforms« the Alternate install into a networked install, which doesn't work since there is no appropriate network driver.

The only thing I'm considering is to tweak the CDROM detection in the LiveCD image itself but since it's a binary... Unless there's another solution of course.

---

### Post by C.S.Cameron on 2008-11-17
Can you use the Full Ubuntu iso and not the Alternate?
The Alternate is for network install, there is not much on the disk, it all has to be downloaded during the process.

---

### Post by VinzC on 2008-11-18
> **C.S.Cameron said:**
> Can you use the Full Ubuntu iso and not the Alternate?
The Alternate is for network install, there is not much on the disk, it all has to be downloaded during the process.

Well, I thought I understood the alternate image was designed for LVM and a no-network install... I wanted to make sure and started the Alternate CD in a virtual machine and it did an install from the CD itself. :confused:

BTW Unetbootin only suggests "*Live*" and "*Network*" install if you don't have an already downloaded ISO. Do I have to understand the Full install is the Live one? Since the Alternate ISO image is not a LiveCD, there is plenty of room for packages, am I right? That's how I understood the Download page. Was I mistaken?

---

### Post by C.S.Cameron on 2008-11-18
Oops, I was thinking of the mini iso.

---

