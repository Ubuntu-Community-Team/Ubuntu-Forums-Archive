---
title: "Installing 7.04, Problems with Partitioning"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by thetonestarr on 2007-09-21
I recently obtained a 400GB HDD that I'm attempting to set up in a store-bought HP system (replacing the previous HDD (that I'm going to keep as a secondary, has Vista on it). System is an HP Pavilion Slimline s3000y, has a 3.2GHz P4, 2GB SDRAM). 

I'm installing Ubuntu 7.04 on it. Here are the steps I take in partitioning:

- How do you want to partition the disk?
  *Manual  >  [Next]
Select the hard disk (probably /dev/sda)
     - [New Partition Table}
                      - Continue
   -Click on -free space   &#9632;      Click [New Partition}
     #Create a new Partition
         Select Primary, size = 100MB, beginning, Use as: EXT3, Mount point: /boot, Click [OK]
   -Click on -free space   &#9632;      Click [New Partition}
     #Create a new Partition
         Select Primary, size = 1024MB, beginning, Use as: swap Click [OK]
    -Click on -free space   &#9632;      Click [New Partition}
     #Create a new Partition
         Select Logical, size = 500MB, beginning, Use as: ext3,  Mount point /tmp  Click [OK]
       -Click on -free space   &#9632;      Click [New Partition}
     #Create a new Partition
         Select Logical, size = 500MB, beginning, Use as: ext3,  Mount point /var  Click [OK]
    -Click on -free space   &#9632;      Click [New Partition}
     #Create a new Partition
         Select Logical, size = {remainder}, beginning, Use as: ext3,  Mount point /  Click [OK]

Every time I click OK on the last step, I get this error:

[IMG]http://img.photobucket.com/albums/v85/tonyofthesavvy/error.png[/IMG]

I've toyed with changing the last partition. I've switched from "beginning" to "end", I've switched from "logical" to "primary", I've selected less HDD space FOR the partition (first I selected 3MB less, then 13MB, then 63MB, then 163MB, and nothing has helped so far).

Help?

I'd like to keep the current settings for what they do for me, but if I can get that same result another way... please, do tell. I'm open for any suggestions.

---

### Post by Pumalite on 2007-09-21
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
First delete all partitions in your hard drive. Now click on it and make one large partition of your entire hard drive, format ext3 if you want, then install>Guided>Use Entire Disk

---

### Post by thetonestarr on 2007-09-21
I can do a guided partition, no problem. I don't need GParted to do that.

But that's not what I'm wanting to do. I don't want to do a guided partition. I want to do it manually.

Either way, how does it partition the disk via guided mode? Is it just the same thing as what shows when I click "manual", by default? Because that's not what I want. I'm trying to partition it this way for a reason, and I'd like to still reach the same end, if possible.

---

### Post by Pumalite on 2007-09-21
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by maybeway36 on 2007-09-21
GParted can do manual too. And if the GPArted CD doesn't boot, you can use Knoppix.

---

### Post by thetonestarr on 2007-09-21
Thanks guys. I'll be trying these solutions out later tonight (when I get home).

*sigh.* And I'm also going to have to hard-wire my system to the network for the time being, until I can download the drivers for my wireless card. You may find me posting in the wireless forum soon, too.

---

### Post by Pumalite on 2007-09-21
Good luck.

---

### Post by jc508 on 2007-09-21
Its actually a bug in the installer (or reported as such) I can't find the like at the moment though sorry. Seems the installer can't cope with a partition > 200Gb
Workarounds are not clear

JC

---

### Post by Pumalite on 2007-09-21
I have installed Live CD and Alternate CD to 500 GB hard drives without problems.

---

### Post by jc508 on 2007-09-21
Yep - got it to work.

Download gparted live cd from [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Boot to this and partition as desired.  It let me create partition > 200GiB

Now go back to the install and at the partition screen choose manual. 
Reassign the mount points for the partitions you have created and tick the format box

It now seems to install into there with no dramas.

JC

---

### Post by thetonestarr on 2007-09-21
Thank you, sir. I'll be getting all of this taken care of within the next two hours or so, and I'll be keeping you guys updated on how things go from here.

If it still doesn't work, does anybody know if it'll work fine if I just split the partition into two <200GB partitions? Because I may do that, then use one of the partitions for apps, games, and the like, and use the other for media (MP3s, videos, images, etc).

---

### Post by Pumalite on 2007-09-21
You can partition your drive as you like  with Gparted. Whatever you do, give at least 10 GB for'/', 500 MB for /swap and the rest for /home.

---

### Post by thetonestarr on 2007-09-25
Okay, I got it to work right. GParted Live CD wouldn't load to the GUI, so I downloaded Parted Magic (an alternate partition editor that uses GParted in it), and it worked correctly.

I've got Ubuntu installed now with the aforementioned partitions.

---

### Post by Pumalite on 2007-09-25
Glad you got it working!

---

