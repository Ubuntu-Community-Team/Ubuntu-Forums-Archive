---
title: "LVM help"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by umbernaut on 2011-12-30
I have installed Ubuntu 10.04.3 and did LVM2 from the install -- basically let it make it all.

Here my output of df -h:

root@server1:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/server1-root
                      396G  1.5G  375G   1% /
none                 1000M  248K 1000M   1% /dev
none                 1005M     0 1005M   0% /dev/shm
none                 1005M  284K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
none                  396G  1.5G  375G   1% /var/lib/ureadahead/debugfs
/dev/sda1             228M   33M  184M  15% /boot

And fdisk -l:


root@server1:~# fdisk -l

Disk /dev/sda: 438.0 GB, 437998583808 bytes
255 heads, 63 sectors/track, 53250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097deb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       53251   427481089    5  Extended
/dev/sda5              32       53251   427481088   8e  Linux LVM

Basically, I've not messed with LVM much and thought I'd give it a try.  What I want is to mount /home with most of the half terabyte of space, giving the rest to / about 15gb I figure will do for /

I'm reading lvm guides.  So, first step is to reduce / and then make a new partition I assume to mount /home on.

How do I go about reducing the size of /?

lvreduce will kill the data already there.

Thx.

---

### Post by darkod on 2011-12-30
This says you can do it without data loss, from a live mode of course.
[http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/](http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/)

Note that if using ubuntu desktop cd for live mode, you will need to install lvm2 first and probably scan for the PV and VG to make sure they are recognized:

sudo apt-get install lvm2
sudo pvscan
sudo vgscan

As for separating /home from / and moving it, I guess you have found some guides since you didn't ask anything about that. I have no idea if it's easy or difficult.

---

### Post by umbernaut on 2011-12-30
Ah very good.  Should have googled harder.

I have lvm2 already I believe:

lvm version:
LVM version:     2.02.54(1) (2009-10-26)
  Library version: 1.02.39 (2009-10-26)
  Driver version:  4.15.0

No no.  I need all the help I can get.  I'm just getting started :)

Moving home should be no big deal since this is a new server doing nothing.

Normally, I would just start over and do it all from install and not use lvm at all.  I just wanted to give it a chance.  From what I've read, it can be a good thing, although, some people have complained about it being too complex in a disaster....

---

### Post by darkod on 2011-12-30
You misunderstood me. You do have lvm2 installed on the server. However, shrinking root '/' can't be done while it's mounted. So you can't simply boot your server from the HDD.

To make it easier, you might as well use a ubuntu desktop cd (live cd) and boot it in live mode with Try Ubuntu. That way it's running from the cd and the HDD root is not mounted.

But the desktop cd doesn't have lvm2 included so you need to install it with that command so it can work with LVM partitions. That install in live mode is temporary, the next time you boot in live mode it won't be there.

---

### Post by umbernaut on 2011-12-30
Ah ok I gotcha.  Yes I realize it must be done with root not mounted.

That page you sent is great.  Reading it now.

Thanks much.  I'm still up for any advice however....

---

### Post by darkod on 2011-12-30
This looks like a procedure to move Home to a partition /home.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

In your case you will have to create an ext4 LV in your LVM, after you shrink the root LV.

This has some more detailed info about LVM in Ubuntu:
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

Note that you already have a Physical Volume and Volume Group. You only need to create new Logical Volume in the free space created after you shrink the root LV.

---

### Post by umbernaut on 2012-01-02
That guide was great:

