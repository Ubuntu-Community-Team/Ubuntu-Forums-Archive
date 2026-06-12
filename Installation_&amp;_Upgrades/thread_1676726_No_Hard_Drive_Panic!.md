---
title: "No Hard Drive Panic!"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by kesent7 on 2011-01-27
ok quick question i have a netbook gateway and i seem to have ripped the  cord that connects the hardrive to the computer and i was wondering if i  can install linux netbook edition on a usb drive and have the netbook  boot off of that would it work and if so how?

---

### Post by gordintoronto on 2011-01-27
Yes, it should work, if your netbook can boot from USB.

If you plug in a flash drive, you can open Accesories/Terminal and enter the command:
sudo fdisk -l
You should be able to see what the flash drive is called, such as /dev/sdb1
You can boot from CD and install to sdb1.

---

### Post by Mark Phelps on 2011-01-28
> **kesent7 said:**
> ... can install linux netbook edition on a usb drive and have the netbook  boot off of that would it work and if so how?

It CAN be done -- whether or not you really want it done this way is a different question.

You'll be accessing your installation through a USB port -- which will severely limit the data transfer rate.

You may get acceptable performance if the USB port is v2.0.  If it's version 1.1, it's likely to be so slow as to be useless.

---

