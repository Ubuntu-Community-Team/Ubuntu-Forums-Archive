---
title: "newbie on ubuntu mimimal"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by xinxinren on 2010-05-15
I am a newbie in ubuntu. I just installed a ubuntu 9.10 minimal. The installation works fine. Since it is in the console mode, can someone give me a pointer on how do I access the usb drive and cdrom? Thanks in advance.

---

### Post by kerry_s on 2010-05-15
sudo apt-get install pmount

pmount /dev/?
pumount /dev/?

you can use "fdisk -l" to find /dev/?

---

### Post by xinxinren on 2010-05-16
kerry_s,

thanks for the info. I tried pmount, somehow, it does not work. I got a message saying that 
"error: device /dev/sdb1 is not removable.

I used fdisk -l that shows the usb is /dev/sdb1. I tried mount /dev/sdb1 /mnt, and I can see the files in usb disk. 

Thanks again.

---

### Post by kerry_s on 2010-05-16
> **xinxinren said:**
> kerry_s,

thanks for the info. I tried pmount, somehow, it does not work. I got a message saying that 
"error: device /dev/sdb1 is not removable.

I used fdisk -l that shows the usb is /dev/sdb1. I tried mount /dev/sdb1 /mnt, and I can see the files in usb disk. 

Thanks again.

sorry, just looked it up, looks like pmount is broken for now, some libsysfs bug. i guess you'll just have to stick with mount/umount.

---

