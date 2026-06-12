---
title: "Selecting Right HDD help"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by Threaten on 2010-08-05
Hi. I have been a fan of Ubuntu ever since I discovered it. I have wanted nothing more than to make it my primary operating system, but due to some restrictions I cannot.

However, I would like to install it on my computer which has two separate 300gb HDD's. One of the hard drives has Windows 7 on it, and I do not really want to partition it to fit Ubuntu in that cramped space. I would rather it be installed on my other hard drive, but I do not know how.

Could someone help me do that?

---

### Post by dabl on 2010-08-05
There's nothing special about your situation -- the installation on your unused drive can be as simple or complex as you want, just as if it were the only drive present on the system.

I personally use a Parted Magic Live CD to partition my target hard drive, before I install Linux.  If you do that, it should be obvious from the color-coding on the partitioner graphic which hard drive has something on the partition, and which one does not.

If that's too difficult, then if you shut down and open your computer, and pull the data cable off one hard drive, you have a 50% chance of having only your target (empty) drive left connected.  If it boots Windows, then you 'll know you went wrong and you'll have to shut it down again, and pull the other data cable, and reconnect the first one. Then you'll only have the one drive to worry about while you install Ubuntu.  :)

---

### Post by ajgreeny on 2010-08-05
Firstly, I strongly recommend that you backup all your files from both disks, assuming there are files on both.   Then I would suggest you run the live CD, and in that use the command ```
sudo fdisk -l
``` in terminal.  That will tell you the disk naming as sda and sdb.

I suspect sda will be the win7 disk and have ntfs, and perhaps fat32 partitions on it.  sdb may or may not have partitions on as well, but will not have the OS.  It may be just a data disk, but you did not say if it is used at all at the moment.

Now run the install program from the desktop icon and at the partitioning stage choose manual partitioning which will show you both disks and the partitions on them.  If I have things right about your win7, you can delete the partitions on sdb and install to that disk very easily, and also make a separate /home partition if you want to.  In your situation, however, it may be better to have a separate /data partition formatted as ntfs so both OSs can use it, and this could simply be a shrunk version of the ntfs partition already on that disk, if it is already being used for that purpose.

Just to make sure we get things right, can you run gparted from the live CD, and show a screenshot of both sda and sdb before you go ahead with the install.  Grub can be installed on sdb if you prefer rather than the MBR of sda where the windows bootloader files will be at the moment.  That way you can choose to either boot straight to windows if sda is first device, or to grub and then choose either OS if sdb is first device.  Your choice.

---

### Post by Threaten on 2010-08-05
Thank you for the quick response!

ajgreeny, some of the stuff you mentioned makes little sense to me...I am very new to the ubuntu world. It wouldn't be a stretch to call me a n00b.

Anyways, I followed your instructions, and did both of those. I captured a screenshot of GParted and the terminal window, and I must say I like how ubuntu handles the pressing of the Print Screen button.

Anyways, here it is:
[img]http://img411.imageshack.us/img411/9364/screenshotxp.png[/img]

I am too lazy to back up my files, and I do not have anything really worthwhile on there, I just do not want the hassle of messing up and having to reinstall. I am just looking for a confirmation on which hard drive to use, and how to avoid removing my Win7.

Thank you!

---

### Post by ajgreeny on 2010-08-05
OK, if there is nothing on sdb that needs keeping, just run the installer from the live CD and choose to install to the whole disk sdb.  You already have a swap partition which you can use so manual partitioning may be the best option, but is perhaps a more difficult way to do things if you did not follow my first post easily.  Come back again or have a look at [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) which has some good general info on installing that may be helpful to you.

On the final screen before you actually install the system there is an **Advanced** button which allows you to choose where to put grub.  Choose either sda or sdb, but make sure you do not put it on a partition, ie not sda1 or sda2, or anything with a number at the end, just sda or sdb, then choose the disk to boot in the BIOS or the boot options that you may have at bootup

---

### Post by Threaten on 2010-08-05
Alright, thank you.

For confirmation, Grub is the bootloader, and where I put it allows me to select which operating system I start up? If my understanding is correct, if I put Grub on sda, I can choose either Windows 7 or Ubuntu to startup every time?

---

### Post by Threaten on 2010-08-06
I have solved this. Thank you for your help!

---

