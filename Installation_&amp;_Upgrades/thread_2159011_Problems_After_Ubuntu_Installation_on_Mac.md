---
title: "Problems After Ubuntu Installation on Mac"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by promac123 on 2013-07-01
I recently tried to install Ubuntu on my iMac, using the latest version of OS X and Ubuntu (13.04). I downloaded rEFFIT and burned the .iso onto a CD. I forgot to make the partition before rebooting with the disk. I chose the install Ubuntu instead of to try Ubuntu. I have two hard drives. One is a 251 GB SSD and the other is a 2 TB SATA. I chose the second as the swap area. I really don't remember which one I chose to install Ubuntu on. After it was finished, I rebooted and it went into some OS X Utilities page instead of Ubuntu. The options included restoring from a Time Machine, Reinstalling OS X, the Disk Utility program, and getting help online. When I try to reinstall OS X, it only shows the Recover HD, which I cannot reinstall OS X on. My two hard drives don't show up there. I put the CD in and restarted while holding C. When I got to the install place, it said that I don't have any OS on the system. I installed it and restarted holding C again. Now it says that I have Ubuntu on the system, but whenever I restart, it goes into the OS X utilites page. Also, when I go to install Ubuntu and I get to the Installation type page, (where you partition stuff) my SSD shows up as /dev/sdb as the device, but everything else is blank. Instead of saying the type (swap, efit, etc...), size, used, and system, it's just white space.

Thanks in advance,
Whatever I Made my Name on This Forum Be

---

### Post by buzzingrobot on 2013-07-01
It appears OS X is no longer available and the machine is offering you the recovery option via the hidden recovery partition.  If you used one of two drives for swap and the other for the Ubuntu install, without resizing the OS X partition to free space for UBuntu, then OS X is gone 


Use the partitioner in Disk Utility to remove the Ubuntu partitions, create new partition(s) for OS X. Quit Disk Utility and you should be able proceed with the recovery.

---

### Post by promac123 on 2013-07-01
I think when I checked, there were no partitions. I forgot to make partitions before. About the OS X being gone, I know that, but I don't think I can get it back if it's gone. More detail about how to create a partition specifically for OS X would be nice.

Thanks,
promac123

---

### Post by buzzingrobot on 2013-07-01
Her's an Apple link on Disk Utility: [http://support.apple.com/kb/PH5845?viewlocale=en_US](http://support.apple.com/kb/PH5845?viewlocale=en_US).  Another link from a third-party source: [http://pondini.org/OSX/DU.html](http://pondini.org/OSX/DU.html).

The last few iterations of Mac hardware -- the ones that don't come with DVD's to install OS X -- include a hidden recovery partition on the drive. When activated, it displays the menu you mentioned, and also puts Disk Utility and a few other tools up in the menu bar.

On my Macbook, holding Command-R down as the machine boots will bring up the Internet Recovery option. Eventually.  It takes a minute or more here. It will download OS X and install it on the drive.  However, if it does not find a drive with an Apple partition, it will fail.  That's why Disk Utility is provided. Use it to make a new partition for OS X, then quit Disk Utility.  You'll be returned to the Recovery option, which should then go ahead and finish. It takes 40-60 minutes here.  The version of OS X that was on the machine when it was sold, not the version it may have been upgraded to, will be installed.

When I've done this, I've partitioned the entire drive in the Macbook for OS X.  Then, after it's reinstalled and all is well, I use Disk Utility to shrink that partition to make room for another (attempted) Ubuntu installation.

---

