---
title: "Reformat Windows, keep GRUB"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by Stealth on 2005-05-01
I plan on reformatting Windows soon, but I have it on a dual-boot with GRUB, so I'm pretty sure on the reinsallation of Windows its gonna replace the bootloader. How can I save or do something with grub, so I can reinstall it and keep everything normal?

---

### Post by dave9191 on 2005-05-01
Windows is going to be really nice and annoying for you. Its going to write to the MBR and overwrite grub for you. You will have to boot up a live cd and install grub into the MBR afterwards. Since the config files for grub are kept on the boot partion they wont be deleted. You will have to know what partion you boot partion is when you install grub into the MBR again. The Gentoo handbook descibed how to install grub, and Im sure that youll find something about it on these forums somewhere. 

Dave

---

### Post by nad on 2005-05-01
Good advice in post#2.

You could also try the ubuntu package 'bootcd' available in universe and use this as a rescue cd. It will "Copy your running Debian System on CD with the command bootcdwrite".

---

### Post by az on 2005-05-01
You can boot the Ubuntu install cd, (CTRL_ALT_F2), mount the partition (look in /dev since your partition wil have a devfs name - use tab completion) and chroot into it.  Then do a 
grub-install /dev/(whatever...)
 
Easy.

---

### Post by Stealth on 2005-05-04
What exactly would I do?

mount /dev/hda1 /mnt/hda1
grub-install /mnt/hda1 ? That simple?

---

### Post by T. G. Cid on 2005-05-05
Personally, I recommend letting Windows have it's way:

Pre-install run the command:

dd if=/dev/hda of=/tmp/ubuntu.bin bs=512 count=1

This will copy the first 512 byte block (ie Master Boot Record) into a file called ubuntu.bin.  Transfer this file (probably via floppy) to your C:\ of your new Windows install.

Then run notepad C:\boot.ini

You should see something like:

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

change this to:

[boot loader]
timeout=**1**
**default=C:\ubuntu.bin**
[operating systems]
**C:\ubuntu.bin="Ubuntu GRUB"**


Windows will load it's boot loader which immediately loads GRUB.

---

