---
title: "Grub error 17 after fresh install"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Diod on 2008-02-27
I just removed vista and went for a kubuntu only system. But after the installation(from the DVD(64-bit)), grub gives me error 17.

There are 3 drives in the system. Dont really know what other info to give

---

### Post by logos34 on 2008-02-27
[Super Grub Disk ]("http://supergrub.forjamari.linex.org/")should be able to boot you into ubuntu.  It may be that your menu.lst has the wrong root and/or grub is pointing to the wrong bios address.  Correct the root and 'groot' lines:

gksudo gedit /boot/grub/menu.lst

and reinstall grub to mbr:

> **sudo grub**

**> find /boot/grub/stage1**
(enter output in next command)
**> root (hd?,?)**
**> setup (hd0)** (--> write grub to boot drive)
**> exit**

---

### Post by Diod on 2008-02-27
I got around the error by disconnecting all the drives except the main one.

But now, when i boot(it gets past grub), all i get is a black screen.

Before the black screen, i get a screen with, bottom left, some text about the kernel(no error or anything).

I also get this when trying to run kubuntu straight from the dvd. I installed with the text setup.

Running the NVIDIA 8800GTX

EDIT: Cheered a bit too soon. After i plugged in the HDDs, the same old error 17 comes up :(

---

### Post by dstew on 2008-02-27
First, plug all your drives in again as they originally were. Now, the grub error, is it just "Error 17" or does it also give an explanation, such as "Error 17: Cannot mount selected partition"?

If it is just the error number, then you will have to re-install grub. It is not hard to do. You can use the supergrub disk or the re-install instructions as posted by logos34.

---

### Post by Diod on 2008-02-27
It's just "Error 17".

I'll try to reinstall grub tomorrow, if/when i got time

---

