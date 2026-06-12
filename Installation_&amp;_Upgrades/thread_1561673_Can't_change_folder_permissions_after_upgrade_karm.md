---
title: "Can't change folder permissions after upgrade karmic to lucid (NTFS FAT32)"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by xapa on 2010-08-26
Hi there, I ran into a hard problem to solve regarding permissions. I've been searching around for similar cases (as I always do) but I thing i got into a dead end.

It all started like this:

I had my karmic working just fine, and I used to watch movies in my living room's media center through wifi. These movies were in three different partitions. A fat32 on a hitachi 200gb hdd(no boot), an 140gb NTFS with windows xp(which I didn't boot in years, using it just for storage), and ubuntu's ext3 with 16Gb. The NTFS partition and the ext3 are on the same 160gb WD Caviar hdd (both bootable). (and the swap partition which I'm ignoring)

Then I upgraded to lucid a few days ago. And to do that I had to free up 30Gb of space from the NTFS, to shrink it. I had to defrag it first because Parted Magic (Gparted) was having errors on simulation. After defrag, I did the shrinking and I gave ext3 26Gb.

//Problem starts here//

Then I did the upgrade to lucid, no trouble there.
And after booting and solving some graphics problems (during this I installed Grup-pc/Grub2), I noticed that Gnome Do wasn't mounting my NTFS and FAT drives (named CAVIAR and HITACHI respectively). So I mounted them manually, authenticating myself. And even that was strange because, as I wrote the pass and hit enter, the authentication thingy didn't close by itself, and the "Autheticate" button didn't change to gray, and kept itself "pressable". I closed the auth thingy, and the disks finally mounted.

But then...I tried to watch movies in the living room, and I had problems accessing the folders. So I went back to the computer to set the permissions again (sudo nautilus, just in case) and as I changed the "Others" permissions to "Access files" it changed back to "None"...same thing with Thunar. I even tried sudo chmod, with no results. I tried changing permissions on ext3 and all was fine.

All this while searching through forums for anything. I've found some similar cases but the solutions didn't seem to work. And I'm being a bit vague about this now because I did it two days ago and didn't keep track of it all.


I guess that the problem keeping Gnome Do from mounting the drives by itself is the same problem making the mount authentication thing act odd, and it is the same problem preventing nautilus and chmod from changing permissions.

Any thoughts on that?

Thanks in advance for reading all this. ;)
xapa

P.S: oh btw, I'm using ubuntu studio. forgot about that.

---

### Post by xapa on 2010-08-27
So...no one has any idea?

---

### Post by oldfred on 2010-08-27
Do not know about gnomedo, but NTFS or FAT partitions permissions and ownership are set at mounting. It is usually best mount in fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by xapa on 2010-08-27
Thanks a lot oldfred, I'll try setting up permissions editing the fstab file in a few moments. Although...I really want to find out the root cause for this problem. In karmic everything was fine, never had to touch fstab or anything.

But still thanks for your help oldfred, I'll post the results soon.

---

### Post by xapa on 2010-08-28
Ok so I checked fstab and the disks weren't there. So someone recomended I installed ntfs-config in order to put them on the table. 

I did that, selected Autoconfigure in ntfs-config, and the disks apeared in fstab. Next thing I noticed after rebooting was that the diks had been mounted on boot automatically. And then it was easy to configure permissions with sudo nautilus. I am watching movies in the living room now...but all this comes as a bitter sweet victory.

In karmic I wanted specifically to mount the disks by myself, at will. So I added noauto to both disks in fstab like this:

```
#Entry for /dev/sda1 :
UUID=38DC1198DC11520C	/media/CAVIAR	ntfs-3g	noauto,user,defaults,nosuid,nodev,locale=en_US.utf8	0	0
```

But despite the "user" option i wrote also, I can only mount them as root, not as user which is what I want. 

(I just want it to be like it was before.)


Do I have to change the owner? I've read it somewhere.
Or am I doing something wrong? And btw, how can I figure out what caused this?

(Changing owner with sudo nautilus doesn't work. Again, the option reverts back to what it was before, like the permissions at the beginning)

---

### Post by oldfred on 2010-08-28
I thought I had saved some links but I just have my notes. But I just mount NTFS with defaults and it works for me.

These will provide the additional detailed steps:
HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)
Auto mount NTFS Partition
[http://ubuntuforums.org/showpost.php?p=7342606&postcount=10](http://ubuntuforums.org/showpost.php?p=7342606&postcount=10)


Notes from various posts:
What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 0
EDIT: If you prefer to be the owner then you can also go with this:
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,uid=1000 0 0

The owner is root, but the the files/directories are writable by the plugdev(gid 46) group.

To grant write permissions for a user, add the user to the plugdev group:
sudo adduser username plugdev
where username is the login name of the user.
The mount point doesn't matter, you can mount the partitions anywhere in the file system. I would mount the partitions in /media (/media/XP and /media/NTFS), since this directories will show up in the Places menu.

To create the mount points in /media you need root permissions:
sudo mkdir /media/XP
Before mounting the partitions you may have to set the group ownership of the mount point:
sudo chgrp plugdev /media/XP

---

