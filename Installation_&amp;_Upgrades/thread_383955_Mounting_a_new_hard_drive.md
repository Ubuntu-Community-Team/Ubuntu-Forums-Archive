---
title: "Mounting a new hard drive"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by Sturm on 2007-03-13
I'll be adding a 500GB hard drive soon to my Edgy installation and I plan to mount it as /media, after which I'll move all my music and such over there. Is there anything I should know in advance before I add this new HDD? Would it be advisable to just do a clean install of Ubuntu? Thanks, and take care!

---

### Post by aidanr on 2007-03-13
no, a clean install is not neccessary, a couple of things to note though

a) the new drive will need to be formatted before you can use it, you can use gparted for this
b) to have the drive mounted at boot, you'll have to add it to /etc/fstab
c) the drives name depends on its connection, eg. ide primary master is hda, ide primary slave is hdb, secondary master is hdc, secondary slave is hdd, sata1 is sda, sata2 is sdb etc. etc.

---

### Post by raverdack2 on 2007-03-14
Hi I am also doing this to my Ubuntu box.  I am new to Ubuntu, having just started using it four days ago.  I have a 250gb drive that I had as an external previously.  I believe it is formatted to FAT32 and it currently has all my media on it.  Is there an easy way I can get Ubuntu to recognize it and all that is on the drive as well?  Can you elaborate on the formatting process?  Thanks!

---

### Post by wonk-o-matic on 2007-03-14
Don't re-install!  Just use gparted to partition the drive (if it isn't already partitioned) and format it (ext3.)  

You might want to create a directory under /media, and mount your drive to that.  A lot of devices get mounted to /media, like /media/cdrom.  So something like /media/music might be better.

---

### Post by Sturm on 2007-03-14
> **aidanr said:**
> b) to have the drive mounted at boot, you'll have to add it to /etc/fstab

Okay, I'm gonna need some help on that.  What should I put in there, and where?

> c) the drives name depends on its connection, eg. ide primary master is hda, ide primary slave is hdb, secondary master is hdc, secondary slave is hdd, sata1 is sda, sata2 is sdb etc. etc.

Hehehe...   When I said I was installing a HDD, I meant "Hard Disk Drive," actually.  My apologies for the confusion.  Actually, it will be the second SATA drive that I will have installed in this box, so I'm assuming it will be sdb.  I haven't decided if I should split it into two 250GB partitions yet (sdb1 & sdb2, presumably).  If I do, I'll make one /media, but I don't know what to make the other...  Anyway, thanks for the reply!

---

### Post by aidanr on 2007-03-14
@raverdack2

do not format it or you will lose all your media, it is already formatted fat32

and the info you need to mount it is [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

---

### Post by Sturm on 2007-03-14
> **raverdack2 said:**
> Hi I am also doing this to my Ubuntu box.  I am new to Ubuntu, having just started using it four days ago.  I have a 250gb drive that I had as an external previously.  I believe it is formatted to FAT32 and it currently has all my media on it.  Is there an easy way I can get Ubuntu to recognize it and all that is on the drive as well?  Can you elaborate on the formatting process?  Thanks!

As far as I know, Ubuntu understands FAT32 drives perfectly.  When I first installed it on my SATA hard drive, it automatically saw and mounted my IDE drive with NTFS.  As for how to get Ubuntu to recognize and mount a newly-added FAT32 drive is beyond my knowledge.  Surely one of the gurus here will help you out with that.  I imagine it would be relatively easy and painless.

> **wonk-o-matic said:**
> You might want to create a directory under /media, and mount your drive to that.  A lot of devices get mounted to /media, like /media/cdrom.  So something like /media/music might be better.

Thanks for the advice!  I think you just solved my dilemma of what partitions to make on my new 500-gigger.  I'm thinking one for /media/music, one for /media/images, and one for /media/videos.  Perhaps others, too, if I can think of any.  Thanks again!

---

### Post by aidanr on 2007-03-14
> **Sturm said:**
> Okay, I'm gonna need some help on that.  What should I put in there, and where

/dev/sdb1	/media/Music 	ext3 	defaults,errors=remount-ro 	0 	1

position doesn't matter, should be on it's own line though i think

---

### Post by Sturm on 2007-03-14
> **aidanr said:**
> /dev/sdb1	/media/Music 	ext3 	defaults,errors=remount-ro 	0 	1

position doesn't matter, should be on it's own line though i think

Sweet!  Thank ya!

---

### Post by raverdack2 on 2007-03-15
thanks for the help!
i'll try that and let you know if i have more questions

---

### Post by bukdor on 2007-03-16
Hey, I'm working on Ubuntu Server, and just wanted to know if someone can help me mount a secondary hard drive, partition it and what not?

---

### Post by geirha on 2007-03-16
> **aidanr said:**
> /dev/sdb1	/media/Music 	ext3 	defaults,errors=remount-ro 	0 	1

position doesn't matter, should be on it's own line though i think

Almost. That's the options you would use for the root ( / ) partition. Every other partition with ext3 should have a line like this:
```
/dev/sdb1 /media/music ext3 defaults 0 2
```

More specifically, only the root-partition needs the **errors=remount-ro** option, and the last field determines which drive should be checked for errors first during boot. The root partition should be checked first, then the other partitions in any order, thus every ext3-partition other than / should have 2 on the last field
.
Windows partitions like vfat, ntfs and ntfs-g3 should have 0 on the last field... leave filesystem checking of windows paritions to windows, and linux partitions to linux. ^ ^

---

### Post by geirha on 2007-03-16
And as a sidenote, gnome (and probably kde too) regularly checks /media/ for mounted partitions. If it finds a mounted partition there, it will put a harddrive-icon for it on the desktop. This is probably something you want, but in case you don't, you should mount it somewhere else, like /mnt/music for instance.

---

### Post by aidanr on 2007-03-16
thanks dude, learn something new every day:)

