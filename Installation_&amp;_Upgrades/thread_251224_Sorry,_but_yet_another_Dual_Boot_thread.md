---
title: "Sorry, but yet another Dual Boot thread"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by blackdalek on 2006-09-05
Hi,

I know there are loads of dual booting threads going on already, but this situation is somewhat different to your standard dual boot set-up so it doesn't really fit into any of the other threads I found here.

I got another computer here I would like to put Ubuntu onto, however this computer already has XP installed in an odd way and I want to keep it where it is if that's at all possible and have it dual boot with Ubuntu.

You see, the problem is there are 3 disks -

Disk 0 is a 200Gb IDE on primary master containing a small 200Mb fat32 boot partition with XP's boot loader files. The remaining 180Gb is unused/unpartitioned.

Disk 1 is a 200Gb SATA with a 40Gb fat32 partition and a 150Gb ntfs partition.

Disk 3 is an 18Gb SCSI which contains the XP OS on an 18Gb fat32 partition.

I want to format the unused 180Gb on Disk 0 as ext3 and install the Ubuntu OS to that. I also want Grub installed onto the fat32 boot partition on that same Disk 0 and be able to still boot into XP from that partition where the Grub boot loader will be.

Is what I want to do at all possible? Will I be able to do this from the Live CD installer without too much trouble?
Here is a link to a picture of my drive set-up explaining where things are.
[http://i7.photobucket.com/albums/y265/BlackDalek/myharddisks.jpg](http://i7.photobucket.com/albums/y265/BlackDalek/myharddisks.jpg)

If anyone can help me with this it will be great.

---

### Post by petri on 2006-09-05
Maybe [hermans]("http://users.bigpond.net.au/hermanzone/") site can help you.

There is another good install Ubuntu at [aysius]("http://www.psychocats.net/ubuntu/index.php") site.

Yes, a lot to read but the best way to learn is to do it yourself ;)

---

### Post by blackdalek on 2006-09-08
I've put this project of mine on hold for a bit while I sort my wireless networking problems, but anyway, from what I've read it seems like it is going to be possible for me to specify which disk and partition that ubuntu is installed onto... but what I'm still not sure about is where the boot loader is going to end up - I assume it will be written to the same partition where my XP boot files are and add XP to the boot options menu. Is this correct?

---