[http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/](http://blog.shadypixel.com/how-to-shrink-an-lvm-volume-safely/)

I used the rescue cd it recommended: SystemRescueCD.  It worked like a champ to resize my root volume, and had everything needed.  It is now 15G instead of 396G.  I can now go about creating new home volume.

I had downloaded and made a CD of PartedMagic, but it does not support LVM (yet).

I'll let you know how making new volume and doing /home goes.

---

### Post by umbernaut on 2012-01-03
Summation:

How to shrink the root dir in Linux, using LVM, create a new partition for /home with the free space left over from the shrinkage, format it ext4 and make it mount at boot:

[Note: I did this from root and so "sudo" is not needed; you may need to do sudo in front of each command]

I started with this link:
[http://blog.shadypixel.com/how-to-sh...volume-safely/](http://blog.shadypixel.com/how-to-sh...volume-safely/)

That page was great to resize root. I followed it closely since it discusses making sure to not resize the file system (which you must do first) greater than 90% of what you will resize the volume to:

"Why is this necessary? When we reduce the size of the actual volume in the next step, it&#8217;s critical that the new size is greater than or equal to the size of the file system."

The SystemRescueCD it recommends worked great (I had initially tried Parted Magic, but it does not support LVM). Just use the default boot:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

After root was the right size (from 375G to 15G), I was ready to deal with /home.

I used this:
[https://help.ubuntu.com/community/Pa...ng/Home/Moving](https://help.ubuntu.com/community/Pa...ng/Home/Moving)

And this:
[http://www.walkernews.net/2007/07/02...-in-3-minutes/](http://www.walkernews.net/2007/07/02...-in-3-minutes/) <-- rather old, but useful

However, my volume group was already created at install. So for the walkernews.net page, I started at #5. HOWEVER, I highly recommend doing the size by extents. This page helped for that:

[http://www.centos.org/docs/5/html/Cl...nofreeext.html](http://www.centos.org/docs/5/html/Cl...nofreeext.html)

Lastly, the ubuntu.com's "PartitioningHomeMoving" page provided above, filled in the rest of the gaps (for fstab, moving /home around, etc.)

Here are the commands to the best of my ability for resizing root, creating new partition for /home and moving old home to it, then deleting old home (from memory and putty logs):

[Boot to SystemRescueCD]

[Choose default boot]

"vgchange -a y"

"e2fsck -f /dev/<volume group>/<logical volume>"

"resize2fs /dev/polar/root 14G"

"lvreduce -L 15G /dev/<volume group>/<logical volume>" <-- I thought I might have wasted a GB here, but it doesn't appear so doing "df -h" now. This was before I learned about extents sizing

"resize2fs /dev/<volume group>/<logical volume>"

[Boot back to Ubuntu install]

"mkfs -t ext4 -m 1 -v /dev/<volume group>/<logical volume>"

"vgs -o +vg_free_count,vg_extent_count" <-- this outputs the number of free extents. Basically, it makes the size of the volume using this number _instead_ of bytes and/or, it utilizes _all_ the space available as measured by "extents"; or, it will tell you how many free extents you have if you try to make it too big; this is how I got mine and then issued the command to use them: "Insufficient free extents (99054) in volume group vg1: 99072 required"

"lvcreate -l99054 -n home vg1" <-- volume created "home" in volume group "vg1"; note: "home" here is the new volume that we will next format ext4; "vg1" here is the LVM volume group it will be created in

"mkfs -t ext4 -m 1 -v /dev/<volume group>/<logical volume>" <-- formatted ext4

"blkid" <-- get the UUID for fstab

"cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)" <-- make backup of fstab

"vim /etc/fstab" <-- edit fstab

"# (identifier) (location, eg sda5) (format, eg ext3 or ext4) (some settings) 
UUID=???????? /media/home ext4 nodev,nosuid 0 2" <-- added to fstab; see the guide at ubuntu.com -- "PartitioningHomeMoving"

"cd / && mv /home /old_home && cd / && mkdir -p /home" <-- move home to /old_home and make new /home dir

[reboot]

"rm -r /old_home <-- double-check everything; make sure you gotta good backup, then delete old home with this command

I think that's about it. I still have most of the putty sessions up and just copied/pasted from those. The SystemRescueCD commands I pulled from the guide above at shadypixel.com, "How to Shrink an LVM Volume Safely."

Thanks all!

---

### Post by darkod on 2012-01-03
Excellent job.

I have to say I love it how you can do things like this in linux, without even needing a new install. I hate to even start planning what something like this would need in windows.

My win7 can't even swallow changing the SATA mode in bios to AHCI since I foolishly left it at IDE before the install. If I change it, I have to reinstall. Ubuntu boots fine after the change.

---

