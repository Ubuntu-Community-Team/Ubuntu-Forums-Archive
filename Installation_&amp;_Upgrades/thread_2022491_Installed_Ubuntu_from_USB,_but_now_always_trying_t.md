---
title: "Installed Ubuntu from USB, but now always trying to boot from USB"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by aecs1234 on 2012-07-11
Hi,
My netbook does not have a CD ROM, I just installed Ubuntu 12.04 from USB by following the steps found in 
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
After installation is completed successfully, I am seeing that it is trying to get access USB while booting, (I installed completely, it was not a live USB, and also this is coming after changing the boot options to Hard Disk as well). 
USB is required only for the starting time of OS.
So I am suspecting do I need to copy some startup files somewhere?

Any help regarding this is really appreciated.

Regards,
Mayukh

---

### Post by black veils on 2012-07-11
the only suggestion i can give, is to use [this]("http://unetbootin.sourceforge.net/") for creation of bootable usb flash drive instead.



[]("http://unetbootin.sourceforge.net/")

---

### Post by oldfred on 2012-07-11
Grub usually defaults to installing the boot loader to the MBR of sda or the first drive which usually is the hard drive. But a few BIOS make the flash drive first and then grub installs the boot loader to the flash drive.

If you can boot.

Confirm that normal boot, that hard drive is sda

sudo fdisk -lu

sudo grub-install /dev/sda

But grub remembers where to reinstall on major grub updates, so you should also update that:

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by aecs1234 on 2012-07-12
Thank you all. After creating the bootable USB using Ubuntu's usb-creator-gtk, my issue got resolved.

---

