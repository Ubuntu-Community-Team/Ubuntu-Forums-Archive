---
title: "Moving ubuntu install or &quot;remastering&quot;?"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2012-06-28
I have a fairly fresh Ubuntu 12.04 install that I have been tweaking to my liking, but it is in a small partition (10GB) at the end of a 150GB drive. The main part of the drive is a Windows NTFS partition.

I am considering my options to get Ubuntu running in a larger partition. I have already used gedit to shrink the original ntfs partition to get the 10GB I am now using.  I could shrink it further, but can I then just expand the 10GB partition, or will that upset the ubuntu install that's on there? This would be the easiest way by far if it will work.

Alternatively, can I create (remaster?) a new install disk, based on the existing install, then just re-install Ubuntu after I enlarge the partition?  Is there a good utility program to do this?

Lastly, could I move the install, as per these instructions -
[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)
to an external drive (then maybe back again later), but that seems like a lot of work?

---

### Post by oldfred on 2012-06-28
You can shrink the NTFS partition, but still need lots of free space in the NTFS partition for Windows to work well. Often 30% free is suggested.

But you have to move the Linux partition left and then expand right. Moves are always a bit more dangerous as any power failure or other interruption can cause major partition corruption. So good backups are always recommended.

If you have room you can shrink the NTFS and move /home leaving the / (root) in the current 10GB as /home is the partition that will expand the most.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I actually believe in separate installs on each drive. Your user settings & data are in /home so you can just copy it to the new install and it will be the same. Only if you had to make a system (for hardware) setting or two would you need those from /etc (like special wireless or networking settings).

---

### Post by ubnewbie2 on 2012-06-29
> **oldfred said:**
> You can shrink the NTFS partition, but still need lots of free space in the NTFS partition for Windows to work well. Often 30% free is suggested.

But you have to move the Linux partition left and then expand right. Moves are always a bit more dangerous as any power failure or other interruption can cause major partition corruption. So good backups are always recommended.

So grub let's you move a partition as well as expand it, and as long as no errors occur, the linux(Ubuntu) install will still work normally after being moved left and expanded right?

> **oldfred said:**
> 
If you have room you can shrink the NTFS and move /home leaving the / (root) in the current 10GB as /home is the partition that will expand the most.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


Or I could move the /home data to the new partition, then mount the new partition at /home as a mount point (or is that what you meant?).

> **oldfred said:**
> 
I actually believe in separate installs on each drive. Your user settings & data are in /home so you can just copy it to the new install and it will be the same. Only if you had to make a system (for hardware) setting or two would you need those from /etc (like special wireless or networking settings).

Part of the reason I wanted to move the lot is there are probably other things - at least I know I have changed fstab and the grub config, and it would be nice to not have to re-install all the extra apps that I have added.

Anyway, thanks for the help - appreciate it!

---

### Post by oldfred on 2012-06-29
Normally moves do not change UUID and now both grub2 & fstab work off UUID not device settings like /dev/sda1. Sometimes changes become too much and you do have to update settings or reinstall grub, so it always pays to have current liveCD or USB to be able to reinstall grub2's boot loader or edit fstab.

Depending on how you copy from one drive to another, can cause major issues on grub, fstab & some other settings. UUID has to be unique and system uses UUID to boot. So  if a drive is imaged as backup that is ok, if not mounted normally. But duplicate UUIDs will cause major issues on a imaged drive if also mounted.

If data is just copied to a new drive then you have to update all UUID settings in Ubuntu to use the new UUIDs. Often just easier to reinstall & copy /home over.

---

### Post by ubnewbie2 on 2012-06-29
Wanted to thank you again, as I have successfully shrunk the ntfs partition, created a new partition, copied the ubuntu install to it, deleted the old partition, and expanded the new one into that space, all using gparted.

The only problem was that grub2 couldn't see the new partition, so I had to mount it while booted from the live cd and 

grub-install --root-directory=/mnt/xxxx /sda

but all is working well now!!

---

