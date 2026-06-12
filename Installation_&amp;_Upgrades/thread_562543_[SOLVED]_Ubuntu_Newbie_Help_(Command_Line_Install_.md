---
title: "[SOLVED] Ubuntu Newbie Help (Command Line Install?  Force My Own Partitions?)"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by macromorgan on 2007-09-28
I've been using Gentoo for a while because so far it's the only Linux I can get working on my system.  I'm having a large amount of difficulty switching to Ubuntu.  Parted/Gparted doesn't like my partition tables.  It swears up and down I'm using a GPT disk, but I'm not... my disk is MBR all the way.  My partition table looks just fine.  I do not want to reformat my hard drive or dd it into oblivion with a bunch of 0s.

Anyway, my problem is this.  When I attempt to use ANY Ubuntu installer, be it 32bit/64bit or Live/Alternate/Mini, the installer always sees my HD as a 1 Meg partition, followed by a 128 meg partition, followed by about 200 gigs of free space.  What I really have according to FDISK is a 160 gig NTFS partition, followed by about 30-40 gigs of free space. (200 GiB HD)

Running gparted from Gentoo tells me I have either a corrupt GPT disk with no fake MBR (no) or I have GPT signatures on an MBR disk (yes).  It won't tell me squat when I tell it my disk is MBR.


Here's what I want to do.  I want to tell the installer to let me partition the disks my own damn self, or to use a partition table I have already created with FDISK and mkfs.whatever.  Nothing I've tried so far has worked.  Is there a way to force the installer to use partitions I've already created?

Alternatively, if I can't do that, is there a down and dirty manual command line install method that doesn't try to hold my hand?  

Perhaps someone knows how to remove those pesky GPT signatures without blanking the drive?

I want a linux installation that won't crap out and demand I edit 50+ config files before it will work every time I perform a system update, but sadly Gentoo is the only thing I've been able to get working. :(

If anyone can help me, I would be very greatful.  Thanks!

---

### Post by Pumalite on 2007-09-28
Post:
sudo fdisk -lu

---

### Post by macromorgan on 2007-09-29
Sorry if it's hard to read, but I appreciate the help.  I recently put a Gentoo boot setup back on here.  There is no boot partition, grub and the kernel are stored on the /dev/sda2 under /boot.  Grub is installed in the first sector of /dev/sda2, and NTLDR is installed in the MBR and is used as my bootloader to load Windows XP x64 and Gentoo x64.

**Output of FDISK**

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes  
Device		Boot	Start		End		Blocks		Id	System
/dev/sda1	*	63		335549654   	167774796	7	HPFS/NTFS
/dev/sda2		335549655	393592499	29021422+	83	Linux
/dev/sda3		393592500	398283479	2345490		82	Linux swap / Solaris

**Output of PARTED  (if I tell it N I get nothing, so I told it Y)**

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y
Model: ATA Maxtor 6B200M0 (scsi)
Disk /dev/sda: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Number  Start   End     Size    File system  Name                          Flags  
1      17.4kB  1066kB  1049kB               LDM metadata partition               
2      1066kB  134MB   133MB                Microsoft reserved partition  msftres

**For reference, the output of Diskpart in Windows XP (x64):**

  Disk ###  Status      Size     Free     Dyn  Gpt
  --------  ----------  -------  -------  ---  ---
* Disk 0    Online       190 GB      0 B

Partition ###  Type              Size     Offset
-------------  ----------------  -------  -------
Partition 1    Primary            160 GB    32 KB
Partition 2    Unknown             28 GB   160 GB
Partition 3    Unknown           2291 MB   188 GB

---

### Post by Pumalite on 2007-09-29
Have you tried rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)

---

### Post by macromorgan on 2007-10-25
Rescue CD does not work for me.

I'm now trying Ubuntu 7.10.  They must have upgraded the version of fdisk, because now I get the message "WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted."

But it's not GPT!  It's MBR!  I can't figure out how to tell Ubiquity my disk is MBR!  Or to not even bother checking for partitions and just assume I have a / and swap.

---

### Post by Pumalite on 2007-10-25
You can use Gparted Live CD to make your partitions ahead of time and then Install with Alternate CD, using the partitions already made or point to the partitions you want.

---

### Post by macromorgan on 2007-10-25
The alternate install CD does not work as it still calls gparted to partition my hard drive.

Having said that, I got brave and managed to fix the problem on my own.

I found some disk editing software, and manually edited my hard drive.  There was some garbage immediately after the MBR and some of the text led me to believe that it was causing the problem.

I zeroed out about 1 kilobyte worth of data immediately following the MBR (if you try this at home make DAMN sure you know where the MBR stops).

After I did this and rebooted, gparted now sees my hard drive correctly, and Ubuntu is installing now.  Woot!

---

