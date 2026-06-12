---
title: "Dual boot with Windows 7"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by 60cents on 2009-12-25
Just got a new Dell with Windoze 7.  I added an additional SATA hard drive for my Ubuntu installation.
When I start the Ubuntu 9.1 installation the partitioning part says there are no operating systems on the computer.  The only drive choice is the new drive and the drive will be partitioned into two equal parts.  I formatted the drive with Windows 7 before I tried to install Ubuntu because before that Ubuntu would only see the original Windows 7 drive.

My concern is that if I go ahead with the install I won't have a dual boot choice since it doesn't see the original drive with the Windows install?
Do I go ahead and install Ubuntu on the second SATA drive or do something else first????

---

### Post by ajgreeny on 2009-12-25
Are you sure it does not see the new drive?  When the installer gets to the partitioning stage it shows just the layout of the first disk, if I remember correctly.

You will need to choose the manual option, the exact words of which I can't remember, but are something like "Set my own partitions manually" I think.  You should then be able to choose the second disk, and make the partitions as you want on it.

If it does not show still, open the terminal in the live CD and run ```
sudo fdisk -l
``` to see if the system sees the disk at all.

---

### Post by darkod on 2009-12-25
> **60cents said:**
> Just got a new Dell with Windoze 7.  I added an additional SATA hard drive for my Ubuntu installation.
When I start the Ubuntu 9.1 installation the partitioning part says there are no operating systems on the computer.  The only drive choice is the new drive and the drive will be partitioned into two equal parts.  I formatted the drive with Windows 7 before I tried to install Ubuntu because before that Ubuntu would only see the original Windows 7 drive.

My concern is that if I go ahead with the install I won't have a dual boot choice since it doesn't see the original drive with the Windows install?
Do I go ahead and install Ubuntu on the second SATA drive or do something else first????

If you are not running raid you can also try booting with Try Ubuntu option and in terminal execute:
sudo apt-get remove dmraid

Reboot and see if the partitioner sees the disk you want. Another option is to click on the option Erase and use whole disk, that will enable the drop down list under it, and select your new (second) drive from the list. Depending how you want to install and whether you want to create partitions manually, you can even use that Erase and use whole disk option to install it. Just make sure you select the correct disk.

---

### Post by 60cents on 2009-12-25
Blogodaria Darko
Ot kudey sta via?

Don't remember seeing the erase function??

---

### Post by darkod on 2009-12-25
> **60cents said:**
> Blogodaria Darko
Ot kudey sta via?

Don't remember seeing the erase function??

[http://news.softpedia.com/images/extra/LINUX/large/ubuntu910installation-large_007.jpg](http://news.softpedia.com/images/extra/LINUX/large/ubuntu910installation-large_007.jpg)

---

### Post by 60cents on 2009-12-25
That helped Darko
But I still don't see where I would put GRUB.
Does that appear later in the install?
I've done this before but it has been a while
Thanks for your help

---

### Post by oldfred on 2009-12-26
It has to be real late in Bulgaria now. I think it is late here.

Near the end of the graphical install is an advanced button that you can use to choose where grub is installed. Otherwise it installs to the boot drive. If you are installing on a separate hard drive it is better to keep grub on the same drive and make that drive first to boot. If you ever have problems you can switch drives back and still boot windows or what ever is on that drive.

There also is a minor bug in grub2 that if it is on one drive and the install on another it does a search for about 20 seconds for some unknown reason and slows boot by that 20 seconds. I also like to keep drives and operating systems separate and have each operating system in the MBR. Since grub/Ubuntu is good at multibooting and finding other operating systems to boot, I always make it first in BIOS to boot.

---

### Post by 60cents on 2009-12-26
Thanks All!

Got 9.10 installed on its own drive with dual boot on the UBUNTU drive and working just great. Changed the boot order per oldfred, happy as a clam.
Now I have to figure out how to set up my wireless adapter.

---

