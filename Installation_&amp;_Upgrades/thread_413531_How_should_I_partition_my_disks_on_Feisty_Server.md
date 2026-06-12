---
title: "How should I partition my disks on Feisty Server?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by krolben on 2007-04-19
Hi all

I'm in the process of installing a Feisty server, but I'm not sure what the best partitioning of the system will be.
The server will be used as a file/music server and home web server.

Hardware:
It's a Mini-ITX system with a primary harddisk of 1GB (flashcard attached to IDE) and two 320 GB disks connected through USB.

The idea is that these 2 disks should function in some kind of RAID1. Can I set up this RAID in the partitioning process in some way, or do I have to set it up afterwards.

What partitions would you set up? Where, and what sizes?

---

### Post by krolben on 2007-04-19
nothing?

---

### Post by stuarttaylor on 2007-04-20
I am currently wondering that at this very moment. Although I doubt you can set up a USB drives in a raid array.

---

### Post by Mr Wonka on 2007-04-20
You should be able to do all this just fine though I'm not sure 1Gb is big enough for a root disk. I'd recommend a minimum of 3Gb. You may be able to use the flash as /boot and have root on the MD-Raid discs but that depends on whether the ubuntu initrd image brings up USB before attempting to mount the root filesystem. This will need some research but it is possible.

Personally I'd recommend that you use 'evms'. It's a layer over the top of LVM and MD-Raid. It has taken me a while to get used to terminology and the way it works but it's very nice and makes it incredibly simple to do disk related things. LVM is especially nice as you can just fiddle around with partition sizes and thing with no data loss. If you use ext3 as the filesystem you can increase the size of a disc on a live filesystem (great for root, which you generally can't unmount)

You should install evms-ncurses (or something like that) to get a nice command line GUI type thing.

So assuming you can get it to mount root from USB i'd recommend the following.

/boot on CF card.
Use EVMS to set up the following tree:
/ - 3GB *ext3 (Start small and increase in size as needed. Since you can do this on a live filesystem)*swap - *Same as Ram*    
    LVM - 320GB Volume Group
        /dev/md0 - 320GB *raid1* 
            /dev/sda (assuming it's here)
            /dev/sdb (ditto)

Once you happy it's up and running you can create new volumes within the LVM volume group i.e. 70GB /home. Use evms' fantastic snapshoting facility to image the current home on the new volume and then mount the new volume at /home. Without having to restart anything and without disruption.

Hope some of this helps
Mr Wonka

---

