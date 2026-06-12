---
title: "Custom partition table"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by Martinsk on 2005-03-07
I just installed a second disk in my computer for experimenting with several Linux distros. To maximize the number of versions I could hava at the same time, I partitoned the disk in the following way:
 two 50M partitons at the beginning of the disk for /boot on two linux systems,
one 1G swap partition to be shared, and an extended partition containing two 30G
logical partitions for / on both systems.
Ubuntu wants to take over the whole distk for / with a small  swap apartition at the end.
How do I get Ubuntu to accept my parttitoning scheme?
I'm thinking that the sahred swap would be ok, since I can only boot into one system at a time.

Martins

---

### Post by bored2k on 2005-03-07
[QUOTE=Martinsk]I just installed a second disk in my computer for experimenting with several Linux distros. To maximize the number of versions I could hava at the same time, I partitoned the disk in the following way:
 two 50M partitons at the beginning of the disk for /boot on two linux systems,
one 1G swap partition to be shared, and an extended partition containing two 30G
logical partitions for / on both systems.
Ubuntu wants to take over the whole distk for / with a small  swap apartition at the end.
How do I get Ubuntu to accept my parttitoning scheme?
I'm thinking that the sahred swap would be ok, since I can only boot into one system at a time.

Martins[/QUOTE]

Instead of selecting it to take over , select Edit Partition Tables, from there you should see you're drives right ? Yes .

Then select where u want ubuntu to be installed [preferably +1.5gb], format it to one of the filesystems [recommended : XFS, Ext3 or ReiserFS] and select a mount point [ would be / ] . iF  you want home folder on another partition, do the same with another 1, and in mount point select /home . 

Its strongly advised to make a swap area space... around 500mb would be ok [format > use as swap] .

---

### Post by Martinsk on 2005-03-08
Ok, here is what I was trying to do:
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1          98       49360+  83  Linux ; ext2 for /boot on Ubuntu
/dev/hdb2              99         196       49392   83  Linux ; ext2 for /boot on system 2
/dev/hdb3             197        4072     1953504   82  Linux swap / Solaris
/dev/hdb4            4073      119150    57999312    5  Extended
/dev/hdb5            4073       61612    29000128+  83  Linux ; reiser for / on Ubuntu
/dev/hdb6           61613      119150    28999120+  83  Linux; reis for / on system 2

This I had set up before I started the Ubuntu install disk. When I go from partition to install base system, Ubuntu erases the bootable flag on hdb1 and puts me back into the partition module. Does Ubuntu want to be installed on a single partition or is my boot partition too small or what?

Martins

---

### Post by bored2k on 2005-03-08
[QUOTE=Martinsk]Ok, here is what I was trying to do:
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1          98       49360+  83  Linux ; ext2 for /boot on Ubuntu
/dev/hdb2              99         196       49392   83  Linux ; ext2 for /boot on system 2
/dev/hdb3             197        4072     1953504   82  Linux swap / Solaris
/dev/hdb4            4073      119150    57999312    5  Extended
/dev/hdb5            4073       61612    29000128+  83  Linux ; reiser for / on Ubuntu
/dev/hdb6           61613      119150    28999120+  83  Linux; reis for / on system 2

This I had set up before I started the Ubuntu install disk. When I go from partition to install base system, Ubuntu erases the bootable flag on hdb1 and puts me back into the partition module. Does Ubuntu want to be installed on a single partition or is my boot partition too small or what?

Martins[/QUOTE]
 I have never had that problem, and I have about 4-5 partitions. Weird problem tho it erasing the bootable flag and returning to the partition module ... im unXPrienced here.


*Emulates Macho Mexican Wrestling and extends hand on the rope for someone to tag in and help ^O_. :P*

---

