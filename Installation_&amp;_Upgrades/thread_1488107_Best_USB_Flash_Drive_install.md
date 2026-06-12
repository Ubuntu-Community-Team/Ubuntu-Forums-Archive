---
title: "Best USB Flash Drive install"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Nightshade69 on 2010-05-19
I plan to install Ubuntu 10.04 to a flash drive and I would like to know the best way to do so, i have found about three or four ways to do so and I would like to know the best.

---

### Post by wojox on 2010-05-19
Are you currently running Ubuntu? If so the application Start up Disk Creator works well.

If not [UNetbootin]("http://unetbootin.sourceforge.net/") is my other favorite.

---

### Post by CDennis on 2010-05-19
Hi. I'm running 10.04 on an Attache 8GB flash. I think smaller than 8GB would work but be a little confining.
I put the pen drive in the usb port, the install disk in the cd and chose the usb pen drive as the target. 
I went with ext 4 though some say a journaling file system causes more writes - slower more wear and so not a good choice for a pen drive.
On the last step before install choose the advanced option button and put the Grub loader on the pen drive NOT the hard drive of your pc.
Hope this helps. It's fun to do as thumb drives are so cheap now; it will take longer to install as large writes will be slower than to a main hd.

-DJ

---

### Post by Nightshade69 on 2010-05-19
Thanks all i have heard of all of those. I know all are easy, I was just wondering if any were better than others, and if it is possible to use it for normal storage after the install.

---

### Post by C.S.Cameron on 2010-05-19
Best is relative to your needs.
If you plan on installing 10.04 LTS for the long term a "Full" install will let you update and upgrade as desired. With this method disable your hard drive, plug in the flash drive then boot the Live CD and run install. A 4gb flash drive is minimum. If heavily customized with proprietary drivers it may not work on every computer.  

A persistent install, (usb-creator), is not lacking much but you can't upgrade the kernel, and out of the box persistence is limited to 4GB.
Both usb-creator and UNetbootin disk image installs can be made to work with persistent partitions, (casper-rw and home-rw). these aren't limited to 4GB and you can usually upgrade Ubuntu versions without loosing much.

A grub2 iso install is similar to the above disk image install. you can put multiple bootable iso's on the drive and use persistent partitions also. It is real easy and fast to delete an old O/S version and add a new one. Works with Ubuntu, gparted and many more.

There is some controversy about which method or file system is fastest.

You can use each method for normal storage, for the full install leave a FAT32 partition as the first partition, for a persistent install make the fat32 partition larger than required for the O/S and save stuff to the cdrom folder. The iso install is basically FAT32 so saving stuff is also not a problem.

---

### Post by Nightshade69 on 2010-05-19
Thank you C.S. Cameron, you helped a great deal. I'm going to have to take a little while to decide though.

---

