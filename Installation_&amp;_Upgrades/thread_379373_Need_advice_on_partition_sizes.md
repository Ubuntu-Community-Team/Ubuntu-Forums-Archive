---
title: "Need advice on partition sizes"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by jmattos on 2007-03-08
Hi there

As a POC, I plan to set up a dual boot configuration with windows XP and Ubuntu, both as fresh installs.

I read this HowTo ([http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)) which seems to be a good guide for an older version of Ubuntu...

What I'd like is ...
1. Someone to explain to me how many partitions I need to set up on this new drive to accomplish this
2. What size the partitions should be

Should i use the built in partitioner in Ubuntu? Should I buy partitionMagic? What have other people's experiences been?

additionally, I want the partitions to be set up like...

1. Windows (OS)
2. Ubuntu (OS)
3. FAT32 Data, accessible by both

Help!

John

---

### Post by glotz on 2007-03-08
Right.

What kind of disk(s) you've got? Basically you first install windows and make it at least 5 gig partition using the windows installer partitioner. Then you install Ubuntu and make it at least 5 gig partition using the Ubuntu installer partitioner. And then you make the fat32, using whatever partitioner. Should be quite straight forward. I've heard that people have had problems with partition magic so I wouldn't buy it.

Here's a few other sites explaining how this all is done
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.psychocats.net/ubuntu/partitioning/](http://www.psychocats.net/ubuntu/partitioning/)

---

### Post by jmattos on 2007-03-08
The drive is a Seagate sata-150 120Gb 7200 rpm drive ([http://www.newegg.com/product/product.asp?item=N82E16822148161](http://www.newegg.com/product/product.asp?item=N82E16822148161))

I'm assuming I'll do something like....

1. Set up windows on one partition (~40Gb)
2. Create a "data" FAT32 partition (~80gb) (using  partitionMagic, which I bought or possibly the windows drive utilities? or maybe the Ubuntu utilities?)
3. Install Ubuntu to the remaining space (~40Gb) (during windows install i'll leave this space unpartitioned)

Will that work?

---

### Post by hardyn on 2007-03-08
... qustion along the same lines...

swap size? there are many many many many philosophies on swap size... what is the majority recognised formula for swap partition?

swap = physical ram?
swap = 1.5 * phyical ram?
swap = 0.75 * physical ram?

anybody?

---

### Post by glotz on 2007-03-08
You need a / (root) partition. Then you need a swap partition. And if you want, you can make a separate home partition.
(Here / needs to be at least 5 gigs, I'd suggest 10 or so.)

Ubuntu can "outta box" read vfat and ntfs and write vfat but cannot write ntfs. You'll need [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) if you plan to write ntfs. (I never tried it when I still had a ntfs partition.) So I'm not sure if you need to convert the (D) disk. Otherwise it all looks good to me. You'll want to defrag your windows before repartitioning and installing Ubuntu.

This wiki page suggests twice the amount of RAM as swap size [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Cobikegeek on 2007-03-08
It sounds like you'll need a ntfs patition for xp, an ext3 partition for ubuntu, a fat32 partition for data and a swap partition.  Since you are limited to 4 primary partitions, you probably just want the xp and ubuntu partitions to be primary (for example: sda1 and sda2).  Then make an extended partition (sda3 ?) with the remaining space and have your fat32 (sda4 ?) and swap (sda5 ?) be logical partitions in that space.   This gives you some flexibility if you decide you want a /home partition or any other partitions down the road.

As for partition sizes, Ubuntu only needs 5-10 gb for the os if you are going to store you /home data on another partition (I assume your fat32 partition).  The rule of thumb for swap is 2x your ram, but more that a gig or so is probably wasted.

Be sure to install xp first, then ubuntu.  The partitioner on the ubuntu install cd works as good or better than partition magic, so don't waste your money buying a partitioning app if you haven't already.

Good luck.

---

### Post by jmattos on 2007-03-08
> **hardyn said:**
> ... qustion along the same lines...

swap size? there are many many many many philosophies on swap size... what is the majority recognised formula for swap partition?

swap = physical ram?
swap = 1.5 * phyical ram?
swap = 0.75 * physical ram?

anybody?

I was planning 2x[ram] in my case, 4gb. That's what I've read most often, and unless I'm mistaken.. better too much than too little!

---

### Post by glotz on 2007-03-08
Except he's got two disks so the designations will be hda# and hdb#. And the 4 primaries is per disk.

---

### Post by jmattos on 2007-03-08
> **glotz said:**
> You need a / (root) partition. Then you need a swap partition. And if you want, you can make a separate home partition.
(Here / needs to be at least 5 gigs, I'd suggest 10 or so.)

Ubuntu can "outta box" read vfat and ntfs and write vfat but cannot write ntfs. You'll need [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) if you plan to write ntfs. (I never tried it when I still had a ntfs partition.) So I'm not sure if you need to convert the (D) disk. Otherwise it all looks good to me. You'll want to defrag your windows before repartitioning and installing Ubuntu.

This wiki page suggests twice the amount of RAM as swap size [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Ah okay this brings up an important question for me.

Lets say my computer currently has windows running on one physical drive (assume it's the one I listed above.) and the drive is formatted as NTFS.

IDEALLY, I'd like to go through the simple installation and have Ubuntu just take the free space to install into on the drive.... but this raises two questions.

1. Can the ubuntu installer resize that NTFS partition to give itself a nice chunk of disk space to install into ?

2. If it CAN, will it take 100% of the free space? What I mean is... if the drive is currently 50% full, or 60Gb full now, will Ubuntu take 100% of the free space?

Thanks!!!!

John

---

### Post by glotz on 2007-03-08
It can and you decide how much you'd like to use. It uses GParted to partition, here you can see ntfs is fully supported. [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
Just remember to defrag windows first so there will be no surprises.

In the install, just choose the right options so you can define how much disk it will use! :)

---

### Post by jmattos on 2007-03-08
> **glotz said:**
> It can and you decide how much you'd like to use. It uses GParted to partition, here you can see ntfs is fully supported. [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
Just remember to defrag windows first so there will be no surprises.

In the install, just choose the right options so you can define how much disk it will use! :)


Okay, that's cool. Looking at this walk through ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) I see that one option is to manually set up the partitions, which I THINK I can handle.

I'm going to give that method a try, and simply leave 50% of the drive (~60gb) for Windows (Winblows) and give the rest to Ubuntu.

All good. Thank you all for some excellent input and information!!!!!!!!

---

### Post by glotz on 2007-03-08
:biggrin: 

Welcome to the tribe!

---

