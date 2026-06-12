---
title: "Need to undo a howto"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Guns90 on 2006-07-19
Several people have assisted me, but I have been unsuccessful in mounting a second internal hard drive using the howto at [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html) .  How do I 'undo' all that was done following that particular howto?

---

### Post by bernied on 2006-07-19
To me it looks like that tutorial simply tells you how to mount hard-drive partitions, by adding them to the file /etc/fstab.
If this has not worked, then what do you need to undo?

If you are getting error messages about not being able to mount something, then you could remove the line(s) in /etc/fstab that you added. You would do this the same way that you added it:
sudo nano /etc/fstab

Then go to the line and delete it (Ctrl-K does this). Ctrl-X exits.

The tutorial also tells you to install some software which you could remove if you wanted to, but it is not really necessary. To remove it, simply use:
sudo aptitude remove gparted gksu
(but be sure that you are not already using gksu for anything else - in my opinion it is easier to leave the software there - it will do no harm)

Do you have a new problem as a result of following the tutorial?

---

### Post by Guns90 on 2006-07-19
Maybe I'm wanting something that can't be given to me in Linux.  What I want is to be able to 'see' my hdb1 in some window, mount it, and be able to work with it (reformat, copy to/from, etc.).  Right now, all I have (or can find, at least) is a storage folder with only a few of the files that I know are on the hdd.  Shouldn't I be able to 'see' my secondary HDD in someplace like the Places>Computer window like I see my printer, floppy, removeable drive, etc.?

---

### Post by bernied on 2006-07-19
So you've succeeded in mounting something?

What filesystem is on the partition(s) that you want to work with? What have you tried so far? And what were the results?

---

### Post by Guns90 on 2006-07-19
I'll try to make sence of this.  

My hdb1 hdd was initially my only hdd.  It was loaded with Breezy using all the default partitions after I reformatted the hdd.  I bought a new hdd, disconnected the old one, connected the new one, and did a clean install of Dapper using all the default partitions.  Once I had Dapper up and running pretty much the way I wanted it, I reconnected the Breezy hdd as a slave.  It initially was recognized, but I could not access it because it was being recognized as a 'removeable data device'.  When I followed the howto to mount hdb1, the hdd disappeared from the Places>Computer window; however, I now could access the 'created' files (only) that were on my hdb1 by using filesystem, storage, home.  I have copied the files that I want over to hda1, but I now want to be able to reformat hdb1 to get rid of Breezy and all its dependants and all other data files because it is only an 80 Gb hdd and I want to use it for backing up all my data files. 

My fstab is /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /storage ext3 defaults 0 0


and my partitions are
/dev/hda1  ext3      275.84 Gb     11.42 Gb    264.42 Gb    boot
/dev/hda2  extended    3.62 Gb
/dev/hda5  linux-swap  3.62 Gb

/dev/hdb1  ext3       71.48 Gb      7.69 Gb     63.79 Gb    boot
/dev/hdb2  extended    3.05 Gb
/dev/hdb5  linux-swap  3.05 Gb

---

