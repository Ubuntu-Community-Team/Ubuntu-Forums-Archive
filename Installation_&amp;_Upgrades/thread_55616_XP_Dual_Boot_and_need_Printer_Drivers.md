---
title: "XP Dual Boot and need Printer Drivers"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by RaY2DaY on 2005-08-09
Hi All,

As a newby to Ubuntu & Linux I decided to take the plunge after being mightily impressed with open source from the [Smoothwall](http://www.smoothwall.org) firewall side.
Installed Ubuntu on a second 20 Gig HDD and all went well, no problems on install whatsoever. I was impressed for a newbie - installation was pretty easy and not too confusing despite the multitude of lines scrolling by....!!
Even more impressive was the automatic LAN detection to the point where I am able to "see" the other computers on the network.

I do however require help with a few items:

Firstly, the boot up screen when the computer is started has Ubuntu as the default OS to boot to, can this be changed to XP Pro? In other words I would like XP Pro on my primary HDD to be the OS the system boots into if I don't make a choice on start up.

Secondly, I have the following printers on the network:- HP 6213 Officejet All-in-One - How do I get this recognised for both printing and scanning - I have used the default 6200 driver provided and printing is great, it just doesn't recognise the scanner. In additio I have the following printers: Canon LBP800 - no drivers provided, can someone point me to a site that would have drivers, and the same for an Epson Stylus Color 440.

Thirdly when in Windows XP Pro I am unable to see the second HDD no that Ubuntu is installed - how can I change this so that I can swap files between the two drives. In the same vein when in Ubuntu I am unable to see the Win XP drive which is partitioned into 3, therefore C drive (OS & system files), D drive (Documents etc) and E drive (swap file).

All assistance is greatly appreciated.

RaY2DaY

---

### Post by blastus on 2005-08-09
I'm a newbie also and struggled with these same issues at one time. I can't help with the printer (as I have printer problems also...some applications don't print others do!?) but I can give you an overview of what you need to do for the other issues. Then a Linux wizard can fill in the details.

> Firstly, the boot up screen when the computer is started has Ubuntu as the default OS to boot to, can this be changed to XP Pro? In other words I would like XP Pro on my primary HDD to be the OS the system boots into if I don't make a choice on start up.

You can edit the "/boot/grub/menu.lst" file to change the default OS that is booted. To edit the file enter (in a terminal window):

sudo gedit /boot/grub/menu.lst
<then enter your password that you login to Ubuntu with>

You'll need to find the line in that file that says "default 0" or something like that. The first item in the menu is 0, the second is 1 and so forth. You'll need to study the file a little (and perhaps others can fill in some more details for you) to find out what the menu number is. On my machine I think it is 3 so in my file I have the line "default 3."

> Thirdly when in Windows XP Pro I am unable to see the second HDD no that Ubuntu is installed - how can I change this so that I can swap files between the two drives. In the same vein when in Ubuntu I am unable to see the Win XP drive which is partitioned into 3, therefore C drive (OS & system files), D drive (Documents etc) and E drive (swap file).

First off I would recommend that you read up on the MBR (Master Boot Record), partitions, GRUB (the boot loader for Ubuntu and other lInux distributions), and the way the Linux file system is organized. It helped me enormously to understand some of these basic things at least on the surface.

Linux can't read Windows NTFS partitions right out-of-the-box and Windows XP can't read Linux ext3 partitions (or any kind non-Windows partition for that matter.) This is why Linux can't see your Windows partition and Windows can't see your Linux partition. However, Linux can read/write FAT32 partitions. So if you want to share data between Linux and Windows, you need to have a FAT32 partition somewhere in your system. If your Windows partition is FAT32 then you can see it in Linux by "mounting" it.

Windows will automatically see FAT32 partitions. To get Linux to see a FAT32 partition you need to "mount" it in Linux. This is easy to do if you know how the Linux file system works, what it means to "mount" something and how hard drive partitions work in Linux. You may want to read up on this stuff first and save yourself countless hours of frustration like me when I first tried to do that. It's just that you need to understand these concepts first.

You may have to reinstall everything from scratch and plan out how you want to partition everything to allow for a FAT32 partition (if you don't have any FAT32 partitions anywhere on your system.) You can resize partitions with special tools and even install special software on Windows to read ext3 or on Linux to read NTFS but I wouldn't recommend any of this to a newbie (and I certainly am a newbie!) The best way is to start from scratch and plan things out. If you are only running Windows XP and Ubuntu and have two hard drives (I assume they are EIDE) then I would recommend the following plan:

Primary Master (called /dev/hda in Linux):
- partition 1: install Windows XP on this partition (can be FAT32 but I would recommend NTFS so Linux can't see it)
- partition 2: install Ubuntu on this partition (should be ext3)

Primary Slave (called /dev/hdb in Linux):
- partition 1: format as FAT32

Then to mount the FAT32 partition in Linux you would enter something like:

sudo mkdir /mnt/backup
sudo chmod a+rw /mnt/backup
sudo mount -t vfat /dev/hdb1 /mnt/backup

Now your FAT32 partition is contained with the /mnt/backup directory in Linux. The above syntax may be incorrect or a little different for your system. Finally, to have Linux automount /dev/hdb1 everytime you boot, you need to edit the /etc/fstab file and add the appropriate entry. I don't have time to explain everything but maybe someone else can come in and fill in the details.

Also the commands "sudo fdisk -l" and "sudo mount -l" are very useful for looking at your partitions and what is mounted. By the way, don't be confused by the "sudo." It just means that you are telling Ubuntu to run the command as root. The root account is similar to the "administrator" account on Windows XP. You can do everything as root. But in Ubuntu, you cannot, by default, log in as root. So you need to prefix everything you type in with "sudo" to do things as root..

---

### Post by yellowband on 2005-08-09
thanks for that blastus, i was wondering the same thing. One detail that concerns me is the file size limitation that FAT32 has.  What is it exactly? i wonder because i plan to record large shows / rip DVD's with linux, but i want to see them in windows XP as well.  i wouldn't be able to put these larges files onto the FAT32 drive, and thus would not be able to see them in windows, right?

---

### Post by blastus on 2005-08-09
FAT16 has a 2Gb limit. Older versions of Linux (I believe Red Hat 6 or something like that) only supported FAT16.

FAT32 has a 32Gb limit. But my computer came with XP on it and I believe it was originally FAT32 (I've since partitioned the drive and reinstalled XP several times) and it was way more than 32Gb so I'm not totally sure on the FAT32 size limit. I do know that you cannot create a FAT32 partition larger than 32Gb when you setup Windows XP. So you may need to create multiple partitions if larger than 32Gb but you really only need one FAT32 partition to share data.

There are special drivers (or software) to get Linux to read NTFS or Windows to read ext3. Personally I would never use them. I have a hard enough time just trying to understand the basics to be messing around with that kind of stuff.  ](*,) I like being able to do stuff from an out-of-the-box installation as much as possible and not rely on esoteric or difficult setup routines to keep things as simple as possible. :wink:

---

