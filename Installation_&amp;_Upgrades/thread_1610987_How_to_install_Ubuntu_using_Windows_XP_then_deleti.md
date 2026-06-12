---
title: "How to install Ubuntu using Windows XP then deleting XP"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by smuro on 2010-11-01
I want to put Ubuntu up on one of my computers but I don't have a  working CD drive on it and my USB drive is only 1 GB while 2 GB is  needed.

Is there any way I can install Ubuntu through Windows with Wubi f.x. and then delete the windows part or?

---

### Post by mikewhatever on 2010-11-01
It is possible, but requires booting from a cd and migrating the wubi installation to a partition. Not a solution for you.
I suggest using the 1GB usb and installing from the minimal image.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by krishnandu.sarkar on 2010-11-01
No if you install Ubuntu with Wubi then deleting Windows will also delete Ubuntu. And Ubuntu installed with Wubi has so many problems later.

If you have USB Drive, why don't you install from USB??

Make it Live USB using unetbootin, and then boot from it and install :)

---

### Post by coffeecat on 2010-11-01
> **smuro said:**
>  and my USB drive is only 1 GB while 2 GB is  needed.

If you were wanting to install Ubuntu to your 2GB USB drive in the normal way, then 2GB wouldn't be large enough. But if you can boot from USB, you can burn the desktop ISO to the USB drive to make a bootable live USB, boot up from that and install Ubuntu to the internal drive from the live session. It also gives you a chance to test your hardware in the live session before you commit to a hard drive install.

You need less than 1GB for this, so your USB drive is ample. More information here, including how to prepare the USB drive from Windows.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The reason you need so much less space is that a live Ubuntu USB stick is highly compressed. But a default install on a hard drive (or USB drive) before you have updated or installed any extra apps is about 2.2GB.

---

