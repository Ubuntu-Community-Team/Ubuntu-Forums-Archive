---
title: "Dual Boot - 1 HD with partition for linux"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by Caritas on 2007-02-19
After working with Xubuntu on an old slow PC, I'd like to try Ubuntu on my faster everyday desktop.  My PC has only one bay for a HD, the other is filled with an internal multi-card reader.  I installed a new HD in that 1 bay, reformatted and partitioned the new HD with 4 partitions, 1=C windows OS, 2=D partition for Ubuntu, 3=E applications, 4=F data.  I used Windows XP Pro Disk Management to do the partitioning.

In reviewing information about dual booting I have gotten the impression I have to use a linux partition tool on my hard drive, but I'm not sure how I would do that.

Can I use the Ubuntu 6.06 Live CD to prepare only the partition I have already set aside for Ubuntu?

If my already existing partition set aside for Ubuntu is ready for installing, how would I do that?

Thanks.

---

### Post by confused57 on 2007-02-19
Here's an excellent guide, see the section on "Plan Partitions":
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

The gparted live cd is an excellent partitioning tool:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Keep in mind that you can only have 4 primary partitions on a hard drive, but one of those can be an extended partition, that can have many logical partitions within it.  The standard Ubuntu install is a root partition and a swap partition(unless you have at least 1 Gb memory, you'll probably need swap).

Ubuntu doesn't use C,D,E,F, to designate partitions, but uses hda1, hda2, hda3, etc(hdb for the slave IDE drive) or sda1,sda2,etc for SATA drives.

You'll have to use Windows partitioning tool to setup NTFS partitions, however, Linux is not able to write to NTFS(unless you install a driver, which is beta & unstable)...Linux can write to & read FAT32...Windows can read & write to ext3, with the fs-driver & from what I've read it works quite well.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Partitioning is individual preference, but you might want to consider having your Windows install, applications, & data partitions as primary partitions, then an extended partition that you can install Ubuntu on(root & swap)...this should give some idea of what you "might" want to consider.
If you want to keep what you've already set up, you may want to delete the Ubuntu partition, so that it is "unallocated' space, that way the live cd installer "should" automatically set up & install Ubuntu...creating an extended partition & install root & swap on logical partitions.  You might want to select "manual" partitioning, choose to install to the unallocated space...that way you can specify how much to allocate to swap(1 Gb should be sufficient)....just keep in mind, you wouldn't be able to share a NTFS partition between Windows & Ubuntu(read, but not write to NTFS).

---

### Post by Caritas on 2007-02-19
Thanks, the planning for partition was helpful.

If I understand my options I can do the following.

Use Win XP's disk management to change my current D partition to unallocated space.

Use the Live CD to install Ubuntu and choose manual for install/partition.

Select 1 gb for the swap file and use the rest of the unallocated space for an ext3 partition.

Do I have the right ideas?

Thanks.

---

### Post by Caritas on 2007-02-19
Deleting the partition with win xp disk management and making it unallocated space, followed by booting from the Ubuntu install disk worked.  I planned to have  /root, /home and swap partitions in the allocated space and figuring out how to make each partition ext3 or linux swap was easy but how to configure them as /, /home and swap was not intuitive for me.  I eventually got it right.  This reply is being written using Firefox from Ubuntu in my new Linux partitions.  I was amazed that I did not have to do anything at all for Ubuntu to effortlessly integrate into my home network (dsl bridge and wireless access point with an ethernet cable to the access point).

One plea for help and one reply - that's a record for me when asking for assistance.

---

### Post by confused57 on 2007-02-19
> **Caritas said:**
> Deleting the partition with win xp disk management and making it unallocated space, followed by booting from the Ubuntu install disk worked.  I planned to have  /root, /home and swap partitions in the allocated space and figuring out how to make each partition ext3 or linux swap was easy but how to configure them as /, /home and swap was not intuitive for me.  I eventually got it right.  This reply is being written using Firefox from Ubuntu in my new Linux partitions.  I was amazed that I did not have to do anything at all for Ubuntu to effortlessly integrate into my home network (dsl bridge and wireless access point with an ethernet cable to the access point).

One plea for help and one reply - that's a record for me when asking for assistance.

Glad to hear it worked out, doesn't sound like you had much problem installing...you'll enjoy working with Ubuntu & Linux, least you have a choice of OS...

---

