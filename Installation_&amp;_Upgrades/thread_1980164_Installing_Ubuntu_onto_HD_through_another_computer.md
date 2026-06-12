---
title: "Installing Ubuntu onto HD through another computer"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by marcinx27 on 2012-05-14
I have a netbook with a broken screen that I wanted to put Ubuntu on.  I have an SATA to USB connector, but I don't know what I should do to install Ubuntu onto the hard drive from the netbook.

Any ideas?

---

### Post by marcinx27 on 2012-05-14
Actually, I ran the usb installer and am at the "installation type" partition area.  I imagine my /dev/sda is the desktop that I don't want to touch and /dev/sdb is the one I want to put ubuntu on.  Does anyone know where I go from here?

---

### Post by nicolasdiogo on 2012-05-14
not sure i understand what you are trying to do.

you want to install ubuntu on a netbook

or create a usb installation - to install ubuntu on another PC?

---

### Post by efflandt on 2012-05-14
Yes if the netbook drive is connected to another computer (either with USB or internally) you can install Ubuntu on it.  You do NOT want to do any partitioning automatically.  When it asks where or how you want to install Ubuntu, you want the last option (something like "Other").

From that it should be obvious from size and partitioning which one is the netbook drive.  If you are installing from CD and the netbook drive is external it would usually be sdb.  Otherwise if the drive is internal and/or installing from USB stick, it should be obvious which drive is which from listed partitions and drive size (or output of **sudu fdisk -l** in a terminal).

**IMPORTANT NOTE:** At the bottom of that partitioning screen in the installer is a dropdown list to select where to put grub.  Make sure that you put grub in the mbr of the netbook drive.

I am not certain, but I think it might install additional drivers for video on the installing computer if that would use something different from default drivers.  When I booted install iso on USB stick it, used default nouveau driver for my NVIDIA video, but after installing on a USB drive, that booted up with nvidia driver already installed.  But if you install with a PC that uses Intel or legacy (old ATI from before acquired by AMD), it may just include default video drivers.

---

