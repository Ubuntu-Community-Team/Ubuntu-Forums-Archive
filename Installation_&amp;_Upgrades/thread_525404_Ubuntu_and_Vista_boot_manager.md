---
title: "Ubuntu and Vista boot manager"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by surrizola on 2007-08-14
Hi, i am new to ubuntu (i use linux for a while but only for servers). I have a new laptop and i want to install ubuntu 7.0.4 but i want to keep mi vista installation (i need it for workf).
Is there any possibility to install ubunty and use the vista boot manager?
What are the steps i must follow during the ubuntu installation ?

---

### Post by renzokuken on 2007-08-14
have a look at this

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

why dont you want to use grub?

---

### Post by surrizola on 2007-08-14
>>why dont you want to use grub? 
What happens if i want to remove ubuntu? how can left my laptop as if ubuntu never exists? i mean .. how can a i remove linux without affect the vista installation or boot manager

PD: I like a lot linux but is a work machine.

---

### Post by renzokuken on 2007-08-14
fair enough, then i hope that guide helps

i beleive there is an option somewhere in Vista to "restore the boot loader" back to its original state

another option would be to install ubuntu, but **NOT** install grub when it asks, then use a SUPERGRUB CD to choose which to boot into, then to completely remove ubuntu without any trace all you have to do is erase the ubuntu partition

---

### Post by stchman on 2007-08-14
> **surrizola said:**
> >>why dont you want to use grub? 
What happens if i want to remove ubuntu? how can left my laptop as if ubuntu never exists? i mean .. how can a i remove linux without affect the vista installation or boot manager

PD: I like a lot linux but is a work machine.

Very easy, get a boot CD with fdisk on it and type fdisk /mbr.

---

