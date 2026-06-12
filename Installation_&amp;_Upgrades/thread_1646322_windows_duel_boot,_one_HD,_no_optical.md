---
title: "windows duel boot, one HD, no optical?"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by hetkat on 2010-12-15
Hi,

I am pretty new to ubuntu, I have a machine without an optical drive booting meerkat from the only partition on the only disk. I would like to move from this situation to duel booting with windows 7. Can anyone advise on general strategy/path for achieving this? In particular addressing the following:

1) Can I unmount the partition that ubuntu is running off in order to repartition the disk? If not (how) can I partition my OS boot disk?

2) Is there any way to install windows onto a clean partition using the windows disk ISO from within ubuntu? Could I perhaps somehow mount the ISO as a drive then use Wine to run the windows installer? Would this approach break down when the windows installer restarts the machine to continue installation? I assume its impossible to boot off the ISO? 

FYI I'm absolutely loving ubuntu - the only reason I want windows too is so I can play some windows games without an emulation layer.

Many thanks for any help,
felix

---

### Post by sikander3786 on 2010-12-16
Welcome to the forums :-)

Instead of a CD-ROM disc, the operations can be performed from a USB drive but not from inside the Ubuntu install.

Create a bootable USB:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Resizing the Root partition is not recommended, but you have to do if you've got no other choice. Make sure you've backed up everything important from the partition to some external storage device.

For resizing using Gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Once created your intended partitions successfully, run a filesystem check from Gparted on your root partition. Then reboot a couple of times to see if everything is working.

Now you need to create a Windows 7 start-up USB:
[http://ubuntuforums.org/showpost.php?p=9458199&postcount=6](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6)

Remember, you need a primary partition for Windows not an extended/logical one and you need to place a boot flag on that partition. Secondly, you can never install Windows using Wine but you can install Windows inside Ubuntu using a Virtual Machine server like Virtualbox but you won't be able to play games in there as the graphics performance would be low and hence that is irrelative here.

And regarding you first query, Ubuntu partition can't be un-mounted when Ubuntu is running. How would your OS run when the system partition is not mounted ;-) That needs to be done from some other OS or a Live CD/USB.

---

### Post by hetkat on 2010-12-17
Hi thanks for the reply,

I had come to a similar plan myself, namely:

1) Create a GParted bootable USB stick.
2) Use that to resize my ubuntu partition and create a new partition for windows.
3) Borrow a USB DVD drive from work, boot off the windows cd using that and follow the normal windows install procedure.

The advice you gave regarding backing up, checking the ubuntu partition and the type of partition required for windows will come in very handy.

Cheers!

---

### Post by Hates_Gates on 2011-01-12
I am doing something similar and am a bit confused on how to go about it. I have a USB external 120gig HDD and want to recover windows pc's or laptops with it using Linux. (Partition #1)
I also want to have Win 7 Recovery and ISO on the disc for a clean install and the same with XP, so that is Parts #2 and #3. But to top it off, I want to try and and have a bootable utility disc as well. Thats 4 thirty gig partitions, more than enough room to store the ISO's and any drivers I might need for any of the systems. I am just confused on how I would go about making a partition table that allows for selecting DOS, FAT32, NTFS, and ext3. Would each partition have it's own flag and would the BIOS recognize that and give me 4 choices like you would get on a duel windows boot?
Considering the hdd is being recognized as a USB drive now I am a little confused on how to do it. I am wondering if just throwing Grub for Dos in there somewhere would fix it easy enough...

Any help would be great.

---

### Post by sikander3786 on 2011-01-12
SO if I understood you correctly, you plan to place your Windows 7 recovery image on sda1, Windows XP image on sda2 and sda3 and sda4 for drivers/ISOs. And that disk also needs to hold a Live Linux Distro as well? Am I right?

Any of the partitions can be formatted either Dos, FAT32 or NTFS or ext3/ext4. That doesn't matter to the disk.

Can't say much about boot flags. sda1 would surely have the boot flag but what about the others?

And Grub2 will do the job nicely for you.

---

