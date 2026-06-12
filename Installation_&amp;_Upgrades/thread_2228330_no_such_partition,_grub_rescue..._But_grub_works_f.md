---
title: "no such partition, grub rescue... But grub works fine through easyBCD"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by azibux1 on 2014-06-06
Hi all,

First post here so hope this is in the correct place

I have a bit of Linux use/knowledge, but not so much when it comes to GRUB

I installed a second hard disk drive in my laptop (in replace of the optical drive), I've installed Windows 8 on one drive and on the other I'd like:

- NTFS Partition for files (for windows)
- An Ubuntu 14.04 install

I have created two partitions for the ubuntu install, one 4GB for SWAP and one 50GB for the rest. I have installed it and stated that I want the 4GB for SWAP and the rest is formatted at Ext4, and I put the mount point as '/'. I set "device to install bootloader installation" as the 50GB drive/partition.

Now when I had this all setup on one drive, I was able to boot up, it goes straight to grub and I would choose ubuntu or windows 8. Now it is on two drives (all reinstalled as mentioned above), it would only boot into Windows. I'd switch the BIOS boot order to check the linux drive first and I'd get the error about "error no such partition", and it would go to a grub rescue command line style interface.

The thing is, through windows, I installed easyBCD and told it to add a second boot option to the windows boot options for ubuntu and I specified the partition (the 50GB one), it shows up fine in Windows boot options, if I select ubuntu the computer will restart, go through POST again and THEN goes to grub which works fine.

What I'd like to do, hopefully with the help of some people here with advice, is to get it to go to grub initially and completely avoid the windows boot options as it seems unnecessary as it then reboots and goes through POST again/BIOS splashscreen, then goes to GRUB anyway

Does anyone know how I can do this please?

Hope someone can help, :)

Thanks!

---

### Post by oldfred on 2014-06-06
You normally install grub to the MBR or if second drive sdb, not sdb1 or a partition.
EasyBCD uses a partition to boot from, but with two drives you can keep the Windows boot loader in sda, and have grub in sdb. Grub will then find Windows and let you boot it also.

Grub has remembered where you installed. So on a major update it will reinstall there. You need to update that as well.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

If you run the dpkg command you do not need to run the grub-install as it is included in eh dpkg command.

---

### Post by azibux1 on 2014-06-07
Thank you!

I will bear it in mind for future, but this time, just in case I do that above process wrong, to avoid possible issues in the future I just reinstalled ubuntu instead (as I hadn't set it all up yet anyway), and this time I installed the bootloader in the correct place like you say, on the drive rather than the partition and it all works exactly like I want it to

Thanks :)

---

