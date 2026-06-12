---
title: "Problems unmounting partitions with gparted"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by gibxam on 2011-06-03
Hello,

I'm trying to delete my /dev/sda1 partition which currently has 32bit Ubuntu 10.04 on it so that I can install 64bit 10.04. I created a bootable usb drive and booted it up. I then opened up gparted to delete the partition but I can't because it won't let me unmount it first. I see from the error message ```
 umount: /cdrom: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1)) 
``` and from the key symbol in gparted (see attached picture) that the partition is currently being using. I don't understand how it could be in use since I'm booting from the usb drive. The command ```
 fuser -c /cdrom/ 
``` returns nothing. I'm completely stumped as to how to figure out which processes are using the partition i'm trying to delete or cdrom. I have to say this is a bit of a bummer since I've repartition my laptops or desktops dozens of times and have never run into a snag like this. any help would be much appreciated.
[IMG]http://img685.imageshack.us/img685/2640/screenshotkl.png[/IMG]

---

### Post by tommcd on 2011-06-03
You do not have to delete your 32bit Ubuntu on /dev/sda1 to install 64bit Ubuntu.
When you install 64bit Ubuntu, just choose manual partitioning, and choose to install the 64bit Ubuntu right over the 32bit Ubuntu. Be sure to select to format the /dev/sda1 partition and choose the mount point 
/ (root) for /dev/sda1 for your 64bit Ubuntu.

Do you have a separate /home partition? If not, you will need to backup any data before reinstalling Ubuntu. This would be a great time to create a separate /home partition if you don't already have one.

If you do have a separate /home partition, then choose mount point /home for that partition and select *not* to format that partition.
Your current swap you can leave as swap.

---

### Post by gibxam on 2011-06-03
the problem was that I orginally was too lazy to make a usb bootable so i used unbootin (or some other name I forget) but bottom line is that the program made it so I couldn't unmount the partition, I just unistalled unbootin and now everything is working and I'm running a spiffy new 64 bit version of the lts

---

