---
title: "Deskto launchers don't work with USB drive"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by wyhog on 2010-05-04
Upgraded from Ubuntu 9.10 to 10.4 yesterday on my Dell desktop. 

I get Permission Denied errors when a python script and other programs pass a filename (or directory) that is located on a USB hard drive. For instance a desktop launcher with the simple command:
nautilus
when doubleclicked will start nautilus and I can then display-access-read-write any files on my USB hard drive named "S", no problem. (The USB HD is FAT32).
But if I create a launcher such as:
nautilus /media/S
when doubleclicked it gives a permissions denied.
The same thing happens when I try to use a launcher to run a python script which passes a path/filename argument where the argument is located on the USB hard drive "S". The python script runs but gets a permission denied error when it tries to access the argument file on the USB HD.

However both of the above examples work fine if the files or path is located on a USB memory card (named "R" and shows FAT12) instead of the USB hard drive. In other words, a desktop launcher such as:
nautilus /media/R
works fine. But:
nautilus /media/S
does not.

My several launchers and scripts worked fine on the USB "S" drive for a year before I upgraded to 10.4. If I check the properties and permissions of the USB hard drive it says that I am the owner and have Read/Write permission and I can do that, but my launchers can't. How can I get these launchers to work again.

Other upgrade problems:
1. After upgrade 10.4 would not boot. I fixed that by live booting the 10.4 CD and using a terminal to fix grub.
2. No sound. I fixed that by deleting the pulseaudio directory in my  home directory.

Wyhog

---

