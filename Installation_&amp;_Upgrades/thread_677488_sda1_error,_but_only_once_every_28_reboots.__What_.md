---
title: "sda1 error, but only once every 28 reboots.  What the heck?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by oldsmobile_mike on 2008-01-24
I get this message, once every 28 times I reboot my laptop:

* Checking root file system...
fsck 1.40.2 (12-Jul-2007)
/dev/sda1 has been mounted 28 times without being checked, check forced.

Then it runs through a check, after which everything seems to continue to work fine.  What is going on here, and what is sda1?  Is it anything to be concerned about?  The system seems to run fine, aside from occasional freezes, but this seems to be related to IO input, and will be a topic for another thread...

System specs, if it matters:

Sager 5600P laptop, 2.0Ghz P4, 512Mb ram, Ati 7500 graphics, running 7.10.

Thanks!

---

### Post by wieman01 on 2008-01-25
'/dev/sda1' is your root file system, i.e. your Linux partition. And a file check is forced upon you after 28 restarts or so. That's a pretty common feature and is nothing you have to worry about. Read this for more:

[http://www.zip.com.au/~akpm/linux/ext3/ext3-usage.html]("http://www.zip.com.au/~akpm/linux/ext3/ext3-usage.html")

---

### Post by hpn909 on 2008-01-26
> **wieman01 said:**
> '/dev/sda1' is your root file system, i.e. your Linux partition. And a file check is forced upon you after 28 restarts or so. That's a pretty common feature and is nothing you have to worry about. Read this for more:

[http://www.zip.com.au/~akpm/linux/ext3/ext3-usage.html]("http://www.zip.com.au/~akpm/linux/ext3/ext3-usage.html")

I got a similar message and the check halts, again and again, on different stages from 3,5% to 90%
How do I com out of this mess? Reinstall?

HP Pavillion dv9000seies, 2x180GB HD, dualboot, Vista on Disc1, Ubuntu 7.10 on disc2, other partitions on Disc2 in NTFS seems OK.

---

### Post by oldsmobile_mike on 2008-01-26
> **hpn909 said:**
> I got a similar message and the check halts, again and again, on different stages from 3,5% to 90%
How do I com out of this mess? Reinstall?

HP Pavillion dv9000seies, 2x180GB HD, dualboot, Vista on Disc1, Ubuntu 7.10 on disc2, other partitions on Disc2 in NTFS seems OK.

The linked-to instructions provide these instructions to disable checking:

[I]So it is a good idea to turn this feature off for ext3.  Use the command 
  
tune2fs -i 0 -c 0 /dev/hdxx
To disable the checking. 

NOTE: this means that it is your responsibility to periodically schedule downtime for the manual checking of disks.  In many Linux distributions this is most easily done by creating a file called /forcefsck and rebooting[/I].

However, you might want to investigate what's causing your checks to halt...

---

### Post by hpn909 on 2008-01-26
I would do this if I knew how to stop the check before disabling it.

I cant find how to do that.

BTW, thanks for trying to help.

---

