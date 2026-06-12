---
title: "Help installing on a usbflash drive"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by tumble on 2007-02-27
Hi, So I'm running Windows XP on my laptops 40gig hd (not much space left now). I got a 4gig flash drive and thought ooh great I'll install Ubuntu on it. I burnt a cd with 6.10 version and ran that live. All working very nice- even gaim. So I went to install and cool it shows up my flashdrive as sda (which is blank) so i choose option to erase completely. It seems to work then the installer quits saying "partitioner failed".
So I try again this time choosing to manually edit partiontable, the sda is greyed out and i get this message.

 " The kernel is unable to re-read the partitiontables on the following devices:
- /dev/sda

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access."

What is wrong and what can I do about it?

Tumble out

---

### Post by obelisk on 2007-02-27
How did you format the drive, mkfs.vfat -F 16 or 32?

---

### Post by obelisk on 2007-02-27
Follow this tutorial: [http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

---

