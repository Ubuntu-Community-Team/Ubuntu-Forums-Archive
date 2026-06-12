---
title: "advanced format drive - ubuntu 10.04"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by rothbert on 2012-04-17
Greetings,
I've installed a 2TB western digital HD on my desktop with ubuntu 10.04 LTS basically for more data storage. Used gparted and GPT partition table format and created one partition. 

Disk utility however says "warning: this partition is misaligned by 3072 bytes. This may result in poor performance etc.

Downloaded the latest gparted and tried again but same results. Have read around but still not sure if this is a problem worth fixing or how to fix it given that there's just the one partition.

some info:

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34 3,907,029,134 3,907,029,101 Data partition (Windows/Linux)



Any tips much appreciated
thanks
Rob

---

### Post by cortman on 2012-04-17
Check in GParted that the starting sector of the partition is divisible by 512. If not, adjust it so it is.
I believe that may be the fix for your problem, unless someone more knowledgeable has an idea?

---

### Post by rothbert on 2012-04-18
Thanks cortman. I found a thread elsewhere which seems to deal pretty closely with the same issue here: [http://forums.linuxmint.com/viewtopic.php?f=50&t=96149&p=551494](http://forums.linuxmint.com/viewtopic.php?f=50&t=96149&p=551494)

The author of gparted gives advice I've read elsewhere that partition start points should be divisible by 8. As in that thread, mine starts on 34 which is clearly not divisible by 8 however I'm a bit stumped as to how I can align a single partition. As in, what happens to the space created before or after the single partition?!

I looked at the resize/move option but that deals with space before rather than sectors.

According to the author (srs5694 who I think posts on these forums as well) the performance issues are such that it is worth getting this sorted. 

So still looking for an actual method.

---

### Post by cortman on 2012-04-18
Yes, ultimately it should be divisible by 8, or any binary number.
In the HDD info that you posted-

> Units = sectors of 1 * 512 = 512 bytes

Therefore, if you can align it to an evenly divisible number of MB or KB, the sectors should hold out too.

---

### Post by mastablasta on 2012-04-18
shouldn't the gparted do this automaticly on newer versions of Ubuntu?

---

### Post by darkod on 2012-04-18
Unless you started loading it with data (and before you have too much stuff on it), you can rather use parted command line tool for more precise options. Move all your data from the partition, delete it, and create a new one. It would go something like (the partition has to be unmounted):

To enter the parted prompt:
sudo parted /dev/sdd

First to print the current view:
print

To remove the partition #1 (at the moment only):
rm 1

To change the unit to sectors from default MB:
unit s

Print the current view:
print

That will also show the total number of sectors the disk has. In your case around 3.9 billion as per fdisk output. Today it is common to start the partitions at sector 2048 if you have 512B sectors (like in your case). That means leaving 1MiB at the front.

So, simply create a partition from 2048 to end (total number of sectors):
mkpart primary 2048 XXXXX

You can create the filesystem in parted but I prefer to do it outside. Quit parted prompt:
quit

Make the filesystem:
sudo mkfs ext4 /dev/sdd1 (if I am not mistaken)

Gparted might have messed things up because of the gpt table. Parted doesn't have those issues. And you can change the unit to sectors and work with sectors directly which helps a lot.

---

### Post by rothbert on 2012-04-18
Thanks darkod - sorted. I think although I installed latest version of gparted, libparted is still a bit dated which may have been a factor. Not sure, anyway parted is a nice solution. 
cheers

---

### Post by growingneeds on 2012-04-23
In my experience, misalignment issues can be addressed with a setting in the partition editor. Make sure that the option that enables "Rounding off to nearest cylinder" is not selected. Rather, the option for "**_Rounding off to nearest MB_**" is. I had used **_GPartEd Live CD_** for partitioning and found it to be very useful. The default partition editor used by Ubuntu, in contrast, does not explicitly offer this option during installation.

Hope this helps.

---

