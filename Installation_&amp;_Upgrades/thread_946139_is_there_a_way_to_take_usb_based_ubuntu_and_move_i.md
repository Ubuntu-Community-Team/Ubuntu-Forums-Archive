---
title: "is there a way to take usb based ubuntu and move it to hard drive"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by mjlee105 on 2008-10-13
Wondered if once I had move ubuntu to a pen usb flash drive, if you could reverse the process and take it to a non ubuntu system and install it, without the cd.

---

### Post by caljohnsmith on 2008-10-13
If you installed Ubuntu to a USB flash drive, and it works on the "non-ubuntu system" you are referring to, then it would be easy to transfer it to that computer's HDD and get it working. Although you could clone the partition from your USB over to the computer's HDD, that can be tricky unless you set up the exact same size partition on your HDD to clone it to. I would simply copy over the entire Ubuntu file system from the USB to the HDD using "cp -ax", and then all you need to do is modify your /etc/fstab and your /boot/grub/menu.lst to use the new UUIDs for your new Ubuntu partition and probably your new swap partition too. That's the general idea, but if you want more details of the exact procedure, please first post:
```
sudo fdisk -lu
```
With your USB drive connected to the computer where you want to copy it to.

---

### Post by C.S.Cameron on 2008-10-13
I just got a Flash drive how I want it.
Booting from the Live CD I used 
sudo dd if=/dev/sd? of=/dev/sd?
(confirm /dev/sd? before proceeding).
to clone the o/s to a second Flash Drive.
This worked great.
Then I used the above to clone to a HDD.
This also worked.
I then used gparted Live CD to expand partitions.

---

