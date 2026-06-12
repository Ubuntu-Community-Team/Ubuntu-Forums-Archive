---
title: "Can i install 9.10 onto a usb flash drive"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by hatewindows on 2010-01-22
Hello all--I wanted to know if i can install 9.10 onto a usb flash drive--without using my computers hard drive at all when running ubuntu off the flash drive--and how can i do this? Thanks so much..

---

### Post by raymondh on 2010-01-23
Yes. Look at/for 'persistent' installs. As an example:

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

Booting into your ubuntu flash drive will require you to select it from BIOS so make sure your system is able to boot from a USB drive.  A option/workaround is to use GRUB2 as the bootloader in your HD's MBR.  I'd rather just control the boot through the BIOS quick change ... that way, I preserve the windows bootloader.

Regards,

Raymond

---

### Post by hatewindows on 2010-01-24
THANKS RAYMOND!!  Have a great day!!!:popcorn:

---

### Post by Handssolow on 2010-01-24
There's more information here below and if you're successful perhaps you'll post a report.

[http://ubuntuforums.org/showthread.php?t=1179595](http://ubuntuforums.org/showthread.php?t=1179595)

With flash drives, my experiments last year produced Ubuntu persistent but it stopped working after a few updates and I had to start afresh. Another approach was to treat the flash drive like a hard drive but then  the data transfer rate was too slow, I couldn't run Google Earth on my netbook.

If you need to wipe the flash drive look here

[http://www.pendrivelinux.com/restoring-your-usb-key-partition/](http://www.pendrivelinux.com/restoring-your-usb-key-partition/)

Re-visiting this project I'm stuck because I can't get a live CD of 9.10 to run properly.

---

