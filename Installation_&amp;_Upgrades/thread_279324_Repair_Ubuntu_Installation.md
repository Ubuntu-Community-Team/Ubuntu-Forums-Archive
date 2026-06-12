---
title: "Repair Ubuntu Installation"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by cmeek on 2006-10-17
I installed Ubuntu a couple of weeks ago and all was well. This was setup to dual boot with Windows.

A few days ago I decided to also try an install of Suse Linux alongside my Windows and Ubuntu installation. This initially messed up my multi-boot in that Suse's multi-boot program took over and failed to recognized that I already had Ubuntu installed. I finally fixed this by reinstalling Grub from the Ubuntu Live CD and adding Suse to the list of OSs.

However, now my Ubuntu will not boot. Both Suse and Windows will boot fine, but when I try to start Ubuntu it fails. I get the usual messages about decomressing the kernel and a few other messages, then the error messages start. It tells me that /etc/fstab does not exist. Then it cannot mount several locations like sys and proc (if I remember correctly). It appears that it is getting at the kernel, but for some reason does not have the drive mounted correctly.

If I boot up the live CD and mount the drive with the Ubuntu installation I can clearly see the /etc/fstab file. And everything else seems to be intact.

What settings or files or commands should I try to see if I can get this fixed without having to fully reinstall?

---

### Post by cmeek on 2006-10-18
No answers yet, so how about I provide a little more informatio...

When I select Ubuntu to load from my Grub menu I get the Ubuntu splash screen and at the bottom a couple of messages. Loading drivers I think is the first one which indicates it is OK. Mounting Root Filesystem is the second one, it never indicates success or failure and after a moment drops me to a text screen with a bunch of messages.

The first indication that something is wrong is a message that is giving the usage parameters for modprobe.
After that it seems to be attempting to mount the partition and gives me an arror that /etc/fstab does not exist.
This is followed by errors that it cannot mount /sys and /proc.
Eventually I get a Busybox prompt.

As I said in my first message, I can boot the live CD and mount the Ubuntu partition and everything seems to be there including the /etc/fstab

Anyone have any sugestions on what to try?

---

### Post by taurus on 2006-10-18
If you install GRUB from Ubuntu, then let's have a look at your /boot/grub/menu.lst and your /etc/fstab as well...

---

