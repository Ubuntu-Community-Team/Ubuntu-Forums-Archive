---
title: "understanding partitions"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by TheFaction20 on 2006-03-27
> For multi-user systems or systems with lots of disk space, it's best to put /usr, /var, /tmp, and /home each on their own partitions separate from the / partition. 

You might need a separate /usr/local partition if you plan to install many programs that are not part of the Ubuntu distribution. If your machine will be a mail server, you might need to make /var/mail a separate partition. Often, putting /tmp on its own partition, for instance 20 to 50MB, is a good idea. If you are setting up a server with lots of user accounts, it's generally good to have a separate, large /home partition. In general, the partitioning situation varies from computer to computer depending on its uses. 


from: [http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apbs03.html](http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apbs03.html)

im an ubuntu noob and a linux noob in general. im trying to understand this section with the "/" which i know is root, "/usr","/home", etc.

are these things already created? or do i have to make these? if so where do i make them?

---

### Post by Sef on 2006-03-27
> this section with the "/" which i know is root, "/usr","/home", etc.

are these things already created? or do i have to make these? if so where do i make them?

The default install will just do a fat32 and a swap of 512.  

It is good to have the following partitions:

root, fat32, home, and swap.  

If you have a home partition, you can install or reinstall the os and not lose any documents, which are saved in home.

---

### Post by TheFaction20 on 2006-03-27
can you possibly explain a little more for me? im not sure if i understand. how do i set up those partition types?

---

### Post by Sef on 2006-03-27
Sorry,  i had meant to put in this link:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by munga_bill on 2006-03-27
You might be the system administrator for a large central server and you may need to strictly control the amount of data many (anonymous) users store in various parts of the system. In the old days the computers Unix and Linux began on were like that. The ability to make many rigid partitions can help contain and limit groups of (potentially) unruly users. 
Another problem was the old ext2 file system, which was non-journalling, so you could loose data if it crashed or was shut down incorrectly.
There was also  the 8 GB BIOS limit in the old days too, where a computer needed the boot loader to be installed on a partition inside the 8 GB BIOS limit so the computer would boot Linux which might be installed outside the area on the disk that was useable by another operating system.  
Nowadays with the nice modern personal computers we have now, we are free of all those problems and their work-arounds, so we can have the luxury of installing Linux on just one main /  partition and a small swap area. This is better in lots of ways, it makes for easier installing and a more flexible system. Folders can shrink or grow automatically according to the amount of data you put in them, where partitions can't. This is more convenient than having to stop what you are doing to re-size a partition so you can record a CD or something for example if you found you made a mistake in partitioning and didn't leave enough room where the CD data needs to be spooled.:oops:
With a nice simple single-partition (plus swap area) install you can have a much tidier hard-disk if you decide to multi-boot too. With modern day partitioning software it is even doubtful whether a seperate /home is really needed, since you can so easily copy and paste a spare copy of your entire Ubuntu install to an area at the end of your disk, added software and tweaked settings and all with GParted LiveCD in case you trash your current system. Restoring is just copy and paste now for the whole installation. 
Whatever partitioning schemes you decide to try out, have fun and enjoy yourself, Ubuntu is lots of fun and there is lots to learn. Regards, munga_bill

---

### Post by cls1chuck on 2006-03-29
so - what is the best partition type to create for installing my Linux to? (NTFS, fat32, linux swap, etc.)?  Are there pros/cons to the various types?  FYI, I have XP on an NTFS partion on the same disk now.  I'd like to 'pull' data (files) from XP in to Linux as I become more comfortable w/Linux.  And I'm trying to do this using gparted.

76GB HD; 30GB is XP (ntfs); 46 is free (I should probably set up a swap partition too, huh)?

---

### Post by Sef on 2006-03-29
> so - what is the best partition type to create for installing my Linux to? (NTFS, fat32, linux swap, etc.)? Are there pros/cons to the various types? FYI, I have XP on an NTFS partion on the same disk now. I'd like to 'pull' data (files) from XP in to Linux as I become more comfortable w/Linux. And I'm trying to do this using gparted.


For the os itself, FAT32, for root and home resfiers (or ext3), for swap swap.  Linux can't write to NTFS, only read it.  

For sharing files, create a ext2 extension.  Both Windows and Linux can read and write to it.  

If you are working on a big document like a book or a dissertation, resfiers is better, otherwise not much difference.  

Gparted works well.  It is on the install disk too.

And by the way, cls1chuck, it would be best to start your own thread.  Otherwise it looks like your hijacking the thread here. (Which I don't believe is your intension.)

---

