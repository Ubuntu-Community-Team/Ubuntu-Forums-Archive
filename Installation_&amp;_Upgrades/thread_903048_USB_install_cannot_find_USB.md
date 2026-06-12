---
title: "USB install cannot find USB"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by rayblasdel on 2008-08-27
I am currently trying to install Ubuntu Server 8.04 on to an Intel Server Platform (S3000AHLX), using a USB drive in place of the standard CD. I have formatted the USB drive to properly boot and start the installation, and have replaced the standard CD install vmlinuz with the current HD-media version.

My problem is after the installation has started and to goes to mount the USB drive to access the ISO, it returns a failure to find ISO. No matter where I place the ISO file, packed or unpacked it cannot find what it is looking for. My best guess is that it is not actually mounting the USB drive, and the installation provides no means for identifying the problem or providing an alternative /dev/. 

I have been searching and reading a lot of posts and information but have not encountered any reference to a problem such as this. If anyone has any suggestions, I would be eternally grateful.

---

### Post by drejk on 2008-08-28
Well I just hit a similar problem, it boots from the USB, but when it comes to detecting cdrom it fails. If I provide it with /dev/sda or /dev/sda1 (which is the USB flash) it fails anyways. 

If I try to manually mount the drive it fails and says that there is no such device as /dev/sda ....


Drejk

---

### Post by Fredrik_b on 2009-01-30
Anyone have a sulution to this? I am booting the alternative CD from USB and I cant find the USB stick during the instalation. All /dev/sda-sdh5 is emty when I run ls "/dev/sda" etc.

---