---

### Post by Sturm on 2007-03-17
I'm just about ready to create the partitions...  I've chosen to make one for images, one for videos, one for music, one for packed files (drivers, utilities, and other things DLed from the internet), and one for miscellaneous stuff.

Should I make them all Primary partitions, or Logical Drives in an Extended Partition?  And what are the ups and downs of both types?

---

### Post by Kateikyoushi on 2007-03-17
The difference is that you can have maximum 4 primary partitions and extended counts as one, so if one day you want to make more partitions for whatever reason an extended one might be better.

---

### Post by Sturm on 2007-03-17
Thank you, Kateikyoushi...

I made an extended partition with five logical partitions in it.  Now, how do I mount them?  I know from geirha's post that I should add some lines to /etc/fstab in order to mount them at boot-time.

Does that mean that it is entirely possible to have drives with data on them and, if those lines are not in /etc/fstab, they are completely inaccessible until they are mounted manually?  (Or until /etc/fstab is edited)

I was expecting Ubuntu to ask me where to mount the new partitions, then do so automatically for me after creating them in GParted, since Ubuntu is meant to be the easiest Linus OS out there ("it should 'just work'").  But I guess adding a new hard drive isn't exactly a newbie's activity, just like networking with Windows computers, which is why each requires manually editing a system file.

---

### Post by Kateikyoushi on 2007-03-17
Yes the drives are not accessed until you mount them either manually or upon boot.

To mount them show us the partition laytout and your fstab.
Copy these to terminal and post the output.

```
sudo fdisk -l
cat /etc/fstab
```

Thanks for commenting what is hard for beginners we want to know your opinion to improve the OS, but I think it won't make it into ubuntu in the near future.

---

### Post by Sturm on 2007-03-17
> **Kateikyoushi said:**
> To mount them show us the partition laytout and your fstab.

Alrighty, then.  For fdisk:

```
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         255     2048256    b  W95 FAT32
/dev/hda2             256       10011    78365070    f  W95 Ext'd (LBA)
/dev/hda5             256       10011    78365038+   7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2           14202       14593     3148740   82  Linux swap / Solaris
/dev/sda3            1306       14201   103587120   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    5  Extended
/dev/sdb5               1       13054   104856192   83  Linux
/dev/sdb6           13055       26108   104856223+  83  Linux
/dev/sdb7           26109       39162   104856223+  83  Linux
/dev/sdb8           39163       52217   104864256   83  Linux
/dev/sdb9           52218       60801    68950948+  83  Linux
```

and for fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0c8c7366-389e-4ab0-bb31-9ef122f0d5b9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=eb3061e1-55b1-4df8-bacf-39216a3cb69d /home           ext3    defaults        0       2
# /dev/hda5
UUID=000000003FE34EEB /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=1da8589a-c774-4986-b117-c2998460e631 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

So there ye have it.

> **Kateikyoushi said:**
> Thanks for commenting what is hard for beginners we want to know your opinion to improve the OS, but I think it won't make it into ubuntu in the near future.

Quite alright.  In my mind, I'm just comparing the process to how it's done in Windows.  In version XP of that OS, you have a graphical interface via the "Manage My Computer" dialog, where you can see all the physical drives connected.  Then you just choose format from the right-click menu on the new drive and it takes care of the rest, including assigning it a drive letter.  And that, too, can be changed from within the same dialog.

---

