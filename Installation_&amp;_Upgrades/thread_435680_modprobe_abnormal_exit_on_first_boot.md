---
title: "modprobe abnormal exit on first boot"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by giggsey on 2007-05-07
I've just installed Feisty onto a dual boot with Windows XP using the graphical installer, and when I rebooted it for the first time, I get this error:

[http://img135.imageshack.us/img135/6140/00001kl8.jpg](http://img135.imageshack.us/img135/6140/00001kl8.jpg)

After a while on that, it brings up some prompt. (Can't remember its name off the top of my head, but not the normal prompt).

Following some advice from IRC, I downloaded and tried to install feisty from the alternative CD. However, that won't even boot, as it gives the same error.

I have a Packard Bell NEC P660400201 with a NEC COMPUTERS INTERNATIONAL SiS650 1.0 motherboard, a HL-DT-ST DVDRAM GSA-H10A DVD drive (I have tried it with removing the drive, and it still didn't work), and a ST340810A Hard drive (Info from  Belarc Advisor).

Any ideas?
*~ Joshua Gigg*

---

### Post by giggsey on 2007-05-08
I've changed my hard drive and DVD drives around, so that the HDD is on IDE1 and the DVD drive is on ID2, and it still gives an error.

Ideas needed.

I don't really want to keep trying to have it booting but failing.

---

### Post by giggsey on 2007-05-10
*bump*?

---

### Post by SeaWolf on 2007-05-15
So, it looks like you have a motherboard with an SiS650 chipset.  So do I.  An Asus P4S333-VM.  And I also have the same problem.  I'm back to fighting this because I had problems with the nvidia driver, but I did get a susscessful install by unplugging all of my USB devices and unplugging all of the ide drives except for my DVD drive and the hard drive I was installing to.  When you install, let the syytem choose how it will partition the hard drive.

---

### Post by giggsey on 2007-05-16
I only have a DVD-RAM and HDD in the PC, and all the USB stuff was already unplugged/switched off.

If it helps, I have a ATi RADEON 9600 in their.

---

### Post by mohtasham1983 on 2007-06-16
I am having the same problem.

I partitioned my hard drive manually and used same partition i had for edgy. 

I also unplugged all USBs but still no chances.

---

### Post by giggsey on 2007-08-06
I've managed to get my ubuntu working - see [http://giggsey.com/2007/08/06/ubuntu-feisty-modprobe-solved/](http://giggsey.com/2007/08/06/ubuntu-feisty-modprobe-solved/)

---

