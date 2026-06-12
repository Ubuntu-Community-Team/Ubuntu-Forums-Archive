---
title: "Creating new partitions"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by pcal on 2010-08-26
I have a 10.04 64bit install, and want to re-organize the partitions. Specifically, I want to move /user to a separate partition to make future upgrades easier than the last one was.

Is it possible to simply compress the existing root partition, split it in 2, and move the /user portion of the filesystem to the newly created partition?

Presumably there would be some other settings required to keep it all in sync.

If it can't be done that simply, would it work by adding a fresh install of the base system to the root partition after moving the /user data as above?

If that bombs out as well, is there some other way I can preserve the existing /user data while ending up with it in a separate partition?

Many Thanks,

Pcal

---

### Post by arubislander on 2010-08-26
What I did the last time I wanted to move my /home to a different partition was:
1. Backup all my valuable data
2. Boot from a LiveCD
3. Create a new partition to house my /home (I had enough space)
4a. Mount the root partition to ~/oldroot 
4b. Mount the home parition to be in ~/newhome
(create the directories if they dont exist)
5. Copy everything from the old ~/oldroot/home directory to the newly created partition taking care to preserve all permissions. I think I used rsync
6. Add an entry in ~/oldroot/etc/fstab for the new /home partition. The entry should say /home as the mount point, not ~/newhome!
7. Reboot

If all went well you should now be working in your new /home directory. If this is so you can delete the old /home folder on the root partition and shrink the root partition. (You'll have to reboot with a LiveCD to do this)

If you have any problems with any of the steps report back... someone is bound to help.

---

### Post by srs5694 on 2010-08-26
Linux doesn't use a partition called /user by default. I suspect you mean /home, which is where users' home directories reside. (This function is filled by a directory called /user on some Unix-like OSes.) If you mean /usr, which is where most user programs reside, moving it to a separate partition won't really help with system upgrades, but splitting it off can be useful in other ways.

You may want to check [this article](http://www.ibm.com/developerworks/library/l-partplan.html) for an outline of how to split /home off on its own partition. It's a bit elderly (it uses ext2 as the target filesystem type!), but I believe it would still work. You might need to add some partition resizing operations, depending on your current layout.

---

