---
title: "Installer cant find hda"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by huestis on 2007-04-21
Hi all,

Thanks for your help in advance!

Heres the situation:

I have 3 physical hdd's in my pc.  2 are sata and 1 is pata/eide/ whatever you wanna cal it.  The 1 ide is partitioned into 3 partitions and gparted sees them all just fine.  I reformatted my hda5  to ext3 using gparted in hopes that it would resolve the installation issue Im having.  
Whever I boot using the Feisty install cd <either Alternate or Regular> the partitioner sees both sata drives but not the ide drive.

I have searched on the forum, and Im sure that I missed something somewhere that could have prevented this post, so Im sorry for this. :oops: 

Many MANY thanks,

JR

---

### Post by ffxr on 2007-04-21
hda5 doesnt sound quite right for a 3 partitioned HDD.. for starters..

what exactly does your partition tables look like e.g

hda1 NTFS
hda2 ext3
sda1 ext2
sda2 swap
sdb1 FREE SPACE

why do u need 3 partitions on your IDE drive for anyway...?
is it possible to remove all the partitions from the IDE disk and present Feisty with just the free space?

---

### Post by huestis on 2007-04-21
Heh, to be honest, I had setup the 3 partitions prior to getting the addition 2 hdd's <a woot offer I couldnt refuse lol>.  The 3 were basically c: d: and e:    c: being my main winblows partition and d and e storage/experimentation parts.  I need to dualboot because I work from home and need Cisco VPN as well as Cosmo ACD and Go2Assist, I plan on running this Windows part in a vm once I get Ubuntu running.

The table is:

hda1 ntfs   Flags: boot
hda2 ntfs
hda3 Extended   Flags: lba
     hda5 ext3
sda1 unknown
sdb1 unknown

Thanks Again!

---

### Post by huestis on 2007-04-21
[Update]

OK, so, stupid mistake, I was using the Server image.  I can get into LiveCD, but it still wont detect my ide hdd.  I have made sure that all of the jumpers are correct, and what is strange is that my cdrom drive, on the same cable, works fine.  Could it be an issue with either it being a Maxtor hdd OR the Intel 915gag mobo?


Thanks again,

JR

PS
I also disconnected the sata drives, same thing.

---

