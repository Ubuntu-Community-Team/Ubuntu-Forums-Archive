---
title: "USB Boot"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by sonny on 2008-08-26
Hi, I'm doing an uncommon install and I need some help, here's the thing... I have a new HP dv6700 laptop with Vista in it, and I want to dual boot with Ubuntu 8.10, but the thing is that I want to boot it from a usb pendrive.

What I want is this: If some else boots up the laptop without MY usb pendrive then it should load directly to Vista but if I put the usb drive BEFORE turn it on, then it should load directly to Ubuntu (Yes, my laptop supports booting from a usb).

I read some of the posts in the forums about grub usb, but I don't want just grub in it, I want the whole /boot in the usb, I thought it'd be easy, so I installed Ubuntu and manually configured the partitions, so I selected my usb /dev/sdb1 as my /boot partition, which makes sense, but then it gave me an error just when it was 99% of the installation, and Ubiquity closed inexpectedly fast and couldn't see the error, the result was that it didn't installed the /boot files in my /dev/sdb1 therefore leaving me without my ubuntu.

My question is... How can I make this configuration to work as it should? Any thoughts?

---

### Post by ajgreeny on 2008-08-26
I don't know if this will help if you change various parts of the sequence to point to your usb drive, but it is possible to put /boot onto a floppy with the following commands.

sudo mkfs /dev/fd0
sudo mount /media/floppy0
sudo mkdir -p /media/floppy0/boot
sudo cp -r /boot/grub /media/floppy0/boot
sudo umount /media/floppy0

Perhaps worth a try.

---

### Post by sonny on 2008-08-26
> **ajgreeny said:**
> I don't know if this will help if you change various parts of the sequence to point to your usb drive, but it is possible to put /boot onto a floppy with the following commands.

sudo mkfs /dev/fd0
sudo mount /media/floppy0
sudo mkdir -p /media/floppy0/boot
sudo cp -r /boot/grub /media/floppy0/boot
sudo umount /media/floppy0

Perhaps worth a try.

That didn't help... I guess I should do a normal install and then change the /boot partition because I've found many how-to's for that matter. Any other ideas?

---