### Post by geirha on 2007-03-17
sdb5 is the first logical partition, so
```

/dev/sdb5 /media/video ext3 defaults 0 2
/dev/sdb6 /media/music ext3 defaults 0 2
/dev/sdb7 /media/images ext3 defaults 0 2
/dev/sdb8 /media/archives ext3 defaults 0 2
/dev/sdb9 /media/misc ext3 defaults 0 2

```

something like that appended to /etc/fstab should do nicely. You can add some  spaces to make it look nicer if you like.

you should also create the mountpoints first. ```
sudo mkdir /media/{video,music,images,archives,misc}
```
...or whatever mountpoints you choose

---

### Post by Kateikyoushi on 2007-03-17
Do as geirha wrote.
To edit the file copy or type this to terminal.
```
gksudo gedit /etc/fstab
```

---

### Post by geirha on 2007-03-17
> **bukdor said:**
> Hey, I'm working on Ubuntu Server, and just wanted to know if someone can help me mount a secondary hard drive, partition it and what not?

Completely missed your post earlier. 

These steps should work fine on any of the ubuntu releases as far as I know, so maybe you've gotten all your questions answered allready?

---

### Post by Sturm on 2007-03-17
Got the partitions formatted and mounted, as geirha suggested.  There were even shortcuts to each of them placed on the desktop.  Now I'm ready to move all my media to them, but they don't seem to let me do so.  Every time I try to copy or move data to them, I am told that I do not have permission to write to that folder.

When I right-click on each of the new folders (they look like separate drives in the File Browser), I am not given a choice to look at its Properties, so I cannot see any way to change the permissions.  Lil' help?

---

### Post by bukdor on 2007-03-17
> **geirha said:**
> Completely missed your post earlier. 

These steps should work fine on any of the ubuntu releases as far as I know, so maybe you've gotten all your questions answered allready?

That's ok.

I'm trying to do the same thing, installed a second hard drive, but doing it via SSH session.  Because the machine is in a different country.

Should I use fdisk or parted?

And what steps should I take?  Sorry, complete n00b.

---

### Post by Bohica032 on 2007-03-17
> **aidanr said:**
> @raverdack2

do not format it or you will lose all your media, it is already formatted fat32

