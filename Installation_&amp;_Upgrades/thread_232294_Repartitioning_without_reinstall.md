---
title: "Repartitioning without reinstall"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by Flavian on 2006-08-08
Can someone help me please.
I made the mistake to give Ubuntu just 8 Gigs, now the disk seems to be full... I have a hybrid system on my Laptop and Don't need that much for Windows, but since Linux is now my Nr.1 OS I need more for Linux.
Is there a possiblity to repartition my harddrives without needing to reinstall Ubuntu??

My partitions are:
NTFS = 14.9 gig / 4.48 free (Windows)
FAT32 = 50.3 gig / 43.34 free(Share between Linux and Windows)
Ext3 = 8.85 gig / 0.7 free (Linux root)
Swap

I could spare space from FAT32 and the NTFS partition.

I am thankful for every kind of help!
Flo

---

### Post by louis_nichols on 2006-08-08
Unfortunatelly, ext3 is not extendable, so I'm afraid the only way is to completely backup your Ubuntu system somewhere, the delete the ext3 partition, then resize FAT32 or NTFS to get the extra space, then re-formatting that sace as ext3 and restoring the backup you made previously.

May I say, though, that 8.5 gigs seems quite enough, especially since you can use FAT32 for storae, as Ubuntu can write to it...

---

### Post by mlind on 2006-08-08
If it's your /home that's taking the most of the diskspace, it's easiest to create new partition just for /home (and copy/move contents from you current /home to new partition).

I've hit that same problem so many times before, so I learned to use LVM which allows to resize partitions dynamically.

---

### Post by louis_nichols on 2006-08-08
I agree. I also use LVM, which I recommend. I'm just in the process of cleaning my windows partition and adding the space to... well, to whatever I need. :). Online. Not even a logout required. Pretty cool!

The downside is that I wanted to make a clean install of dapper, keeping the contents of my home partition, but the default install CD can't read lvm anymore.

---

### Post by mlind on 2006-08-09
> **louis_nichols said:**
> I agree. I also use LVM, which I recommend. I'm just in the process of cleaning my windows partition and adding the space to... well, to whatever I need. :). Online. Not even a logout required. Pretty cool!

The downside is that I wanted to make a clean install of dapper, keeping the contents of my home partition, but the default install CD can't read lvm anymore.

I've always used "alternative" install cd, but I heard that livecd doesn't support LVM, is that true?
LVM support was also broken on Knot 1, but should be working now according to Ubuntu devs.

---

### Post by louis_nichols on 2006-08-09
> **mlind said:**
> I heard that livecd doesn't support LVM, is that true?

yes, it is. The graphical installer from the livecd environment only shows a partition as being lvm, but can't use it for installation.

Where is that alternate cd, cause I would kinda need it?

---

### Post by mlind on 2006-08-09
> **louis_nichols said:**
> yes, it is. The graphical installer from the livecd environment only shows a partition as being lvm, but can't use it for installation.

Where is that alternate cd, cause I would kinda need it?

for Dapper [http://se.releases.ubuntu.com/6.06](http://se.releases.ubuntu.com/6.06), browse down until you find links for "Alternate install CD".

---

### Post by louis_nichols on 2006-08-09
> **mlind said:**
> for Dapper [http://se.releases.ubuntu.com/6.06](http://se.releases.ubuntu.com/6.06), browse down until you find links for "Alternate install CD".

k. thx. does this use the old installer, like breezy had?

---

### Post by mlind on 2006-08-09
> **louis_nichols said:**
> k. thx. does this use the old installer, like breezy had?

Yeah, the old and better one ;)

---

### Post by Flavian on 2006-08-09
> **louis_nichols said:**
> Unfortunatelly, ext3 is not extendable, so I'm afraid the only way is to completely backup your Ubuntu system somewhere...

How do I do that, are there any effitiant tools around? 
I am afraid of messing up my installation. Because if anything fails, I will not be able to set up my system how I have it rightnow. (We have a download limit of 3GB a month and my whole family uses it, I customized my ubuntu install now the way I want it to be, and it's perfect, but losing all that would mean to start from scratch and that I only could do again next month, which would be a pain :D

I used  this thread, but it does not work quiet well, actually for some miraculous reason it does NOT exclude the folders I told it to exclude!

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Any ideas?

Thanks Flo

---

### Post by louis_nichols on 2006-08-09
> **Flavian said:**
> How do I do that, are there any effitiant tools around? 
I am afraid of messing up my installation. Because if anything fails, I will not be able to set up my system how I have it rightnow. (We have a download limit of 3GB a month and my whole family uses it, I customized my ubuntu install now the way I want it to be, and it's perfect, but losing all that would mean to start from scratch and that I only could do again next month, which would be a pain :D

I used  this thread, but it does not work quiet well, actually for some miraculous reason it does NOT exclude the folders I told it to exclude!

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Any ideas?

Thanks Flo

The howto is pretty good. I used it once and it works. Maybe just try it once more, and it should be ok. You could also use a tool such as [partimage]("http://www.partimage.org/Main_Page"), for that, if you're willing to download it. it's pretty cool and I've used it 3 times so far without issues. As always, of course, you have to be very attentive when you do such changes in your system. Of course, there are always risks, but it's how we learn. :)

Going back to backing up with tar... I guess the safest way, would be to boot the Ubuntu installer, mount your linux partition, then use this method for backup. This way you avoid any such issue and don't have to exclude anything from the partition.

---

### Post by randell6564 on 2006-08-09
> **Flavian said:**
> Can someone help me please.
I made the mistake to give Ubuntu just 8 Gigs, now the disk seems to be full... I have a hybrid system on my Laptop and Don't need that much for Windows, but since Linux is now my Nr.1 OS I need more for Linux.
Is there a possiblity to repartition my harddrives without needing to reinstall Ubuntu??

My partitions are:
NTFS = 14.9 gig / 4.48 free (Windows)
FAT32 = 50.3 gig / 43.34 free(Share between Linux and Windows)
Ext3 = 8.85 gig / 0.7 free (Linux root)
Swap

I could spare space from FAT32 and the NTFS partition.

I am thankful for every kind of help!
Flo

QTparted.  use it to resize partitions.

---

### Post by tagra123 on 2006-08-09
I would use sysrescuecd  specifically the part image program. [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) 

I'm going to put together a how to for this. I can restore any of my partition in about 15 to 20 minutes per partitions using this method and  part image can even be used to backup to a network server or directly to another partion -- of course you need to mount the partition before backing up.

If /dev/hda2 has the free space and /dev/hda3 has Ubuntu installed you would type the following commands from the sysrescuecd's command prompt

mkdir /mnt/hda2
mount /dev/hda2 /mnt/hda2
partimage

once partimage displays its gui then select the partition to back up

select the filename and path to back it up to

in this case you would want to back it up to /mnt/hda2/ubuntu-os-backup

and follow through the remainder of the questions.


How much free space do you still have on the different partitions of your harddrive?


By creating a backup with partimage there is no need to mess with grub, or permissions or recreating nodes as required when using tar.  A tar backup is good for data, but my experience has been that its not reliable for the main root directory.

rsync also works -- I use it for hourly backups of data , documents and source code, but I have an extra disk just for that.

If you have an extra disk you can switch over your home directory to that drive and end up with a very reliable setup

Creating a separate partition for the home directory does not have to be difficult using rsync and editing the /etc/fstab file.

I think you can do this with dappers live cd too but I've only tried it with sysrescue cd.

I keep backups of my mythtv OS like this and it has come to be very useful especially when an update breaks myth I simple restore the image and everything works again.

---

