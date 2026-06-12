---
title: "GParted claims my drive doesn't have ANY data on it, and I cannot make new partitions"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by Tynach on 2010-10-09
RedHat Disk Utility shows all my partitions intact, and I was able to delete partitions fine.

However, I was wanting to delete 2 logical partitions inside an extended partition, and put two different partitions in their place.

I deleted them, which worked fine... But I was getting this error when I tried to create one:

```

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=435684376576, size=21477982208, type=0x83
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 104857600, type 0x07)
new part entry
looking at part 1 (offset 105906176, size 388331732992, type 0x07)
new part entry
looking at part 2 (offset 388438687232, size 111658664448, type 0x0f)
Entering MS-DOS extended parser (offset=388438687232, size=111658664448)
readfrom = 388438687232
MSDOS_MAGIC found
readfrom = 392732606464
MSDOS_MAGIC found
readfrom = 414208650240
MSDOS_MAGIC found
readfrom = 457161062400
MSDOS_MAGIC found
readfrom = 435684856320
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed

```

Now, I can no longer delete partitions in it.

So, I went to GParted.

Guess what? It claims there are NO partitions on the entire drive. At all.

Within Ubuntu, I am able to mount the partitions that are there.

Any help? I hopefully can have this before 5:00 tonight (midnight UTC), as the partitions are for backing up data from my Ubuntu installation for upgrade purposes...

My partitioning scheme (according to RedHat Disk Utility):

```

sda:
	sda1 - 105 MB NTFS (System Reserved) {This is part of Win7}
	sda2 - 388 GB NTFS (Win7)
	sda3 - 112 GB Extended
		sda5 - 4.3 GB Swap
		sda6 - 21 GB Ext3 (SuSE)
		sda7 - 21 GB Ext3 (CentOS)
		     - 21 GB Free (used to be Fedora, deleted it for backup)
		sda8 - 21 GB Ext3 (Debian)
		     - 21 GB Free (used to be PCLinuxOS, deleted it for backup)
sdc:
	sdc1 - 192 GB Ext4 (Ubuntu)
	sdc2 - 8.2 GB Extended
		8.2 GB Free (used to be swap, don't know what happened to my swap there)

```

As you can see, I had quite a few Linux distros installed... They all worked too. But I deleted my two least favorite, for the purposes of creating partitions to backup my data on. Ignore the absense of sdb, my laptop harddrive is currently plugged into my desktop, so it shows up too.

---

### Post by srs5694 on 2010-10-09
First, check [this Web page,](http://www.rodsbooks.com/missing-parts/) which *may* provide a solution. (It's unclear to me if you've got the same problem as described on that page, but you may.)

Second, if that doesn't help or if you don't understand it, please post the output of "sudo fdisk -lu" here for us to see.

---

### Post by laudaka on 2011-01-08
Many many thanks srs56. I used that web page you gave [http://www.rodsbooks.com/missing-parts/](http://www.rodsbooks.com/missing-parts/) by Rod Smith. Among other things it contains a very interesting explanation about the use of the powerful and dangerous command **sfdisk**.

I had that same error

**Invalid partition table on /dev/sda -- wrong signature 0.**

in GParted. All partitions were gone, only unallocated space. Whoops.

I had it while working with GParted in a normal Ubuntu/GNOME session (not while booting from a LiveCD or the like). So imagine how I started panicking knowing I would never be able to switch off the computer and boot next time I switched it on. I had to fix the problem before turning off the computer. This computer is so crappy that I can't use the LiveCD booting mode of an ordinary Ubuntu install CD... 

With that sfdisk command I wrote a dump of the partition table to a file. I used that very same file as input again for sfdisk. And guess what? GParted sees partitions again (two unimportant partitions gone). I had to tell sfdisk to write it it even if it was describing partitions I had mounted at that moment. If you're a beginner better not use sfdisk. If you understand what you do it's a very powerful tool that can help recovering botched partition tables.

P.S. I had backups of my data. A bit scrawny, but at least I couldn't lose my data.
P.S.2 Not yet sure if it really will boot. Although what GParted shows is looking good. I'll tell it here in a few minutes.

---

### Post by laudaka on 2011-01-08
Yes it worked! I could reboot. I'm absolutely sure I couldn't have rebooted with that spoiled partition table. And GParted is of course still showing the partitions, but I wouldn't expect anything else after a succesful reboot.

Pff, that was close.

I'd wish to thank you too, Tynach. You really posted a lot of very useful diagnostic information with your help request. Also about what tools you used to understand the problem. Instructive.

Have fun using free and open source software!
Have fun with Ubuntu!

---

