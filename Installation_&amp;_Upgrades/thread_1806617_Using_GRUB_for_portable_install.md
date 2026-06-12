---
title: "Using GRUB for portable install"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by ManualSparrow on 2011-07-17
Hi, 

I've been using an external USB hard drive for backup and extra storage, but it seems like a good idea to make it a rescue drive as well. Rather than use one of the PenDrive linux tools (like [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)) or the Ubuntu Startup Disk Creator, I'd like to install directly onto the device, mainly because I don't want to format all of the partitions I have and want to use an ext4 partition rather than FAT32.

My question is:
After I specify the OS partition I set up on my external for my install point and point GRUB at the MBR of the external drive, will GRUB always be able to find my installation, or will I have to run probe every time I go to a new computer? I probably won't use GRUB on the external to boot OSs on the internal drive very often, so am not worried about that aspect of the setup. 

Thanks.

EDIT: It remembers the Device ID.

---

