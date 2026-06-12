---
title: "Re partitioning, external HDD, comfused"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by obidose on 2008-04-25
OK, This is a little complicated (to me at least) so bear with me.

I currently have: main hard disk in laptop (divided into 4 partitions 2 visible and 2 not I assume they are restore type things) the main hard disk contains all of vista and is basically untouched since factory settings.

                  Second HDD (external USB 500gb) has 3 partitions (its original storage partition containing my msic video etc used by both windoes and ubuntu, Ubuntu ext3 partition, and linux swap partition)


I have 2 problems with my current set up:

1) When ubunu resized the original partition on my external drive it took way too much of the drive for the home partition and left a pesky amount for my common storage.

2) The grub loader is installed on the external hdd in the home partition I think, this means I can't boot up without this HDD in place.


I am thinking of either wiping all the hdd partitions apart from the storage one and starting ubuntu install from scratch. This method has the major advantage of leaving my vista hdd basically untouched = low risk. If I did this how could I ensure that the grub loader was on my internal HDD?

Or I was thinking of installing Ubuntu on to my internal drive along with vista and then just reverting the external drive to a storage drive. However as my internal hdd has so many partitions allready I am very confused about the partitioning of it and also worried about resizing the vista partition (last time I resized a partition with an os on it Gparted crashed midway through and I spend hours fscking the drive to fix it) any help for this plan?

Which plan do you think is preferable? and help please.

Hope this is clear.I tried searching the forums couldn't find anything directly helpful (lot's of new instsallation threads at the moment)

---

### Post by obidose on 2008-04-25
Also I am worried if I just delete the partition with grub on it, that the information pointing to my vista install will disappear with it. Is this the way it works or can grub just find all the installed OS when it is installed?

---

### Post by martrn on 2008-04-25
> **obidose said:**
> OK, This is a little complicated (to me at least) so bear with me. I currently have: main hard disk in laptop (divided into 4 partitions 2 visible and 2 not I assume they are restore type things) the main hard disk contains all of vista and is basically untouched since factory settings.

You mean they are hidden to wWINDOWS  (4 partitons of NTFS).

> **obidose said:**
> Second HDD (external USB 500gb) has 3 partitions (its original storage partition containing my msic video etc used by both windoes and ubuntu, Ubuntu ext3 partition, and linux swap partition

So you also have a 500gb removable storage device with 3 partitions.

> **obidose said:**
> I have 2 problems with my current set up: 1) When ubunu resized the original partition on my external drive it took way too much of the drive for the home partition and left a pesky amount for my common storage.

The only way you can resize this partition is through gparted live distribution or a live distribution running from a cd, or other external storage device.  It works quite well (gparted) but do not run gparted from the distribution you are currently running.

> **obidose said:**
> 2) The grub loader is installed on the external hdd in the home partition I think, this means I can't boot up without this HDD in place.

Grub (the boot loader) is stored in a master boot record and in not stored in ANY partition home or otherwise.  It does load some files from a linux partition and looks for a directory called /boot/grub.  

> **obidose said:**
> I am thinking of either wiping all the hdd partitions apart from the storage one and starting ubuntu install from scratch. This method has the major advantage of leaving my vista hdd basically untouched = low risk. If I did this how could I ensure that the grub loader was on my internal HDD?

I would not advise this with removable storage, and not a good idear.  Installing grub as a master boot record to boot into a removal drive with some files on a linux partition at a place called /boot/grub will lead you to be unable to boot, anything, if the removable drive is removed.

> **obidose said:**
> 
Or I was thinking of installing Ubuntu on to my internal drive along with vista and then just reverting the external drive to a storage drive. However as my internal hdd has so many partitions already I am very confused about the partitioning of it and also worried about resizing the vista partition (last time I resised a partition with an os on it Gparted crashed midway through and I spend hours fscking the drive to fix it) any help for this plan?


The maximum amount of partitions, you can have on a disk is 4, however you can have more if you create an extended partition and store extra partitions in that.  The more partitions you have the more confusing it will get.  I recommended heaving one partition on each disk and having one disk for vista and one disk for ubuntu.

> **obidose said:**
> Which plan do you think is preferable? and help please.  Hope this is clear.I tried searching the forums couldn't find anything directly helpful (lot's of new installation threads at the moment)

Its clear that you are not sure what to do, but its your choice about what partitions you have where.  You are the one that has run the system on a daily or weekly basis.  If you are re-partitioning your drive you are going to have to run a live distribution of gparted to re-partition your drives whatever you do.  Even though it failed once it shouldn't a second time, and if you plan it, it should go smoothly.  Although as with all partitioning it is very risky business so you should always back up your data before hand, and I mean burn it to a cd or dvd or something in case things do go wrong.

---

### Post by obidose on 2008-04-25
> **martrn said:**
> 
> 
 Originally Posted by obidose  View Post
I am thinking of either wiping all the hdd partitions apart from the storage one and starting ubuntu install from scratch. This method has the major advantage of leaving my vista hdd basically untouched = low risk. If I did this how could I ensure that the grub loader was on my internal HDD?


I would not advise this with removable storage, and not a good idear.  Installing grub as a master boot record to boot into a removal drive with some files on a linux partition at a place called /boot/grub will lead you to be unable to boot, anything, if the removable drive is removed.



This is pretty much the situation I have now. I want to do it like that but maybe create a dedicated grub partition on my vista hdd so I can boot without the usb drive.

---

### Post by martrn on 2008-04-25
> **obidose said:**
> This is pretty much the situation I have now. I want to do it like that but maybe create a dedicated grub partition on my vista hdd so I can boot without the usb drive.

Look at [http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")

And Look at the section about how to use Windows Vista’s Boot Manager to boot Linux.

I would not install grub (if I were you) as a boot loader, to boot any system, whereby the linux /boot/grub directory will be or is possiable removed at any time.

It is oppertunity only for a head-ache.

---

