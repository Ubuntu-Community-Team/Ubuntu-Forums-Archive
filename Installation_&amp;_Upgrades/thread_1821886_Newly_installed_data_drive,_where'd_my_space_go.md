---
title: "Newly installed data drive, where'd my space go?"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by lessblue on 2011-08-09
I have 5 drives installed in my Ubuntu server as follows:

/dev/sda/ - 160GBB drive for Ubuntu Server installation
/dev/sdb/ - 2TB drive split into two partitions
/dev/sdc/ - 2TB drive split into two partitions
/dev/sdd/ - 2TB drive split into two partitions
/dev/sde/ - 2TB drive split into two partitions

I've split all my 2TB drives into two equally sized partitions. These are ext3 formatted and nothing on the drive. Why do all my partitions (the 2TB data drives) show a similar loss in space as the pic below (from webmin)?

[[IMG]http://img41.imageshack.us/img41/6830/capture2be.jpg[/IMG]](http://imageshack.us/photo/my-images/41/capture2be.jpg/)

---

### Post by lessblue on 2011-08-09
I just finished transferring files over from my W7 machine to a partition on the Ubuntu box and it shows 0 free space available which doesn't make sense (there should be some space left over on the Ubuntu partition). And what's being used on these new partitions, that should be 0 no?

Here's what # df shows also:

[[IMG]http://img839.imageshack.us/img839/8493/capturetsv.jpg[/IMG]](http://imageshack.us/photo/my-images/839/capturetsv.jpg/)

---

### Post by lessblue on 2011-08-09
Ah, so 5% is reserved for the superuser.

Is this space completely off limits? It's a data drive so I know how much to store on it. How can I make the full space available for data/file/media storage?

---

### Post by YesWeCan on 2011-08-09
[http://linux.die.net/man/8/mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3)
option -m

---

### Post by lessblue on 2011-08-09
> **YesWeCan said:**
> [http://linux.die.net/man/8/mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3)
option -m

Thank you but I'm not sure if that formats the partition too in which case the data would be lost?

I did find this and used tune2fs to free up all the space:
[https://help.ubuntu.com/community/InstallingANewHardDrive#Modify%20Reserved%20Space%20%28Optional%29](https://help.ubuntu.com/community/InstallingANewHardDrive#Modify%20Reserved%20Space%20%28Optional%29)

> Modify Reserved Space (Optional)

When formatting the drive as ext2/ext3, 5% of the drive's total space is reserved for the super-user (root) so that the operating system can still write to the disk even if it is full. However, for disks that only contain data, this is not necessary.

NOTE: You may run this command on a fat32 file system, but it will do nothing; therefore, I highly recommend not running it.

You can adjust the percentage of reserved space with the "tune2fs" command, like this:

 sudo tune2fs -m 1 /dev/sdb1

This example reserves 1% of space - change this number if you wish.

    {i} Using this command does not change any existing data on the drive. You can use it on a drive which already contains data. 

Thank you for your help!

---

### Post by YesWeCan on 2011-08-09
Yes mkfs will reformat. I thought you had nothing on your drives. tune2fs is better.

---

