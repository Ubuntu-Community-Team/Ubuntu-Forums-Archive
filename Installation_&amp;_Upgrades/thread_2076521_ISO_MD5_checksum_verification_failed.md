---
title: "ISO MD5 checksum verification failed"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by DDZ on 2012-10-26
Hello!


I would like to install Lubuntu 12.10 64 bits on a 8 Gb USB Key  (ext4 formatted) with 5 Gb for persistent storage. I tried it by using Fedora liveusb-creator because usb-creator-gtk can set only 4 Gb max for persistent storage.

I got this error message:
> lubuntu-12.10-desktop-amd64.iso selected
The Master Boot Record on your device is blank. Pressing 'Create LiveUSB' again will reset the MBR on this device.
Resetting Master Boot Record of /dev/sdc
Verifying filesystem...
Setting /dev/sdc1 label to LIVE
Verifying ISO MD5 checksum
There was a problem executing the following command: `checkisomd5 "/home/sebmaurice/Mes_Telechargements/Lubuntu/lubuntu-12.10-desktop-amd64.iso"`
A more detailed error log has been written to '/tmp/liveusb-creator.log'
ISO MD5 checksum verification failed

This is the /tmp/liveusb-creator.log:
> umount /dev/sdc1

cat /usr/lib/syslinux/mbr.bin > /dev/sdc

/sbin/dosfslabel /dev/sdc1 LIVE

checkisomd5 "/*homedirectory*/Lubuntu/lubuntu-12.10-desktop-amd64.iso"Press [Esc] to abort check.

The media check is complete, the result is: NA.

No checksum information available, unable to verify media.


Can you help me, please?
Thank you in advance! :)

---

### Post by dino99 on 2012-10-26
Lot of usb keys have a borked table, and only formatting is not enough. So with gparted, check first the table (built a new one), then format again as ext4 and set it bootable.

---

### Post by DDZ on 2012-10-26
> **dino99 said:**
> Lot of usb keys have a borked table, and only formatting is not enough. So with gparted, check first the table (built a new one), then format again as ext4 and set it bootable.
Done.
Same problem. I think the lubuntu-12.10-desktop-amd64.iso file hasn't checksum information.

---

### Post by 2F4U on 2012-10-26
Not quite true. MD5 and SHA1 checksums can be found here:

[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/)

Scroll down until you see the list of files on the download server.

---

### Post by DDZ on 2012-10-26
> **2F4U said:**
> Not quite true. MD5 and SHA1 checksums can be found here:

[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/)

Scroll down until you see the list of files on the download server.
Ah OK, thank you. I will try this monday and I tell you.

---

### Post by DDZ on 2012-10-29
[FONT="Times New Roman"]Finally, I use usb-creator-gtk with all free space left for persistance. No ISO MD5 checksum verification error.
_[Answer in french]("http://forum.ubuntu-fr.org/viewtopic.php?pid=11314731")_[/FONT]

---

