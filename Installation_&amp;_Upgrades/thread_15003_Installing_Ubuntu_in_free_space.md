---
title: "Installing Ubuntu in free space"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by Nobber on 2005-02-11
Can I install Ubuntu in the free space on my hard disk, or do I have to allocate all the space on the disk to partitions *before* popping the Ubuntu CD in and rebooting? Reason I ask is that I couldn't figure out how to install Ubuntu in the free space on /dev/hda from within the installer.

Here's my hard disk layout.

/dev/hda - 40GB - swap on hda5, BLFS 5.0 on hda6, Mandrake 10.1 on hda2, 20GB unallocated
/dev/hdc - 120GB - ext3 hdc1 for /home, no unallocated space
/dev/hdd - 45GB - ext3 hdd1 for /spare, no unallocated space

When I get to the partitioning screen in the Ubuntu installer, I see one line devoted to a description of /dev/hda, with no indication that the disk already contains partitions. When I select /dev/hda for manual partitioning, it asks whether I want to start with a new partition table!  :!: Obviously, since I don't want to lose my precious data, I say no. The partitioning screen shows correct info  for the existing partitions on /dev/hdc and /dev/hdd, but I don't want to install Ubuntu there.  :-( 

How do I get Ubuntu installed on the unallocated space on /dev/hda?  :?

---

### Post by desh on 2005-02-11
See if you can use fdisk to create new partition on /dev/hda and use that partition to install

---

### Post by az on 2005-02-11
"When I get to the partitioning screen in the Ubuntu installer"

Are you using guided partitioning?

"asks whether I want to start with a new partition table!"

Is that the exact message?  Because I think it tells you that modifications will change the partition table - which is the point of partitionning.

---

### Post by Nobber on 2005-02-11
OK, I've got the Ubuntu installer running, and I've selected manual partitioning. Now the installer's giving me a list of options (Configure Software RAID etc.) and a list of the hard disks. The first item in the list is:

IDE1 master (hda) - 40.0 GB ST340016A

I select this (since it's the disk, already partitioned, that I want to install Ubuntu on), and the installer asks:

Create new empty partition table on this device?

to which I respond No!

And I can't continue, because I haven't set any mount points on the target disk (hda), because the installer won't let me.  :|

---

