---
title: "Xubuntu to Lubuntu clean installation without losing stored data?"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by lolxd657 on 2011-05-19
Hello, linux newbie here. I have been playing with Ubuntu and its variant for a few days, and I must say I like it. I had ubuntu, shifted to xubuntu, installed lxde wm on xubuntu to get lubuntu.

Now what I'm trying to do is install Lubuntu from scratch, wiping out xubuntu, while keeping my music, movies in place. Music and movies are in the directory of /home/*username*. Since the OS is kept on / will formatting the OS partition erase my medias too? Let me know if more details are needed.

Thank you for your help guys :)

---

### Post by jerrrys on 2011-05-19
your files will be wiped 

create a partition to put your files on

---

### Post by kn0w-b1nary on 2011-05-19
I recommend always having the /home/ partition separate, for more reasons than this. Including file survival.

---

### Post by slooksterpsv on 2011-05-19
When you reinstall via USB or CDROM do the advanced partitioning, select your drive, click on properties, select set format as (ext4 is default on new formats, so choose that if that's what it previously was) and make sure that **FORMAT IS UNCHECKED** and make it / it'll remove all previous directories except the /home/<youruser> folder

I do this often!

---

### Post by slooksterpsv on 2011-05-19
Ok so its, when you get to how you want to install Ubuntu choose:
**Something Else**

Then Click on your drive that is already ext4, and choose **Change...**

Then select Use as and choose **Ext4 Filesystem**

Make sure Format partition is **Unchecked**

And Mount point is **/**

See screenshots attached:

---

### Post by lolxd657 on 2011-05-21
> **slooksterpsv said:**
> Ok so its, when you get to how you want to install Ubuntu choose:
**Something Else**

Then Click on your drive that is already ext4, and choose **Change...**

Then select Use as and choose **Ext4 Filesystem**

Make sure Format partition is **Unchecked**

And Mount point is **/**

See screenshots attached:

Ow, okay. Few questions about partitioning.

Mount point for the filesystem will be /. To keep media files in a different partition, i.e. NOT THE SYSTEM PARTITION, what mount point shall I use? What filesystem will be good for storing medias?
I have 512mb of ram (old laptop). Will swap of 512mb be okay?

):P

---

### Post by fabricator4 on 2011-05-21
> **lolxd657 said:**
>  To keep media files in a different partition, i.e. NOT THE SYSTEM PARTITION, what mount point shall I use? 


The conventional way to do this is to set up a separate partition for /home.  This way, it works seamlessly with the filesystem - nothing really changes as far as the user is concerned as it's not obvious that /home is on a different partition.

> 
What filesystem will be good for storing medias?


ext4 is the most appropriate format for all data and system partitions.

> 
I have 512mb of ram (old laptop). Will swap of 512mb be okay?
):P

Yes, however I would be inclined to use 768mb for swap in this case.  Since you only have 512mb RAM then swap is more likely to be required depending on how you use the machine.


Since you're playing around with different 'buntu flavors and are more than likely to change again, I would suggest two boot partions, one with your current favourite (Xubuntu, maybe?) and the second one for installing Lubuntu, Puppy, or some other distro.

This makes your system even more robust, since if something happens to the normal boot partition or files you still have a second boot partition to work from.

I suggest the following layout:

```

partition 1: 15 or 20 Gb - first boot
extended partition: rest of the drive(technical reasons for this)
    partition 2: 15 or 20GB - second boot
    Partition 3: 1gb - swap partition
    partition 4: rest of drive - mounts as /home
end of extended partition

```

Pay attention to the drive designations when you set this up in Gparted (before starting install) they are likely to be something like:

sda1 - first boot
sda2 - extended partition
sda3 - second boot
sda4 - swap partition
sda5 - /home partition

It does depend on the order you set them up however. Note that the boot partitions only need to be 15gb or so - the rest can be for the /home data directory.  When you are install the OS you can specify which partition (eg sda1 or sda3) you are installing to.

BTW, installing without formatting is not guaranteed to work, though in theory it should.  I've had one failed installed from using this method (about the only failed install I've ever had with Ubuntu).

You will of course need to back up your data no matter what you do, to be safe as there's always the chance of data loss or an install going wrong.  Make sure you get all of the hidden files and directories where most of your setup and config files are. (they start with '.')

I can give you an alternative setup method that may let you keep all the data but still set up different partitions.  Obviously it will be much more complex and take much longer (it would be much faster to backup the data and restore later)

Chris.

---

### Post by snowpine on 2011-05-21
No need to reinstall. Xubuntu and Lubuntu are the same operating system with a different "desktop environment."

Try this tutorial: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by lolxd657 on 2011-05-28
Solved, thanks for your help! Appreciated :)

---

