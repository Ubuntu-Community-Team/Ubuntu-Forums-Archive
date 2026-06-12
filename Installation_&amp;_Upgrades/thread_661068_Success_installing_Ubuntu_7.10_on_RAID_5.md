---
title: "Success installing Ubuntu 7.10 on RAID 5"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by adprice on 2008-01-07
Has anybody had any success installing Ubuntu 7.10 from the alternate CD on a RAID 5??  I've been looking for days and haven't been able to find anything or get it working.

I have 3 SATA drives I'm trying to set up as a RAID 5 array and the install Ubuntu on that.  Booting from the alternate CD I can partition the drives (1 partition each set for raid) and create the RAID array (3 partitions) but when I try and partition that, the installer tells me 

"Error informing the kernel about modifications to partition /dev/md/0p1 ..."

I can ignore these errors but then the install craps out saying it can't create the ext3 partition.  Any help would be appreciate...this is driving me f***ing nuts.

By the way, some errors I have encountered:
1) Try to delete a previously create raid array but installer claims it is in use.
   Fixed: open a shell and type "mdadm --stop /dev/md0" "mdadm --zero-superblock /dev/sdaX" where X is the partition number
2) Once a primary partition is created on a disk the remaining space becomes unusable.
   Fix: No clue...
3) Partition information does not seem to update unless I restart the installer.
  Fix: No clue...

I've gone through a bunch of RAID HowTos but nothing quite matches what I wan't to do.  All I want is to be able to install Ubuntu on a RAID 5 array so that I can have some redundancy in case a disk fails.  

Thanks,
Andrew

---

### Post by helix_r on 2008-01-07
Please post about it if you are able to pull this off.

Are you doing this with a raid-enabled mobo or with a pci express raid controller card? It appears that in general people have a much harder time doing this with a raid-enabled mobo. Typically, mobo manuals are terrible at documenting what needs to be done for linux when it comes to raid. With a pcie board that claims linux compatibility you  can at least have better docs.

Here is a Tom's Hardware review of SATA RAID controllers from 2005: [link]("http://www.tomshardware.com/2005/10/31/sata_spells_trouble_for_scsi_raid/index.html").

good luck.

---

### Post by adprice on 2008-01-07
Well at first I tried using the onboard raid (fakeraid, really) of my Asus p5k-e, but gave that up after deciding it was just unsupported.  There is software called dmraid that allows you to set up raid arrays from various fakeraid chipsets but it didn't support raid 5 for my chipset.

What I am working on now is trying to get software raid working using mdadm.  I'll let you know if I make any progress.

---

### Post by stu2k2 on 2008-02-23
This post interests me. 

I have attempted a similar install.  I have 4x500 gb sata hard drives that I am attempting to manually make into a software raid 5 using the mobo sata connections.  I will post again with further information about my efforts, but any information you have to get the type 5 raid to work would be greatly helpful.

Thanks, 
Stew

---

### Post by Delg on 2008-02-28
I have been working on this same problem all day.  I tried fakeraid from my nvidia chipset with no luck.  Followed everything around for dmraid (even gave up on raid 5 in hopes of working).  then i found a link to [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)  this was working with mdadm which seems to have worked somewhat.  no matter what i do i can't mount, can't partition and i can't install to it.  I am thinking i will give up in frustration and redo the lot.  use one 500GB drive by itself for boot/swap etc.. and then the other 3 in a raid 5 for storage.  Hopefully this works a bit better.  mind I will keep my eye on this post in case someone figures it out.

---

