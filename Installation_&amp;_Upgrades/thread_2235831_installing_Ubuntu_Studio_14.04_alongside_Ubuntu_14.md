---
title: "installing Ubuntu Studio 14.04 alongside Ubuntu 14.04"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by pieter512 on 2014-07-23
Hello

I have Ubuntu installed on an external hard disk for quite some time now, and I wondered if it was possible to have a hard disk with both Ubuntu and an Ubuntu flavour, like Ubuntu studio.
I deleted my ntfs partition, and made it a new smaller ntfs partition and an ext4 partition. I didn’t change my Ubuntu 14.04 ext4(extended) and swap partitions.
Then I ran the Ubuntu Studio installer from a usb flash drive, and chose ‘something else’ for the install location. I selected my new ext4 partition, ‘use as ext4 logging file system’, checked the format box, and set ‘mount point’ to ‘/’.
After the install was completed, and I tried booting from the hard drive, but there wasn’t an option for Ubuntu Studio… (it only showed ‘ubuntu’, this was my first partition, ‘Ubuntu 14.04’ and ‘windows 8 loader’, those last two options are installed on my internal hard disk.)
Gparted shows that there is 6GB used on the partition, and the flag is 'boot', so I guess it did install Ubuntu Studio?
[ATTACH=CONFIG]254943[/ATTACH]

Is there a way to get this working without reinstalling my existing Ubuntu 14.04?

Thanks in advance
Pieter

---

### Post by yancek on 2014-07-23
You either installed the Grub bootloader for Ubuntu Studio to the / partition on which it was installed or to the master boot record of sdb.  Since you can apparently boot Ubuntu and windows (??) just boot Ubuntu and make sure your external is attached and run:  sudo update-grub, then watch the output to see if Ubuntu Studio is detected.  If it is you should have it in the menu when you reboot.  if you have a problem, post back with details on what happened.

---

### Post by pieter512 on 2014-07-23
Yancek, thank you for your reaction,

this was the result of the update-grub:

```
Grub-instellingenbestand aan het maken...
Linux-image gevonden: /boot/vmlinuz-3.13.0-32-generic
Initrd-image gevonden: /boot/initrd.img-3.13.0-32-generic
Linux-image gevonden: /boot/vmlinuz-3.13.0-30-generic
Initrd-image gevonden: /boot/initrd.img-3.13.0-30-generic
Linux-image gevonden: /boot/vmlinuz-3.13.0-29-generic
Initrd-image gevonden: /boot/initrd.img-3.13.0-29-generic
Linux-image gevonden: /boot/vmlinuz-3.13.0-24-generic
Initrd-image gevonden: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Ubuntu 14.04 LTS (14.04) gevonden op /dev/sda1
Windows 8 (loader) gevonden op /dev/sdb3
Ubuntu 14.04 LTS (14.04) gevonden op /dev/sdb4
voltooid

```

(I'm sorry, it's in Dutch... 'gevonden' means 'found', 'op' means 'on', 'voltooid' means 'completed, finished', and 'Grub-instellingenbestand aan het maken...' means something like 'Creating Grub-configuration file...' )

Restarted my pc, booted from external hdd, now I have these options:

```
Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu 14.04 LTS (14.04) (on /dev/sda1)
Advanced options for Ubuntu 14.04 LTS (14.04) (on /dev/sda1)
Windows 8 (loader) (on /dev/sdb3)
Ubuntu 14.04 LTS (14.04) (on /dev/sdb4)
Advanced options for Ubuntu 14.04 LTS (14.04) (on /dev/sdb4)

```

Now there are 3 Ubuntu 14's, tried the last one, since sdb4 was the partition on which I installed Ubuntu Studio, and it worked!

Is there a way to rename this boot option, or set it as default?

Thanks for your advice
Pieter

---

### Post by yancek on 2014-07-23
To set the Ubuntu Studio entry to boot as default, count the menuentries on the boot menu.  In your last post it is entry 9, verify that so you would put 8 in the line below in the /etc/default/grub file.  In this situation, Grub counts from zero:

> GRUB_DEFAULT=8

In the /boot/grub/grub.cfg file you will see a number of menuentry items.  What is shown in quotes immediately after menuentry and before the firs { symbol is what you see on the menu.  Since this file is updated anytime you update-grub, changes should not be made directly in grub.cfg so the simplest thing to do is copy the entire menuentry into the /etc/grub.d/40_custom file, save and then run sudo update-grub.

---

### Post by pieter512 on 2014-07-25
Everything is working fine now, thanks a lot!

---

