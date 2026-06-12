---
title: "I need help installing Ubuntu 10.10 on my 3 HD desktop"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by TheDudeAbidesLinuxStyle on 2011-02-15
Alright so I need some help. I've been using Ubuntu for a few years now and I see no need to use Windows anymore. My Asus U6S laptop runs only Ubuntu so I figured my desktop should be windowsless as well. On my Sony RA desktop I have a 250 GB Western Digital HD running Windows and a 500 GB HD Western Digital HD running Ubuntu. I also just installed a 3rd 500 GB Western Digital HD I had from another machine which is completely unallocated space. I'd like Ubuntu to take up all of my HD space.

I'm trying to do the install across all 3 but if I choose "erase and use entire disk" it makes me pick only 1 of the 3 HD's. And when I go into the advanced partitioning tool I get a little lost. I added every part of every HD as ext4 and and selected for it to be formatted but I run into "no mount point assigned for ext file system SDC...." and then I assign a mount point "/" for that file system it tells me that "two file systems can't have the same mount point." 

250 GB HD is sda (no mount point assigned)
500 GB HD is sdb (this is the unallocated HD which I assigned mount point "/")
500 GB HD is sdc (this is the one I tried to add another mount point "/")

So, what should my mount points be? Any advice is most appreciated. Thanks!

---

### Post by jerrrys on 2011-02-16
the standard install will install on only one hdd at a time.  you need something like [colonzilla]("http://clonezilla.org/")

---

### Post by sikander3786 on 2011-02-16
Welcome to the forums :-)

So if I understand you correctly, you want to install Ubuntu in a way that all of your disk space is used efficiently by Ubuntu for different purposes but not in a way that they are multiple copies of installs on all of your HDDs. Right?

You can either make your drives appear as one and setup LVM or software RAID.

[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

Or simply, install Ubuntu to one of your HDDs and then mount the other 2 Hard drives under Ubuntu and use them for data storage. For mounting and chowing ext3/ext4 partitions, see here.

[http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html](http://ubuntu4beginners.blogspot.com/2011/01/permanently-mount-ext3ext4-drives-with.html)

Or, you can choose manual partitioning and then assign different partitions to /, /home, /boot, /var, /log, /tmp etc all on different drives but that would be such a waste of your disk space. Not recommended at all.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

The best I can think of is to mount your extra drives for data storage.

---

### Post by oldfred on 2011-02-16
I go along more with sikander3786's suggestion. In fact I prefer to have each drive bootable on its own, with all the system files & grub in that drive's MBR. That way one hard drive failure does not take entire system down.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate  them from drive to drive (new version install on different drive).

---

