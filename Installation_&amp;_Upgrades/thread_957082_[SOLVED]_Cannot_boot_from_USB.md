---
title: "[SOLVED] Cannot boot from USB"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Firestrider on 2008-10-23
So I installed the latest Daily_Live_x64 from unetbootin and installed it on my USB drive for a live USB and it won't boot from it once restarting. Is there a problem with the MBR or something? I have the boot priority in BIOS to removable -> cdrom -> hard drive.


Also what is the best way to set up the partitions for ubuntu regarding the size for /boot swap space /root and /home? I have 2 GB of RAM and usually install more applications (more space) than multimedia content

---

### Post by C.S.Cameron on 2008-10-23
Can your computer handle 64 bit, maybe try the i386 version.
Is your flash drive set as the first hard drive in BIOS? If not do so in hard disk priority.
If you are using the Unibootin install, it is not persistent, you can not save changes.
Usb-creator will make a persistent install but you will not have much room for upgrades on a 2G flash. you can make partitions labeled casper-rw and home-rw on a separate drive.
usb-creator can be found in 8.10 under System as "Create a USB startup disk".
A 4G flash drive will give you enough room to make a full install using installer on the Live CD, (or installer on your current USB).
You can set up your partitions using manual partitioning during setup.

---

### Post by Firestrider on 2008-10-24
Hi, yes I do have a 64-bit processor, it is a X2 4000+. The hard drive I want to install Ubuntu on is 320GB. I'm just wondering what sizes I should make the partitions. I heard that /root is more for applications and /home is more for music/pictures/movies; since I use more application space than multimedia space should I make /root bigger? Also what size should I make /boot and the swap space, 500MB and 2GB respectively? What file system?

I'm using Windows Vista right now and I want to create a Live USB within Windows, so I'm using Unetbootin. Do you know of a better program to make Live USBs within Windows?

---

### Post by Firestrider on 2008-10-24
Ok thank you, I got it to work. I guess the USB was recognized as a hard drive in BIOS. I booted from the "removable" from Live USB when I had PATA hard drives, but now that I have a SATA I guess it changed.

---

### Post by C.S.Cameron on 2008-10-24
Doesn't sound like your system needs much swap, you could leave 2G but will probably never use it.
10G of root should last quite a while
Home can get filled up quickly if you got lots of photos or movies,
I don't use a boot partition myself.
Ext3 is normal for home and root, reiserfs is said to be a bit faster if you have a lot of small files, I've tried it and like it.
Whatever sizes you choose you can easily adjust later using gparted.
Unibootin is great for making a Live USB from Windows.

---

