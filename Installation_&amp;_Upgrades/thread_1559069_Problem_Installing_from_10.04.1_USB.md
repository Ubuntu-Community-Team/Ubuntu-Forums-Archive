---
title: "Problem Installing from 10.04.1 USB"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2010-08-23
Installation from 10.04.1 USB stalled at step 3 (after selecting the default keyboard).

No problem under exact conditions when installed from 10.04 USB.

Machine:  HP DV6, Intel core 2 duo, 4 GB DDR2.

The iso image was md5sum-verified.  No problem installing the same image in VirtualBox v.3.2.8.

Created a new USB stick.  Same problem.

---

### Post by lechien73 on 2010-08-23
Could you give a little bit more information, please? How was the USB stick created? Is this an upgrade? Is it a dual-boot install?

Other threads have suggested that the stage 3 freeze could be due to the hard disk geometry, so could you please post the output of

```
sudo fdisk -l
```

---

### Post by ping-wu on 2010-08-23
> **lechien73 said:**
> Could you give a little bit more information, please? How was the USB stick created? Is this an upgrade? Is it a dual-boot install?

Other threads have suggested that the stage 3 freeze could be due to the hard disk geometry, so could you please post the output of

```
sudo fdisk -l
```

1.  The USB stick was created with "Startup Disk Creator" from a fully updated 10.04 on a different machine. 

2.  This is not an upgrade, but a fresh installation.

3.  It is a dual-boot install (sda3) along with 9.10 (on sda1).

4.  I don't have access to that particular machine on which this problem occurred right now, but could you give me the links to those threads which discussed the stage 3 freeze?

5.  Additional info:  I was able to subsequently install from an old 10.04 USB on that same partition without any problem.  Again, for some reason the 10.04.1 gave me the stage 3 freeze.

---

### Post by lechien73 on 2010-08-23
This was the thread I was looking at, of course it was referring to 10.04 - not 10.04.1, but I would have presumed the installer would be the same.

[http://uri.tl/13](http://uri.tl/13)

---

### Post by ping-wu on 2010-08-23
> **lechien73 said:**
> This was the thread I was looking at, of course it was referring to 10.04 - not 10.04.1, but I would have presumed the installer would be the same.

[http://uri.tl/13](http://uri.tl/13)

I seem to have found the culprit of this problem--I was using the USB stick (Kingston DataTraveler 4GB) as purchased.

After I reformatted the USB stick, this problem went away.  I was able to proceed with the installation, w/o the stage 3 freeze.

---

### Post by bluetomgold on 2010-09-16
I'm having the exact same problem. 10.04.1 install on Medion Akoya E1210 (MSI  Wind) hangs at step 3 having set keyboard. I'd already tried a fresh  format before coming across this thread.

Have now also tried formatting from within Universal USB Installer (with  which I put the ISO on the USB pendrive) and alternative persistence  settings. No joy.

Unless anyone has any better ideas I'm gonna try booting from a DVD (from an external drive) tomorrow.

---

### Post by bluetomgold on 2010-10-26
No issues installing from DVD.

---

