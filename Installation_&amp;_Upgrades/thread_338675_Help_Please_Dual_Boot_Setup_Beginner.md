---
title: "Help Please: Dual Boot Setup Beginner"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Dominicus on 2007-01-14
Hello All,

I wish to setup a dual-boot WinXP/Ubuntu system.  My PC currently has a primary drive with WinXP boot which I do NOT want to reformat.

I just purchased a new 200Gb HDD with hopes to split it three ways:
1. Ubuntu boot partition(s) ~60 Gb?
2. Windows partition for extra storage space ~60Gb
3. Windows partition for periodic backups of WinXP ~80Gb

I've never partitioned a drive this way...only done full installs (i.e. currently have primary PC w/XP, and experimental laptop with Edgy), so I ask to not hold back on the details and recommended applications/sequence to do this.

The vision of final product is for the PC to boot to WinXP as default (my existing 160Gb drive) and access the two Windows partitions on the new 200Gb drive.

Of couse I want the option to redirect boot to Ubuntu if I intervene the boot process, in which case the 200Gb drive with Ubuntu boots, plus wish to have ability to access files in at least some of the Windows partitions.

How do I do this without risking my current XP boot drive install?

My system:
Dell Dimension 8100 (Intel 850 chipset)
P4-2.6Ghz 400FSB
1280Mb PC800 RDRAM
Maxtor ATA133 160Gb w/XP HomeEd
Nvidia GeForce 6200 256Mb
Now sporting an unformatted ATA100 200Gb drive ready to be Ubuntu'ed!

Thank You community! Dominicus

---

### Post by Sef on 2007-01-14
To Dual Boot:

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") (to install from the alternate cd.)

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") (to install from the Live CD.)

---

### Post by confused57 on 2007-01-14
Here's another option, if you don't want to risk installing grub to your Windows mbr:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You might also want to read over the links Sef gave you.

---

### Post by Dominicus on 2007-01-15
Ohhh...I'm liking the help.  Thanks all for quick replies.  My extra HD hasn't arrived yet, and here I am 'planning' how to divvy my extra space...

I plan to leave the XP drive intact with the recommended how-to from confused57:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

That leaves the question of how to split the fresh-new 200Gb drive that's about to arrive. Here's my first pass at future dual-boot system and partitions:

hd#1 (200 Gb):
	Has hidden GRUB redirecting to WinXP by default
	Part_1. Ubuntu / (ext3)  ->Size=10 Gb???
	Part_2. Ubuntu /home (ext3)  ->Size=20 Gb???
	Part_3. Shared Partion (ext3) ->Size=All remaining space
		also accessible from XP via FS-Drive
	Part_4. Swap (3-4 Gb)

hd#2 (160Gb)
	Intact MBR - can be swapped into hd0 position if need be.
	Part_1. WinXP (NTFS) boot (160 Gb)

Now my questions:

1. I like the idea of a large shared partition with read/write ability between Ubuntu and XP, as I plan to use this for periodic backups of critical data from the XP boot drive, temporary space for large video files, and possibly games.  As such, FAT32 won't work due to the file-size limit.  So it was down to two options: NTFS (not writable by Ubuntu), or ext3 with XP running the FS-Drive driver to read/write to it.  QUESTION: is there a read/write speed penalty for using the FS-Drive/ext3 vs. NTFS?

2. What's the recommended size for the \ partition?  (Assuming I want to install all possible mods to this and future installations)

Any other warnings about FS-Drive use?  Thank You

---

### Post by confused57 on 2007-01-15
I've never used the fs-driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
so I can't really offer you any advice for using it.
As far as I can see, the sizes you have for / and /home look OK; however, you definitely don't need that much swap...I'd recommend no more than 1 Gb.

I believe you'll be pleased with setting your system up like I mentioned, I have 2 pc's set up that way & no problems with either.

---

### Post by Dominicus on 2007-01-16
Well, now I'm concerned with this FS-Driver ext3 shared partition deal.

As neat and informative as the driver website is, very little is out there about this utility (i.e. Google, forum talk, etc)...only a few posts of the curious ones, but I've yet to read anyone vouching for this apps reliability....:confused: 

My hopes were to have a common filespace accessible by both Ubuntu and XP, to share the surplus drive capacity.  I'm thinking scheduled backups of financial, images & other critical data I keep in XP, ISO images of random DVD's I keep (i.e. bittorrent), temporary video capture files from my camcorder...most these type files are >>4Gb, so FAT32 won't cut it.

I'm up for any challenge (Ubuntu being one), but I'm having second thoughts on WinXP backup application saving over FS-Driver into ext3 and the thing bomb out at the worst possible moment.

Is this a rare setup, wanting both Linux and XP with shared read/write capable of >3Gb files?

I guess one solution may be to split the extra space into a FAT32 (smaller shared read/write) partition, and another NTFS for big XP files with read-only access from Ubuntu, but darn!

Thanks. Dominicus

---

### Post by confused57 on 2007-01-16
I personally haven't tried the fs-driver, but it seems to be working pretty well for the people who have said they are using it...I honestly believe from what I've read, that your plan of using an ext3 shared partition would be your best option.

  In fact, this partitioning scheme for sharing between Windows & Ubuntu is suggested here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Dominicus on 2007-01-16
Thanks confused57.   I did take this idea from psychocats' excellent docs and visuals.  In fact, I found this was a great [guide]("http://www.psychocats.net/ubuntu/partitioning") to understanding partitioning choices.

I think my initial questions on dual-boot setup are now answered and a lot of the stress about fouling up big-time is gone.

If need be, I'll open a new thread to discuss the FS-Driver performance and crash-recovery later on.

Cheers!Dominicus

---

### Post by merry_meerkat on 2007-01-16
Hi,
I just wanted to let you know that I am reading from and writing to an NTFS partition from Ubuntu using **ntfs-3g**. So far it works just fine.

Here's what I did:
[http://boff.wordpress.com/2007/01/13/readwrite-to-fat-and-ntfs-partitions/](http://boff.wordpress.com/2007/01/13/readwrite-to-fat-and-ntfs-partitions/)
...be sure to also look at the references linked to, if you're going to do this.

Have fun...

---

