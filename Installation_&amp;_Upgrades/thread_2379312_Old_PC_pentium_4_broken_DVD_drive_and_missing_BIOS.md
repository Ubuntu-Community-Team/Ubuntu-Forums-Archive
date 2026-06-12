---
title: "Old PC pentium 4 broken DVD drive and missing BIOS USB boot"
date: 2017-12-04
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2017-12-04
Hi,
I would like to install lubuntu 16.04 or 14.04 32 bit on an old PC with installed windows xp that has pentium 4 2.67 GHz and 2 GB RAM. The problem is that the DVD drive is broken and I do not have any external drive. Moreover, the BIOS does not allow to boot via USB.
So the only way that I know is to use [Unetbootin]("https://unetbootin.github.io/"). I followed the procedure described [here, ]("https://askubuntu.com/questions/484434/install-ubuntu-without-cd-and-usb-how")with hard driver install. After the installation, lubuntu, both versions, do not boot up. The boot procedure gets stuck on busy box.

Thank you

---

### Post by yancek on 2017-12-04
The unetbootin method described on that page is referred to as a 'frugal install'.  What that does is put the extracted Lubuntu iso file on the drive and create an entry for it in the windows boot menu.  If it is successful, you should see your standard windows boot menu with an additional entry which says unetbootin and it should start  the same way it would start a Live CD/DVD.  If that doesn't work, I expect the creation of the frugal install failed for some reason and I would suggest you try it again.  Did you see any warning or error messages when you were doing the frugal install with unetbootin?

---

### Post by Superdude_123 on 2017-12-06
Could you take the drive out and put it in another machine? Its a bit backwards, but it could work!

---

### Post by erotavlas on 2017-12-07
> **yancek said:**
> The unetbootin method described on that page is referred to as a 'frugal install'.  What that does is put the extracted Lubuntu iso file on the drive and create an entry for it in the windows boot menu.  If it is successful, you should see your standard windows boot menu with an additional entry which says unetbootin and it should start  the same way it would start a Live CD/DVD.  If that doesn't work, I expect the creation of the frugal install failed for some reason and I would suggest you try it again.  Did you see any warning or error messages when you were doing the frugal install with unetbootin?

Yes, I can see the Unebootin choice in the windows menu together with windows XP. Then if I select it, I can see the Unetbootin menu that is the same menu of USB live of lubuntu plus UNetbootin as first choice (grub4dos 0.4.3).
If I try Install lubuntu (is the same for try lubuntu) appears booting 'Install lubuntu' and:
```

(hd0,1)
Filesytem type is fat, pratition type 0xc
[Linux-bxImage, setup=0x4200, size=0x654600]
[Linux-initrd @ 0x7ca38000, 0x15b2122 bytes]

```

after it gets stuck on BusyBox v1.21.1 built-in shell (ash)
(initramfs)

What can I do?
Thank you

---

### Post by erotavlas on 2017-12-10
> **Superdude_123 said:**
> Could you take the drive out and put it in another machine? Its a bit backwards, but it could work!

No, I cannot do this. It has the old ATA interface and I do not know where I can find another so old PC :(

---

### Post by sudodus on 2017-12-10
There are adapters, that could work for you. Search the internet for "USB to IDE & SATA Cable" (without quotes), and you should find some useful adapters, that you can use to connect your IDE/PATA hard disk drive to another computer (with USB).

I have such an adapter, and it works well (it is even possible to boot via it in computers that boot via USB).

---

### Post by mastablasta on 2017-12-11
another option is using the floppy drive if you have it. load plop boot manager on floppy and use it to boot from USB drive. proceed with install from there.

---

