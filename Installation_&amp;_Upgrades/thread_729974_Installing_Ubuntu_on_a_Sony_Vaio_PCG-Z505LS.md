---
title: "Installing Ubuntu on a Sony Vaio PCG-Z505LS"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by pancakeman on 2008-03-20
I'm trying to install Ubuntu 7.10 Desktop Edition on  Sony Vaio PCG-Z505LS and have no idea how to go about doing it. It has no CD drive and doesn't support booting from USB.  Any help?

---

### Post by dstew on 2008-03-20
If it has a floppy drive, you can do a network install using [unetbootin]("http://lubi.sourceforge.net/unetbootin.html"). Another way is to use [Wubi ]("http://wubi-installer.org/")from within Windows. If you have no Windows, no floppy, no CD-ROM, no USB boot, you can still do a network install if you have a PXE BIOS. That is a little more complicated.

EDIT: I just checked your laptop specs. You should be able to do the network install using unetbootin, or Wubi. However, if you only have the standard 128 Mb memory, you might consider installing Xubuntu instead of the regular Ubuntu desktop.

---

### Post by pancakeman on 2008-03-20
There is no Operating System installed on the laptop.  How do you tell if you have a PXE BIOS?

---

### Post by dstew on 2008-03-20
It is usually touted as a feature in the specs. I didn't see it, and it is not often a feature of laptops. You can look at your BIOS sceen (by pressing F2 or F12 at boot-up) and see if there is a network boot option. I think you should go with unetbootin. Look at the unetbootin site for the part about installing with floppies only. You have to get a Debian minimal install system (five or six floppies) then you can use unetbootin.

---

### Post by pancakeman on 2008-03-22
How do I go about doing a minimal install of Debian using floppies?

---

### Post by Jahnzee on 2008-03-22
Do you have the USB floppy drive or CD-ROM drive?  I just installed Fedora on my Z505-LS using the PCMCIA CD-ROM, and it was interesting.

It works like a champ though, once installation is done.  The video card and ethernet card were recognized no problem.  The PCMCIA CD-ROM is NOT recognized, but because the BIOS recognizes it, you can still use it to boot into the installer.

---

### Post by pancakeman on 2008-03-22
I don't have the PCMCIA CD-ROM drive but I have the floppy drive.

---

### Post by Jahnzee on 2008-03-22
What OS, if any, is currently on the laptop?

---

### Post by pancakeman on 2008-03-22
It has no operating system on it right now.

---

### Post by dstew on 2008-03-22
Look at the unetbootin site. There is a link to a [Debian minimal install system]("ftp://ftp.debian.org/debian/dists/testing/main/installer-i386/current/images/floppy") down the page. It consists 6 floppy disk images. You download them, and burn them to floppies as images. [Here]("http://www.debian.org/releases/stable/i386/ch04s03.html.en") are instructions to install from floppies from Debian's site.

---

### Post by Jahnzee on 2008-03-22
Sounds like your options are:

- Download the boot images for Debian Sarge, and boot those one-by-one.  Then, you'll have a shell with network capability, and you can install Ubuntu over the network.  Use these instructions:  [https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

- Look on eBay for a Z505 PCMCIA CD-ROM drive

- Borrow someone's Z505 PCMCIA CD-ROM drive

---

### Post by pancakeman on 2008-03-23
-edit-
I tried it again and it got past the problem, sorry.

---

### Post by pancakeman on 2008-03-23
In the part of the installation where it explains how to get debootstrap, when I put in

wget [http://ftp.bit.nl/ubuntu/pool/main/d/debootstrap/debootstrap_0.2.45ubuntu36_i386.deb](http://ftp.bit.nl/ubuntu/pool/main/d/debootstrap/debootstrap_0.2.45ubuntu36_i386.deb)

it says that it wasn't found, s there another file that I should be using instead of this one?

and what does "|" mean?

---

### Post by dstew on 2008-03-23
Try this one:```
wget http://nl.archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.3build1_all.deb
```

And '|' is a pipe character. It is used to feed the output of one command into another. For example, if you have a long directory display, and you want to go through it a page at a time, you can feed the output of the **ls** command into the **more** command like this:```
ls -l | more
```

---

### Post by pancakeman on 2008-03-23
Whenever I put in

/usr/sbin/debootstrap --arch I386 feisty /target [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/)

to download the packages for feisty fawn (that is what I would put in to get feisty faw, right?)

I get the following

I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving Dependencies of required packages...
I: Resolving dependencies of base packages...
W: Failure trying to run: chroot /target mount -t proc proc /proc
~#

What does that mean and how do I fix it please?

---

### Post by dstew on 2008-03-23
I think the bootstrap .deb is for gutsy, so maybe try that instead of feisty. But before you do that, just try entering the chroot command yourself as it says in the guide:```
chroot /target /bin/bash
```Then mount the /proc filesystem:```
mount -t proc proc /proc
```

---

### Post by pancakeman on 2008-03-23
Whenever I put in

chroot /target /bin/bash

it says 

chroot: cannot execute /bin/bash: No such file or directory

and when I put in 

mount -t proc proc /proc

it says

mount: mounting /proc on /proc failed: Device or Resource Busy

trying Gutsy didn't work either

---

