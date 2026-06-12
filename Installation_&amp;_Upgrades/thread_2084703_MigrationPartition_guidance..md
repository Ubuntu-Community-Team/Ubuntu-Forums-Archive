---
title: "Migration/Partition guidance."
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by Coryn11 on 2012-11-16
Hello, I'm Drew. I'm a fairly new Ubuntu user, and have been using it for some time as a Wubi install and quite enjoy it. I understand it somewhat, and I would love to learn the details of how it works and such. I've been using Vista, and I've always disliked it, but its all I've had to work with, and I need to keep it for anything Ubuntu has issues with. Now, onto the problem at hand.

I've been wanting to migrate Ubuntu into a dedicated partition; I have a basic knowledge of partitioning, but all the guides I've looked for online only really show how to migrate it if you already have the partitions set up. The one guide I did find that showed partitions confused me and didn't explain it all. (as far as I recall anyway, I can't seem to find it anymore.) 

I believe I understand the auto migrate guides I've seen. But anyone who could help explain how I should set up the partitions so they will work with the auto migrate commands (or possibly explain the command, and how the partitions function with it and etc.) would be much appreciated. :)

My apologies if this could be solved with a quick google search, if it can then I must be using the wrong search terms; I know I have been having difficulty finding anything that solves my issue

EDIT: I'm using Ubuntu 12.04, I had forgotten to put that originally.

---

### Post by ajgreeny on 2012-11-16
What partitions do you already have on the disk?

I don't know wubi well enough to know if ```
sudo fdisk -l
``` command gives a true output of all the disk's partitions, but it's a good start.  You can also see everything in the Vista disk management utility, which you should use anyway to shrink the windows partition, assuming there is a chance of adding another partition to the disk, as you can only have 4 primary, or 3 primary + 1 extended, partitions on a MBR formatted disk.

So tell us what you have at the moment and then we'll be in a better position to tell you how to proceed.

---

### Post by Mark Phelps on 2012-11-16
To further emphasize that ajgreeny told you -- use ONLY the Vista Disk Management utility to shrink the OS partition.  Using any Linux utility, include the Ubuntu installer, to shrink the partition risks corrupting the Vista OS and rendering it unbootable.  And, since you probably do not have a Vista Repair CD, you would have no real way of repairing that.

---

### Post by oldfred on 2012-11-16
I do not know wubi either and number of existing partitions and sizes is important as to how you may be able to reconfigure.

What size is you current wubi install and what size do you want for you new install? May be limited by how full drive is now. Windows NTFS partitions like 30% free space, so do not shrink too much, but you will make more space when you delete the wubi root.disk file.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

A standard dual boot auto install of Ubuntu just creates / (root) and swap. That is all you have to have and you may not even have to have swap if you have a lot of RAM, but some is always suggested. Many of us suggest a separte /home partition also as that may make new installs a bit easier in the future, but not required. 

Good backups, repairCD or USBs for both Windows and an Ubuntu liveCD are needed before you start.

Use Vista to shrink the Windows partition, but use gparted to create new partitions.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Lots of info on partitions.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Coryn11 on 2012-11-16
I currently only have the single partition. With vista and Wubi install. The Wubi install is a 18gb install.

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) <-- This is the guide im using to auto migrate wubi. My main question is how to create the partitions needed to work with those commands. Or explain how to change the command so I can use my own partition names. 

I understand how to resize, create, and format partitions. My question is what is the details that I need to use for the partitions I'm gonna transfer Ubuntu into. such as to use FAT32, make it primary/extended. Everything to make it work with the commands in the link. 

I have 2gb of RAM, so I believe I'll need a SWAP partition of 4gb. again, I need to know the details of it. And I'm planning on having the total space I wish to use for ubuntu 30gb. (not including the swap)  

I might separate it into /home and such, but that comes second to simply getting it started with the commands.

---

### Post by bcbc on 2012-11-16
You need to create an ext4 partition (type 83). For swap you need to create a swap partition (type 82). GParted is the best way to create these once you have freed up space for them.

To free up space you can use the Windows Disk management tool. Right click on the C: drive and select "Shrink volume". 

I recommend then creating an extended partition in that space, so you have the most flexibility (otherwise you're limited to a max of four partitions). Personally I created my extended partition in Windows using the [diskpart]("http://technet.microsoft.com/en-us/library/cc727978(v=ws.10).aspx") tool, but you should be able to use GParted for this as well (from the Wubi install). [I had a little weirdness with logical partitions becoming primary in Windows so that's why I used Windows to create the extended]

Once you have that you can boot the Wubi install, install gparted, and create two logical partitions inside the extended partition. Make the first of type Ext4 and the second linux-swap. For 2GB of RAM I'd use 3GB of swap. Sometimes hibernation doesn't work if you don't have enough swap. Let the rest be your main partition, or create a separate /home (but this can be a pain if you don't know how much you need and run out of space on the separate partitions later).

I attached a couple of screen shots for examples. Yours won't look exactly the same, but hopefully it gives you an idea. Let me know if you have more questions.

---

### Post by bcbc on 2012-11-16
Here are some more screenshots including what the "sudo fdisk -l" output looks like (where you see partition type 83 and 82). Note that the screenshots are not the most recent version of the script (the main difference being that the main script wubi-move-2.2.sh is now named wubi-move.sh). Other than that, it's the same. [http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html](http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html)

---

### Post by littlegreenman on 2012-11-19
Hi Drew,

I am using Ubuntu 12.10 (Wubi), and I am interested in doing the same, and had exactly the same questions as you do. Please do keep us posted how it worked for you following these suggestions.

I have been an on and off Ubuntu user, and for the first time I find it a system easy enough for me to use, but I am afraid to take the plunge and mess something up, so I am really looking forward to follow your steps...

Thanks,
Diogo

---

