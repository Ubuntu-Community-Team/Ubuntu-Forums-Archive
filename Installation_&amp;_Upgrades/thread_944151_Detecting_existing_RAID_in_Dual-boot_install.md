---
title: "Detecting existing RAID in Dual-boot install?"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by sturdyworks on 2008-10-11
I am struggling to understand how to get Ubuntu to detect my existing RAID array. Just want to add Ubuntu a dual-boot to my Dell XPS 2010 running Vista Ultimate.

Dell installed Vista on 2x200GB SATA drives in RAID-0. The SATA HD & RAID controller chipset is by Intel.

When I select to the "manual partition step" in Ubuntu install it simply shows two 200GB drives to choose from. This obviously means it is not automagically detecting my RAID setup.

Vista has a new Computer -> Manage -> Disk Management application that shows this partitioning:

--------------------------------------------------------------
|        |         | D:      | C:    |             |         |
| Disk 0 | 64MB    | 10GB    | 280GB | 80GB        | 2GB     |
|        | EISA    | NTFS    | NTFS  |             |         |
|        | Config. | Primary | Boot  | Unallocated | Primary |
--------------------------------------------------------------

I created the "80GB Unallocated" for Ubuntu tonight by selecting C: partition, right mouse click, then select Shrink Partition...

There is not another "Disk 1" type on listing, so we must assume that everyone of my partitions are on the RAID-0 setup.

I am an experienced open source programmer, but must admit I have relied heavily on my Systems Administrators in the past, so I'm more than a bit worried about destroying Vista.

There is a RAID related artical on the Ubuntu site:
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)
It mentions things like "Make it a RAID partition, Mark it as bootable, Choose the Configure RAID option" but that guy was doing some truly wacky stuff in his "Installing over an Existing RAID Array" ramblings.

I wish I knew the point, during the Ubuntu install, when the disks and boot records and such will actually get modified--then I would be more likely to tinker around a bit. I do not want to loose Vista tonight--Got work to do...Any info on this appreciated.

B.A.S

---

### Post by sturdyworks on 2008-10-11
Found another article on Ubuntu site refering to RAID install:
[https://help.ubuntu.com/community/Installation/RAID1](https://help.ubuntu.com/community/Installation/RAID1)
It mentions, "RAID1 can be almost completed during the disk partitioning section of the install process. First set two partitions to type FD/Linux Raid on different discs, commit them, then take the 'Configure Raid' option at the top. Do 'Create MD', thence partition the multidisc 'partition' as you see fit."

---

### Post by sturdyworks on 2008-10-11
Ubuntu install seems to use GParted (Gnome Partition Editor application) and underlying GNU libparted library.
The related web-sites for this code base are:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://www.gnu.org/software/parted/](http://www.gnu.org/software/parted/)

Unfortunately, this GParted with libparted combination does not seem to support "raw" (Partition Table) file systems, which are the ones useful for RAID & LVM.

Doing research I have noticed that some other "Partition Editor type applications" use libparted:
[http://www.gnu.org/software/parted/links.shtml](http://www.gnu.org/software/parted/links.shtml)

Some of these other partition apps DO seem to support RAID & Linix (so maybe they added features to basic libparted functionality). 

For example, the Fedora partition app named Anaconda web-site indicates, "A variety of advanced storage devices including LVM, RAID, iSCSI, and multipath are supported from the partitioning program."
[http://fedoraproject.org/wiki/Anaconda](http://fedoraproject.org/wiki/Anaconda)

It seems like now the best bet is to use some other Linux disto with better partition app when user has an existing RAID array...

B.A.S.
Sturdyworks

---

### Post by terrell-coble on 2008-10-13
I have this same issue and have been trying to figure it out for 2 days...

I've completely scrubbed the entire machine which was dual boot orginally to a completely fresh ubuntu studio only machine. Why doesn't it see my hardware raid array?

This guy posted 3 days ago, and replied to his own message! Is that what one expects on this forum?

---

### Post by terrell-coble on 2008-10-13
In the spirit of this thread, I figure I should respond to myself.

If Ubuntu sucks for hardware based Raid Arrays, then why not say so before people spend 25 hours or so trying to figure it out?

However, I'm trying to get the production studio working for ubuntu studio. And, Hardware Raid is standard fare and the order of the day for that user environment...

---

### Post by terrell-coble on 2008-10-13
ibinti! Cause I rock...

Just figured this stuff out...

Luckily, I have enough machines around to where this one is a play toy. I'm having some tweakage issues, but that's just cause I'm a newbie...

The key is to blow offf any hardware assist Raid controllers and throw the dice just like the common guy... Now I need to set up software raid 0 for 4 more drives.... Will be looking for that!

---

