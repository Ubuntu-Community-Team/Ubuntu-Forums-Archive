---
title: "How to combine two Linux partitions?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Endolith on 2008-03-24
I currently have a triple boot:

Win XP: 60 GB
Ubuntu Studio: 10 GB
Ubuntu Feisty: 10 GB

I spend 90% of my time in the regular Ubuntu partition, 10% in WinXP, and I never use Ubuntu Studio.  

I'd like to combine the two Linux partitions into one so that I can use all the space on them.  What's the best way to do this without losing my data?

1. Delete the Studio partition and resize the regular Ubuntu partition using gparted?
2. Backup all my files and settings from the regular partition and delete both and start from scratch?

The first would be easier if it actually works, but there's no guarantee it will work.  Partitions don't like their boot sectors to be moved, right?

The second would be the only alternative I know of if 1 can't work, but requires me to back up all my files and settings, including user accounts, root account, programs and settings that aren't installed by package manager, etc.

Also, Ubuntu Studio is not completely part of the normal Ubuntu repositories, right?  So I can install either and still get all the same programs and enhanced realtime kernel?

---

### Post by bigredradio on 2008-03-24
When you say Linux partitions, you mean you have the OS in only one partition? I would recommend not trying to combine them, but split them up more. You should have multiple filesystems for a linux system.

Since the "Ubuntu Studio" partition is already formatted, why not mount it up inside your current Ubuntu and just rm the files inside. No need to mess with the partition table. You can mount it as /home/username/Movies and use that space for movies or whatever. Keeping system resources and user data on separate filesystems is a good idea. Create a mount point somewhere and put a new line in your /etc/fstab file to mount it up upon boot.

---

### Post by Endolith on 2008-03-24
> **bigredradio said:**
> When you say Linux partitions, you mean you have the OS in only one partition? I would recommend not trying to combine them, but split them up more. You should have multiple filesystems for a linux system.

By what logic?  That would require me to predict how much space should be allocated to each component of the system, causing me to run out of space more easily than if I just used one big partition for everything except the swap.

> Since the "Ubuntu Studio" partition is already formatted, why not mount it up inside your current Ubuntu and just rm the files inside. No need to mess with the partition table. You can mount it as /home/username/Movies and use that space for movies or whatever.

I suppose.  But that's what I use my NTFS partition for these days.  Still requires me to keep track of how much of each partition is used up and move around files and manage them by hand so that I don't run out of space early.

> Keeping system resources and user data on separate filesystems is a good idea.

By what logic?


Oh.  Also, grub boots off the Studio partition, which is annoying, because every time the kernel changes on my main partition, I have to update the menu.lst manually.  Is there an alternative to this?  Like having the main partition chainloaded from the Studio partition so that its own grub is updated automatically?

---

### Post by bigredradio on 2008-03-24
There are a number of reasons for multiple filesystems. 

1) Less risk of an unbootable system due to filesystem corruption. If everything is on one filesystem, you run the risk. Keep system files (which do not change often) on a separate filesystem than user data (which does change often) limits your risk. Also, it's a lot easier to run fsck on a system that can at least get to a shell, then have to boot from some liveCD and try to do it. Remember the saying, Don't put all your eggs in one basket.

2) Faster reads/writes. Again, separating out stable data with (ever changing data) will cut down on non-contiguous storage. If you have a large disk where everything is in one filesystem, the data blocks are written throughout the entire disk. Since /boot / and /usr do not get many writes, the data will be written contiguous. However, /var constantly is changing removing adding files. This fs is best left on its own in a small segment of the disk so that the read/write head is not skipping all over the disk.

3) You can use different filesystem types for different purposes. ext3 is good for stability, reiserfs is good because you can extend or grow the fs without umounting it. You might use xfs on very large filesystems. Or you might want to mount some read-only or encrypted.

The issue of how much space to use in each filesystem was solved with LVM. It kills me to see systems using LVM, with everything in one LV that takes up all of the space in the volume group. Logical volumes should only be as big as needed at the time (with a little growing room). Then if you run out of space, you just extend the logical volume and filesystem to meet your needs. If you run out of disk space, you can add more disks and extend the filesystems some more. You use the disk space efficiently and the back-end makes sure the data is written efficiently to the disk blocks. 

As far as your grub issue, the grub executable is looking for the first filesystem it can get access to that contains a grub/menu.lst file. If you remove/rename it from the studio install, it should locate the one on the standard install. The grub executable that sits in the MBR does not know anything about the conf file. It has to go find one.

---

### Post by Endolith on 2008-03-24
If splitting into multiple partitions were that important, it would be built into the default Ubuntu install.  I'm going to keep everything on one partition and not ruin my system by trying to tweak it.

---

### Post by bigredradio on 2008-03-24
> **Endolith said:**
> If splitting into multiple partitions were that important, it would be built into the default Ubuntu install. 

That is one of my biggest complaints about Ubuntu. I understand why they do this. It is because the majority of Ubuntu converts are coming directly from Windows. They are catering to what users know. However, I see this as "the good being the enemy of the best". I come from a Unix background where multiple filesystems is the norm. Systems administrators have known this for years.

> **Endolith said:**
> I'm going to keep everything on one partition and not ruin my system by trying to tweak it. 

I understand your point. I wish you the best.

---

### Post by Endolith on 2008-03-24
> **bigredradio said:**
> That is one of my biggest complaints about Ubuntu. I understand why they do this. It is because the majority of Ubuntu converts are coming directly from Windows. They are catering to what users know. However, I see this as "the good being the enemy of the best". I come from a Unix background where multiple filesystems is the norm. Systems administrators have known this for years.

Are you sure that's why?  I'm sure there are discussions about it on mailing lists.  Try proposing it on [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/).

I'd bet the benefits of splitting partitions  aren't really that great compared to the simplicity of maintaining one.  Since it's hard to predict the correct size for each partition, you'd use LVM, as you mentioned, but that's even more complexity, and actually makes it harder to recover from a filesystem error, no?

---

