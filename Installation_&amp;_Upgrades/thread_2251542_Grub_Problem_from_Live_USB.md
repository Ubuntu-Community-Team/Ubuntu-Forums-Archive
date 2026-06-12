---
title: "Grub Problem from Live USB"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by german5 on 2014-11-04
Hi All,

Sadly, I have a laptop with windows 8.1 and while playing around I think I screwed something up. I tried installing 14.10, but I got the GRUB problem, so I resetted my laptop. Today, I created a a live usb using the Universal USB Installer, and after disabling safe boot and enebaling legacy boot in my laptop, I get:

 GRUB loading
Welcome to GRUB

error: Unkown filesystem
entering rescue mode
grub rescue >

when I type ls

I get (hd0) (hd0, gpt11)...... (hd0, gpt1) (hd1)

So, I can't even run a live usb to fix the grub. When I set the BIOS to boot mode UEFI, it loads windows no problem.

I would prefer to have a dual boot machine, but I'll settle for being able to at least boot linux from a live USB. Further, my new computer is so effing retarded and can't even boot from a CD/DVD so any help is greatly appreciated.

Thank you

---

### Post by oldfred on 2014-11-05
Try a different installer. There is/were some issues with certain installer.
Double check that the ISO you downloaded is correct.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    
       Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

