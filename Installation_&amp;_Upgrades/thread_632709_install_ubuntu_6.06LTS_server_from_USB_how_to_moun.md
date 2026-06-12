---
title: "install ubuntu 6.06LTS server from USB: how to mount the USB to /cdrom"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by qiu2007 on 2007-12-05
I want to install ubuntu from USB memory.

I find the page about it.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I did it. 

But I have to mount the  flash drive as /cdrom manually.

I used the following command


mkdir /cdrom
mount -t vfat /dev/sda1 /cdrom

It worked.

If the flash drive can be mounted automaticlly?

I have tried to modify the initrd.gz file in /install folder.

//unpack initrd.gz
copy the initrd.gz to /tmp

mkdir initrd.dir
cd initrd.dir
gzip -dc /tmp/initrd.gz |cpio -i

do something....

//pack initrd.gz
find . | cpio --create --format='newc' > ../initrd
cd ..
gzip -9 initrd 

copy the new initrd.gz to flash drive



I have tried to modify some files like init, /etc/fstab, /bin/cdrom-checker-menu and so on. But all of them did not work.

If someone here can tell me what I should do to mount the flash drive in initrd?

Thank you,

---

### Post by qiu2007 on 2007-12-06
I have tried to boot from SGD. I got the same problem. 

I followed this one.
[http://ubuntuforums.org/showthread.php?t=575406&highlight=Ubuntu+supergrub+usb](http://ubuntuforums.org/showthread.php?t=575406&highlight=Ubuntu+supergrub+usb)

---

### Post by qiu2007 on 2007-12-10
any reply?

---

