---
title: "Need help adding a new HDD"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Cooter2543 on 2010-05-15
I have a Seagate 500GB SATA hard drive, which contains my filesystem. I bought a new Samsung 1TB SATA hard drive that I would like to add. Being a noob at storage solutions, I would like some advice on how to proceed. 

It would be nice to add the new HDD so that I could deal with just one logical volume(?), but as I understand, I would have to delete everything from the 500GB HDD in order to do that, correct? I don't have any way to back up that amount of data, so that is not an option to me. Can this be done without deleting the existing HDD?

---

### Post by darkod on 2010-05-15
Uhhh... if you use only ubuntu (no windows), LVM is perfect for you. Just as you said, in short, in LVM you add all your physical storage and it's treated as single logical volume (or you can create more of them if you want). And the good thing is that you can resize partitions without formatting after that. At start you designate some space to /, /home, swap, etc, but later you can enlarge as needed.

However, I'm not sure you can change existing installation into LVM. If you are interested in using it, you might search if google turns up something about switching existing system into LVM.

Otherwise, one workaround would be: Install new ubuntu as LVM on your 1TB disk. Once you have it up and running, move your data from the 500GB disk.

After that delete the old ubuntu, and just add the 500GB to the LVM which would work. You can add disks later without any problem.

But depends if you have specific settings in your current ubuntu and how easy it is for you to make the new ubuntu the same. Otherwise I would seriously think about LVM.

Another solution doesn't come to mind.

Some basic info about LVM:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

NOTE: For LVM install you need to use the Alternate install CD, not the standard desktop image.

---

### Post by Cooter2543 on 2010-05-15
Thanks for your reply, darkod.

In LVM, in order to manage logical volumes, it wants me to 'initialize' partitions before creating a logical volume, which deletes all data on that partition. As I said, that isn't an option for me, because I can't backup 500GB of data. 

I've never setup a RAID array, but I understand that with a 1TB and a 500GB, you would only come out with 1TB of usable space in a RAID 0, so that's not an option either. 

The purpose of the new HDD is basically just for media storage. And I don't want my video/music library split between my home folder and a slave drive I have to re-mount all the time. 

Is there a way to do this without losing the current data, and/or dealing with a split library?

---

### Post by darkod on 2010-05-15
My idea was to install another 10.04 on the 1TB with LVM, if it's not too much bother for you, after that transfer your data across, and delete the old 10.04 and add the 500GB to the LVM storage.

As for the slave drive having to be re-mounted, you can easily set it up to mount at boot so you won't even notice it.

But of course, it would still be like separate data disk.

PS. LVM is the only way I am aware of to make two physical disks act as single logical volume, as you want. And you are right, setting up RAID with disks of different size will leave unusable space.

---

### Post by cascade9 on 2010-05-15
> **darkod said:**
> PS. LVM is the only way I am aware of to make two physical disks act as single logical volume, as you want. And you are right, setting up RAID with disks of different size will leave unusable space.

JBOD (just a bunch of discs) will do it as well, but you need a controller that supports it for that to work.

---

### Post by Cooter2543 on 2010-05-15
I suppose if there is no better way, I could install and transfer to the new hard drive. I guess having to re-customize my desktop is a small price to pay for having my whole media collection right in the home folder.

Thanks for your advice!

---

### Post by oldfred on 2010-05-15
You say you so not want your data elsewhere but you can and have it linked into your /home so it looks just like it is in your install.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Some people like to put an operating system on every drive:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I like to have an operating system on each drive and I alternate installs of Ubuntu between different root partitions. I have /home and /data in separate partitions as well so root is now only about 6GB, /home is just over 1GB and everything else is in /data.

---

