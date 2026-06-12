---
title: "Difficulty getting grub to install correctly"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by jabalsad on 2010-08-01
Hi all,

Im having a hard time getting grub to load correctly. Here is my setup:

I have a single hard drive that already has Windows 7 Installed on a 40gb partition. Windows automatically creates a 128mb boot partition as well. I then ran the Ubuntu alternate install from a USB flash drive and encrypted the remainder of the hard drive. I created a logical volume group inside the encrypted portion and divided it into three logical volumes: one for the OS, one for swap and the rest for storage.

Initially, when it got to the "install grub" stage it failed because it looked like it was attempting to install grub on the usb flash drive (/dev/sda). I then rebooted and performed the installation again, except this time round i marked the 128mb windows boot partition as /boot. The "install grub" stage succeeded, however I get a "Missing operating system" message on boot.

Please assist me in getting this setup right, it will be much appreciated.

---

### Post by TheHimself on 2010-08-01
When you get the message type
```
grub
```
and see what you get. Are you using Ubuntu 9.1 or higher (i.e. grub2)?

I'd say you  use a small linux distro like puppy linux to install grub and edit partitions. It's small ans so saves you some time.  I have it installed on a small partition so no need for a USB drive. (You can do this after you get your computer to work.)

---

### Post by oldfred on 2010-08-01
The windows boot partition is not a boot partition you can use for any other system. For most desktop users (only those real old systems with BIOS limits may need it) you should not even create a separate /boot.

---

### Post by jabalsad on 2010-08-02
oldfred, well where would you put the boot loader if the root filesystem is encrypted?

In the end I reformatted the entire PC with three partitions: Windows, Boot loader and an encrypted LVM for ubuntu. Grub now successfully sees both Windows and Linux, though I'm still not sure how one would achieve this if you already had a working OS and didnt want to lose your data.

---

