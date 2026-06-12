---
title: "ubuntu usb to ram"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by jv13613 on 2008-10-15
Hi,
  I was wondering if if would be possible to have a live usb that would copy system to ram. Then on shutdown copy it back to usb drive. It could save all ststem changes. Thanks ahead of time!

---

### Post by kerry_s on 2008-10-15
only in a distro made to do that.

[http://distrowatch.com/search.php?category=USB+drives&origin=All&basedon=All&desktop=All&architecture=ix86&status=Active](http://distrowatch.com/search.php?category=USB+drives&origin=All&basedon=All&desktop=All&architecture=ix86&status=Active)

---

### Post by snowpine on 2008-10-15
There are 2 different ways to run Ubuntu from a USB stick. One is to install it just as you would to a regular hard drive. This type of install is fully persistent (all your changes are automatically saved) and is quite easy. I have tried this myself and it works very well. The downside is you need at least a 4gb stick.

The other method is to create a Live USB install, either with or without persistence. I have never tried this method personally, but I believe there are tutorials on pendrivelinux.com. Disk usage is less than 1gb (about the same size as a live CD).

I also use a distro called SliTaz that has excellent tools for running from a live USB. The advantage is that it uses much less disk space than Ubuntu, so you actually have space on your USB stick for your personal data.

---

### Post by kerry_s on 2008-10-15
> **snowpine said:**
> There are 2 different ways to run Ubuntu from a USB stick. One is to install it just as you would to a regular hard drive. This type of install is fully persistent (all your changes are automatically saved) and is quite easy. I have tried this myself and it works very well. The downside is you need at least a 4gb stick.

The other method is to create a Live USB install, either with or without persistence. I have never tried this method personally, but I believe there are tutorials on pendrivelinux.com. Disk usage is less than 1gb (about the same size as a live CD).

I also use a distro called SliTaz that has excellent tools for running from a live USB. The advantage is that it uses much less disk space than Ubuntu, so you actually have space on your USB stick for your personal data.

he wants "--toram" from the usb. ubuntus not made for that.

---

### Post by jv13613 on 2008-10-15
I was thinking that i would use the boot to ram tutorial. [https://wiki.ubuntu.com/BootToRAM]("https://wiki.ubuntu.com/BootToRAM") Then make a script to copy contents of tmpfs to a partition on the usb stick. Have grub on usb stick and have entry.

From tutorial
Ok, the last thing we need to do is tell GRUB how to boot this system. Edit /boot/grub/menu.lst to include an entry like this at the bottom:

title Feisty RAM Session
root (hd0,0)
kernel /casper/vmlinuz boot=casper splash
initrd /casper/initrd.gz

Of course, replace (hd0,0) with the correct device that contains the /casper directory. 

I think this is possible

---

