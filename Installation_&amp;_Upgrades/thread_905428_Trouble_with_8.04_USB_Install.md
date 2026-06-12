---
title: "Trouble with 8.04 USB Install"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by ARhere on 2008-08-30
I am having trouble getting 8.04 installed on a Intel Atom D945GCLF Single board computer.

I am trying to install the OS on a 4GB USB stick and it continues to fail at the last steps.  The first time I got a "Fatal Grub Error" and the second time it hung with 100% CPU at the end of "Configuring your hardware" just before the boot loader part of the installation.

The USB stick is the only non-volitile memory during the install and I tried it before with a USB external hard drive and that install worked fine.  I have checked the CD for errors and am also performing a full memtest and so far no errors.

I know a USB stick is not the best but it is a "fun" project.  It supports Compiz and OpenGL well, so I want to measure its power use while playing games on it ;-)

-AR

---

### Post by KiwiNZ on 2008-08-30
Thread title amended by request

---

### Post by Vivaldi Gloria on 2008-08-30
> **ARhere said:**
> I am trying to install the OS on a 4GB USB stick

There are some guides here:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by ARhere on 2008-08-30
> **Vivaldi Gloria said:**
> There are some guides here:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I followed those guides.  If no other hard drive is attached, installation is pretty straight forward, yet these errors still occur.  I know it has to do with the USB memory stick specifically, because the USB hard drive worked the first time.

-AR

---

### Post by Pumalite on 2008-08-30
Maybe it would help to read this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by ARhere on 2008-08-31
> **Pumalite said:**
> Maybe it would help to read this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

I did, no difference.

UPDATE:  I tried one more time, and this time hitting CTRL+ALT+F1 to watch for an error message.  Just when the installation freezes I saw a general I/O error in the comments.  My USB drive is a 4GB stick with a 3.8GB main partition and a 250MB swap file.  My guess is that the installation is having trouble with too little storage space; mot sure why.

I returned the 4GB USB stick for a 16GB USB stick.  When my micro-ITX case arrive Thursday I will try again.

-AR

---

