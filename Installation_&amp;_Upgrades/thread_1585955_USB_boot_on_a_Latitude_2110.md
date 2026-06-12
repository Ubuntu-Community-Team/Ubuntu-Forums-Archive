---
title: "USB boot on a Latitude 2110"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by bishounen on 2010-10-01
Hey all,

I'm trying to perform a USB boot from an Ubuntu 10.10 live USB setup for Ubuntu Netbook remix onto a Dell Latitude 2110 netbook.  The system does indeed recognize the USB key once I select it from the Dell boot menu, but I never get any farther than:

> SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al

and it never goes any further.  Do I have a bad USB image here, or do you all think it's a compatibility issue with the netbook?  I should note that this netbook has run both Win7 and WinXP without issues, so it is fully functional.  (It's brand new)

Thoughts?

---

### Post by dino99 on 2010-10-01
might be a specific Dell config issue (special Dell partition at the beginning of hdd)

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

---

### Post by bishounen on 2010-10-01
Only one partition.  This netbook came with Win7 + Dell recovery partition on it.  We did a full partition delete and reformat and installed XP on it.  So no funky Dell partitions left.

I tried an experiment, and downloaded 10.04 and make a live USB setup with that instead.  On this setup I am able to get to the menu, and it starts the boot process. But partway there I get an intramfs error saying it cannot mount /dev/loop1 on /cow.  I have no idea what that means, other than it's obviously an fs mounting issue.

It then gives me a prompt, and if I type in "exit" and hit return it continues booting, but then fails with a kernel panic.

So I;m not sure what's happening here, but hopefully those error messages are a bit more enlightening.

---

### Post by bishounen on 2010-10-01
Just as a follow-up, I went back and re-made the 10.10 live USB again.  (I'm just re-using the same 2GB USB key) and got the same error message from my opening post.

---

### Post by oldfred on 2010-10-01
Is it perhaps this bug?

Maverick images burned to usb key on lucid fail to boot - different syslinux version 
ui in /isolinux/isolinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by bishounen on 2010-10-01
Could be, except I burned this one on a Windows machine, which has no installed version of Syslinux.  (for obvious reasons)

So I don't know if it is the same bug, a related one, or something else entirely that simply has similar symptoms.

---

### Post by Bellerophon on 2010-10-11
Having the same issue. Creating the USB stick on my Windows 7 machine, failing to boot the stick on an Asus 1101HA.

---

### Post by kumpsath1 on 2010-10-13
This must be problem during USB creation. I'd the same and got rectified by creating bootable drive from Windows XP. I installed unetbootin on windows machine, downloaded 32 bit ubuntu and created bootable there. Installation was failing at the end. Again created and installed and working fine.
I think 10.10 is UNSTABLE now or may be specific issues for Dell (E6500) hardware.

---

