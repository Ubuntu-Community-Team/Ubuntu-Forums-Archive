---
title: "Ubuntu Installer Crashed - Partitions corrupted"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by hatemandatoryregistration on 2007-03-06
I attempted to dual boot Windows and Ubuntu.
I booted up Ubuntu Desktop LiveCD (Yes it passed MD5 and disc check) and the after sorting out Nvidia drivers problems (By temporarily switching to vesa drivers) I then attempted to install envy to see if I could use it to get my nvidia drivers working.
It installed and so did the nVidia driver installation (Though ultimatelty it did not work as it required me to reboot the machine even though I was LiveCD) but had a few dependancies problems (Not that Envy or apt minded)
Willing to actually install Ubuntu onto my machine to see if Envy would work, I opened up the installer.
I have 1 SATA drive of 250GB with a 2 partitions (Both NTFS) with ~40 GB of free space, this is connected directly to one of the motherboard's SATA ports.
I have 1 PATA drive of 160GB with 1 partition (NTFS) with no free space. This has been put on a el-cheapo PCI RAID card (Though RAID wasn't actually setup).
I told it to install on the SATA drive using the "Free space available".
After about 80% the installer crashed with the same errors that came up in Envy. It said that it was a bug in an obtuse dialog box (I was using vesa so my resolution was low) and the the computer stop responding.
Of course I restart and Windows wouldn't boot. Well, I can agree with that because the Grub installation would of messed up the MBR. Upon loading a recovery disk to repair the MBR, I noticed that **all** my partitions on the hard drive were gone. All to be replaced with one large corrupted partition on each drive (Windows Recovery Console even considered it to be FAT).
What can I do from here?

EDIT:
MBR did not rewrite successfully.
Diagnostics say that there are partition(s) that have their starting cylinder **after** the end of the disk?
Other PATA hard drive not even recognised outside of RAID Card BIOS (Kind of understandable, but worked before in low level modes).

---

### Post by Herman on 2007-03-06
Sorry to read of your difficulties.
[B]
[**TestDisk** - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") [/B]Is now available in[GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") (and has been for some time). 
Some people have reported success with recovering MBRs, partitions, filesystems and files with it. Others are not as lucky or maybe didn't have the required computer savvy.
You should do a little bit of reading from the TestDisk site to prepare yourself, and good luck.
I hope this will be helpful, use your own good judgement,
Regards, Herman :)

---

### Post by hatemandatoryregistration on 2007-03-06
Retrived from a Norton LiveState Recovert Utility

**SATA Drive 97914 Cylinders, 116 heads, 43 sectors per track**
**Partition 1** - Main NTFS I think
Type: 64
Boot: FF
Starting Cyl: 68
Starting Head: 13
Starting Sector: 10
Ending Cyl: 288
Ending Head: 115
Ending Sector: 43
Sectors:
Before: 1869771365
Sectors: 168689522

**Partition 2** - Other NTFS I think
Type: 73
Boot: 50
Starting Cyl: 371
Starting Head: 114
Starting Sector: 37
Ending Cyl: 366
Ending Head: 32
Ending Sector: 33
Sectors:
Before: 1701519481
Sectors: 1869881465

**Partition 3** - Ubuntu Swap I think
Type: 74
Boot: 20
Starting Cyl: 371
Starting Head: 114
Starting Sector: 37
Ending Cyl: 372
Ending Head: 97
Ending Sector: 50
Sectors:
Before: 2573
Sectors: 0

**Partition 4** - Free Space?
Type: 00
Boot: 00
Starting Cyl: 0
Starting Head: 0
Starting Sector: 0
Ending Cyl: 0
Ending Head: 0
Ending Sector: 0
Sectors:
Before: 0
Sectors: 3435113472

---

### Post by hatemandatoryregistration on 2007-03-06
Thank you, worked like a charm.

---

### Post by Herman on 2007-03-06
=D> Great job, (phew!) congratulations, you must be a power user.

It's extremely rare for something like that to go wrong, but it can happen.

This makes you a very important person, because if someone else ever needs help to use TestDisk, (or whatever recovery software you used) you will be one of very few people who now have experience in using it for real!
Hopefully you'll still give Ubuntu another try sometime and you'll stick around. (Make sure you back up first).
I'm glad you got your problem sorted at least, well done and best of luck with everything you do from now on, Regards, Herman :)

---

