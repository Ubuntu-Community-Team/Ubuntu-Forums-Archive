---
title: "errno 5"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by Gskellig on 2010-10-27
I'm trying to install Ubuntu Netbook Remix (10.10) on my Asus eeepc 1000HE. I'm installing it as a dual boot with Win7.

Just after partitioning and formatting I get the error```
[Errno 5] Input/output error
This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. ...etc...
```

Hard drive is a 160GB SATA.
dev/sda1 = 100mb windows reserved
dev/sda2 = ~50GB windows7 partition
dev/sda3 = ~50GB ext4 partition
dev/sda4 = 2GB linux swap area
other 50ish GB I will probably format as fat32 for data storage later on.

Installing ubuntu 10.10 desktop edition works fine.

I have tried it on two different USB sticks, an external CDROM (which is how I installed Win7), and a faster SDcard (which I've had the most success, probably because its just faster)

The instructions I used to make the usb/sdcard are the ones from here: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
after clicking "Show me how"

---

### Post by P4man on 2010-10-28
Did you check the ISO you downloaded? The problem could be with the image.

---

