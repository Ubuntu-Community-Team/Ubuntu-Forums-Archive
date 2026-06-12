---
title: "partitioning to make space for Debian"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by shirishagarwal on 2008-11-30
Hi all, 
 I am gonna try install debian. In Windows we have the defragmenter which defrags and then one can do stuff for Ubuntu. For Debian how do I do this?

I do know I could use gparted on the live CD but still if there is a howto or something it would be nice.

---

### Post by forkandles on 2008-11-30
Try starting here.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by shirishagarwal on 2008-12-01
The problem for me is it could turn out to be something like the one described here. 

I dunno if ubuntu should be installed at last or not. If it should be installed last then will have to wait for few days. 

[https://www.linuxquestions.org/questions/linux-newbie-8/installing-debian-has-damaged-ubuntu-on-dual-boot-system-586708/](https://www.linuxquestions.org/questions/linux-newbie-8/installing-debian-has-damaged-ubuntu-on-dual-boot-system-586708/)

---

### Post by forkandles on 2008-12-01
I take it that you have Ubuntu currently installed on your hard drive (sda) and that you have additional space on this drive to also accommodate Debian?

If that is the case, first of all, download and install gparted live (0.3.9-13.iso) from here.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Then burn the .iso to a CD using Brasero or K3b.

For guidance on using gparted look here.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Now, the main thing to remember is that it is only possible to have a maximum of 4 Primary partitions.
The chances are that you are already using 3 primaries for root (/), swap-linux and home (/home) for Ubuntu.
I am guessing that your current situation is something like this.

Partition Number             File System        Name       Mount Point                Size
Partition 1 (/dev/sda1)        ext3                     root              /                           12GB
Partition 2 (dev/sda2)         linux-swap           swap                                        1GB
Partition 3 (/dev/sda3)          ext3                   home         /home                     30GB
Partition 4 (/dev/sda4)          ext3                    unallocated                             40GB

Backup any important data NOW!

Load the gparted CD and boot from it. Select sda drive (top right corner) or whichever drive you wish to partition.
First you need to create an unallocated Extended partition in the 40GB space.
Refer to the gparted guide. 
Then you create 3 (or more) Logical partitions within the newly created Extended partition.

Next, within this partition create, say, 
sda5 root (13GB)
sda6 swap (2GB)
sda7 home (25Gb) as 3 logical partitions to accommodate a new Debian or other Linux installation.

So now we have, in addition to the above sda1, sda2, sda3 for Ubuntu:
sda4  allocated Extended which contains (ready for Debian ):
sda5       ext3                  root                    /                             13GB
sda6                              linux-swap                                          2GB
sda7       ext3                  home                 /home                      25GB

When you are happy with the new partitions click on Apply. When gparted is finished, switch off the pc and eject the gparted CD.
Now load the Debian (or other Linux) installation CD.
Select Manual or Custom Partitions (NOT Auto or Use Whole Disk) to allow Debian to install on sda5, sda6 and sda7.

Select &#8220;Install GRUB on MBR&#8221;.
Click on Finish, reboot and remove Debian CD.
All being well, you should now have Ubuntu and Debian dual booting on your pc.
Select which one you require from the boot up screen.
Good luck.

---

