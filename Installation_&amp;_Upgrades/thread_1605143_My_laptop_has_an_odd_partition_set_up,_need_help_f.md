---
title: "My laptop has an odd partition set up, need help figuring out how to install ubuntu"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by mark92 on 2010-10-24
Hello,

Fairly new Ubuntu user here and a very new drive partitioner.

I have a Lenovo y550p laptop which came with Windows 7 Home Premium 64 bit edition and a total of 4 disk partitions already created. The drive is partitioned up as follows:

Partition 1 - 200 MB NTFS (System, Active, Primary Partition), if I understand correctly this partition is used by Windows 7 when booting?

Partition 2 - 420.56 GB NTFS (Boot, Page File, Crash Dump, Primary Partition), the C: partition for Windows 7

Partition 3 - 30.25 GB NTFS (Logical Drive), the D: which appears to just hold the drivers for the laptop

Partition 4 - 14.75 GB (OEM Partition), I believe this is the restore partition

I would like to create an additional partition and install Ubuntu (64 bit) along side with Windows 7 so I can choose what OS to boot into when starting up. However from what I read you can only have 4 partitions on a drive is this correct? If this is true then if I were to backup the D: drivers to a DVD and then create a new partition in its place could I resize my C: partition and install Ubuntu where the D: used to be (with a little more space than the D: originally occupied)?

Thanks a lot for any help, and if someone could recommend a good tutorial for installing Ubuntu alongside Windows 7 on a partition set up similar to mine and getting a boot loader working and allowing for dual boot I would be very grateful!

Thanks!

---

### Post by Quackers on 2010-10-25
Welcome to Ubuntu Forums :-)
You can only have 4 PRIMARY partitions, but you could have 3 primary partitions and 10 logical partitions if you want to.
If you are planning on reducing the Windows partion anyway I suggest you go to start > then right-click on Computer and select Manage. In the windows that opens up select Disk Management on the left side. A new window will open up giving you a display of your disk layout. Right-click on your Windows 7 partition (420.56GB) and select "shrink". A small window will then open up stating by how much the partition can be shrunk by (if at all). If you shrink the partition the new space will become "unallocated space".
In the Disk Management window are all 4 partitions listed as "primary"? Are the coloured lines in all the partitions the same blue colour?
If they are you will need to delete one of them (after backing up the data first!). This deleted partition can be replaced with a logical partition and the data replaced.
The Ubuntu installation can now be made in the "unallocated space" created previously.

---

### Post by mark92 on 2010-10-25
Thanks for the response!

The colored lines of my four partitions are all blue however the D: partition's color is a lighter blue than the other three (judging by the key the other three are primary and the D: is logical)

Since a drive can have up to 4 primary partitions and I appear to only have 3 I should be able to shrink my Windows 7 partition with the disk tool and then install Ubuntu on the new unallocated space like you stated is that correct?

I just want to clarify that I understand you correctly and thanks for all the help!

---

### Post by srs5694 on 2010-10-25
The Windows partitioning tool seems to be looking at the disk as it exists in some alternate reality; its mapping of "primary" and "logical" labels bears little resemblance to what the disk actually is. I recommend you boot from a Linux CD (an Ubuntu install CD in "live CD" mode or an emergency disc like [Parted Magic](http://partedmagic.com/) or [System Rescue CD](http://www.sysresccd.org/)) and use a Linux partitioning tool to examine the disk. Post either a screen shot of the GParted tool's main display or the text-mode output of "sudo fdisk -lu" typed in a command prompt.

Many computer manufacturers today ship with four primary partitions, which is obnoxious. Fortunately, you can work around this. There should be a Windows utility that enables you to create emergency recovery DVDs. These DVDs, once created, will hold the equivalent of the recovery partition. This partition is usually about 15 GB in size, so I'd guess it's what you've identified as partition #4; however, it's conceivable it's your partition #3. (If it's #3, it's the largest such partition I've ever heard of. Some manufacturer ship with a much smaller partition with custom software. Are you sure it's not a 30 *M*B partition?) I suggest you make your recovery DVDs (make two sets for safety), nail down which partition these disks obviate, and delete that partition. You can then create an extended partition in its place and create as many logical partitions as you like for Linux. (Linux is quite happy to boot from a logical partition.) If your computer manufacturer has not maxed out the primary partition count, your task may be easier; however, I still recommend making emergency recovery DVDs. Whether you choose to delete the partition from which they were built is up to you at that point. You might or might not really need the extra space.

---

### Post by mark92 on 2010-10-25
Thank you for the further information, here is my GParted screen shot from the Ubuntu 10.04 live cd, is there anything I can do with this set up as is? If I were to say shrink /dev/sda5 to 3.00 GiB then could Ubuntu be installed on the unallocated space after it is formatted as an ext4 logical partition?  If so, I'd also be curious as to how I can set up Grub boot loader so that it works with Windows 7 and the new Ubuntu install? Thank you so much for any further help!

[IMG]http://img831.imageshack.us/img831/263/gparted.png

---

### Post by oldfred on 2010-10-26
gparted has trouble (yellow triangle) seeing your Main windows install so it is not showing how much space is used. Did you hibernate windows or does it need chkdsk run. 

Yes you can install Ubuntu into 10-20GB for / (root) and 2GB for swap. Your sda3 is an extended partition and sda5 is a logical with only 3GB used. If you shrink sda5, you then can add sda6 as root and sda7 as swap. Then you can use manual install and choose which partition to use for / and what format to use. If in gparted you set sda7 as swap the installer finds it automatically otherwise you can tell it that sda7 is swap as part of the install.

Eventually if you like Ubuntu you may want more space but we can add that later. I do like to have a shared NTFS partition so you do not have to write data directly into the windows partitioin & then you have a place to save data you want to share between systems.

Some install examples so you can see what you will be doing (the second is closest to what you are doing):
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by mark92 on 2010-10-26
Great! Thanks for the resources, I'm going to back up all my info and make some restore dvds and try an install within that extended partition tomorrow, thanks to everyone for all the help

---

