---
title: "Need help installing through flash drive."
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by bobmatino17 on 2010-08-31
I reacently bought a new computer, and it does not have a cd drive, i know that you can install off of a flash drive, and i was wondering if anybody could tell me how.

---

### Post by oldfred on 2010-08-31
There are a variety of ways. unetbootin and pendrive linux are easy. 

Also has link to USB Flash drive instructions:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Allows extra space on flash to be used
[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)
With lots of links but using FAT, syslinux & grub4dos
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

If you have access to a computer with a CD you can install directly from the liveCD. The system administration, startup disk creator is very straight forward.

I prefer installing grub2 and directly booting the ISO from the USB but that is a little more advanced.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

### Post by bobmatino17 on 2010-08-31
thank you very much for your help!

---