and the info you need to mount it is [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

O.K. i tried that link and did everything it tells me to do to mount the new HDD.  My new HDD is NTFS formated and it has stuff on it, but the system tells me that I do not have permissions for the drive.  So I just want to reformat this HDD so it will work with Ubuntu.  No matter what I try, even though I'm logged in as administrator (owner) I still get an error that i do not have permissions.

How do I format the HDD so it will work as extra space?

By the way I started to use Linux/Ubunto as of yesterday for the first time.  Total green horn here.

Please HELP

---

### Post by geirha on 2007-03-17
> **Sturm said:**
> Got the partitions formatted and mounted, as geirha suggested.  There were even shortcuts to each of them placed on the desktop.  Now I'm ready to move all my media to them, but they don't seem to let me do so.  Every time I try to copy or move data to them, I am told that I do not have permission to write to that folder.

When I right-click on each of the new folders (they look like separate drives in the File Browser), I am not given a choice to look at its Properties, so I cannot see any way to change the permissions.  Lil' help?

Sorry, forgot about that. Typically only root will have write permission to them (and everyone else only read-only permission). Depending on who should have write permission to them there are several choices.

1. Only your user should be allowed to have write access:
Change ownership on them (from a terminal):
```
 sudo chown **your-username** /media/{video,music,images,archives,misc}
```

2. More than one user should be allowed to have write access:
Create a group that will be allowed to access the drives. You do this through System->Administration->Users and groups. The name of the group doesn't matter much, let's say you call it _files_. Add all users that should be allowed to have write permission to that group, then issue these commands:
```

sudo chgrp _files_ /media/{video,music,images,archives,misc}
sudo chmod g+w /media/{video,music,images,archives,misc}

```
which means, 
change group ownership to _files_ on the given directories
give group-members of the given directories write-permission.

3. Same as 2, but no one else should have either read or write permission:
do step 2, then this:
```

sudo chmod o-rwx  /media/{video,music,images,archives,misc}

```

Those would be the most common ones, there are more options available, so ask if you want to know more (if you want to read yourself, you should run **man chown**, **man chgrp** and **man chmod**.

---

### Post by geirha on 2007-03-17
> **bukdor said:**
> That's ok.

I'm trying to do the same thing, installed a second hard drive, but doing it via SSH session.  Because the machine is in a different country.

Should I use fdisk or parted?

And what steps should I take?  Sorry, complete n00b.

Through ssh, either is ok, but I'm used to fdisk, so I'll try to go through the steps using that:

First of all, you should know which drive it is you are going to work on. It's probably /dev/sdb if you have only SATA or SCSI disks, or /dev/hdb or /dev/hdc if you only have old ATA disks. **sudo fdisk -l** shoud give you a clue, the new disk will most likely have no partitions.

As for partitioning using fdisk. I don't know how you want to partition it. If it's 3 or less partitions, then you do like this (assuming your disk your new disk is sdb):
```

sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 

```
you're using grub, so ignore such warnings ;)
```

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)

```
p<enter>, then answer 1 to create the first primary partition (which you will be able to use as /dev/sdb1)
It will then ask where it should start, just hit <enter> for the first available sector.
Then it will ask you how big it should be. Type **+100000M** if you want it to be 100GB (100,000MB) or <enter> to use all space available.
If you want to make more, repeat these steps to make primary partition 2 (/dev/sdb2). 
If you want to make more than four, make sure to make an extended partition, then make logical paritions on the extended partition. Have a look at [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html) for a more detailed explanation.
end by typing **w** to write the partition table (if you did something wrong, just type q to quit without saving)
```
 Command (m for help): w 
```

After partitioning you need to format. do:
```
sudo mke2fs -j /dev/sdb1
```
for each partition to format them as ext3

Then you should be able to mount them by reading this thread ;)

---

### Post by Sturm on 2007-03-18
Thank you, geirha...  I tried changing /media's permissions first, just to see what would happen, and it was, indeed, seen by my Windows systems.  But I didn't particularly like the way all of the server's cdrom and floppy drivers were showing up there, as well, so I changed it back and, instead, tried sharing & changing permissions on /media/music, as a test sample.

I was able to copy files to it, thankfully, but now it won't show up on my Windows systems.  Perhaps I am not being patient enough and need to wait or something.  But I have a feeling there is something not set up right.  Oddly enough, my test folders under my home directory share just fine...  (See [Sharing my Ubuntu folders with Win XP]("http://ubuntuforums.org/showthread.php?t=379873"))  Strange how stuff in /media won't work.

Also, should we break off this thread and start a new one in a more appropriate place?

---

### Post by geirha on 2007-03-19
Indeed, can't think of any reason why that should happen. Is it only the windows box that can't see them though? how about nautilus, if you go to smb://hostname/music for instance...

how do the share sections look in /etc/samba/smb.conf (one that works and one that don't)?

what's the permissions like? **ls -ld /media /media/music ~/the-working-test-share**

And yes, I guess it's turning a bit off topic, so it'll probably help to put this new problem in a new thread, but post an url to it in here if you do ;)

---

### Post by Sturm on 2007-03-20
Thank you for replying, geirha....

Actually, I may have forgotten to mention that I had deleted several of the 'links' to shared folders in Windows' "My Network Places."  It turns out to be a quirk of Windows that it will not re-detect shared folders on the network once you've manually deleted the links to them--you must *force* it to do so.

I described the problem and discovered the answer, which I posted on my other thread, [Sharing my Ubuntu folders with Win XP]("http://ubuntuforums.org/showthread.php?t=379873").  Check out that link if you want to know how I forced Windows to re-detect shared folders.

Also, once I had everything set up the way I wanted it, I ran into the problem again of iTunes not being able to download any new podcasts, telling me that I didn't have enough access privilidges.  It was the same problem I discussed much earlier in [access privileges in iTunes]("http://ubuntuforums.org/showthread.php?t=381923").

Only this time, I couldn't just change the permissions of the /media folder to allow drwxrwxrwx, either.  I tried and it didn't work.  Fortune, however, eventually came to my side when I tried a last ditch effort--restarting Samba.  Once restarted, iTunes started downloading podcasts again without bugging me about access priviliges!

Now, let's hope this is the last time I'll need to post to this thread (or the entire forum, for that matter) describing problems that I'm having.  Cheers!

---

### Post by geirha on 2007-03-22
Nice to hear you got it all figured out :)

---

### Post by Sturm on 2007-03-22
Nope, iTunes got finicky again.  One day, I was able to download podcasts fine.  The next, it tells me I don't have enough access privileges.  But we don't have to discuss the problem here--I already have a discussion started at [access privileges in iTunes]("http://ubuntuforums.org/showthread.php?t=381923").  No replies yet, unfortunately.

---

### Post by DarinB on 2007-08-11
I installed ntfs-g3 and ntfs config tools but when i reboot the internal fat 32 partition doesn't automatically mount i have to mount it manually. which sucks since i have 60 gigs of music i want to use with rhythmbox
when i tried to gpart another partition to ext 3 it came up lost and found and unaccessible so i converted it to ntfs and moved my docs over to it. I'm a newbee please help i want make this work so i can get away from Bill Gates, long live Ubuntu

---

### Post by merlinus on 2007-08-11
ntfs-3g does not work on fat partitions, only ntfs.

Post output of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

