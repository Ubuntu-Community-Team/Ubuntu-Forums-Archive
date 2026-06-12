---
title: "installer doesn't see any partitions"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by flaminglawyer on 2012-04-29
I'm trying to install Ubuntu, but the installer doesn't see any partitions on my HDD. It sees it as just a disk.

Here's my partitioning (as seen from windows):

[IMG]http://i.imgur.com/IuFVk.png[/IMG]

Dellutility and Recovery are unused, "unnamed" is a Truecrypt container, UBU BOOT is going to be the boot partition for ubuntu, PUBLIC is going to be shared files between Windows and Ubuntu, OS is the Windows partition, and UBUNTU is going to be the install partition for ubuntu.

But when I load up the installer CD (either the "live cd" installer or the "alternate" installer, they both do this), it claims that there are no partitions on the drive. Even though clearly there are. (sorry no screenshot.) I previously had the "OS" partition fully-encrypted with Truecrypt, but recently un-encrypted it, if that makes a difference.

What could be the problem here? And how can I fix it?

---

### Post by jadtech on 2012-04-29
you have to partition  it ext4 the use all but 1 or 2 gigs  for root which should be sda5 and the 1 or 2 gigs left over  for sda6 swap  this is min  one that is done  install should find the partition I have never done  the full install yet but everything I read this is how its done  you have to partion frist linux wont  install on fat partition ..

llinux will install on less but I recomen d at least 30 gb just for root 2 gb for swap this gives you room to grow a little ..

something look a little goofy with your set up there windows, recover, dell utility and the smaller partition for MBR should be primary how did  they become unlabeled ??     thew linux partition should be ext4 and inside that the root and swap ..

---

### Post by jadtech on 2012-04-29
the more I look at the picture I just want to say it looks like you already have 4 primary partition on the disk thats all you can have and one of them is label ubuntu at the bottom with a fat 32 fileing system some how ..

you are using Gparted from the live boot cd  to formate correct ??

---

### Post by darkod on 2012-04-30
I think the Truecrypt is giving you problems, it's not allowing ubuntu to see the partitions correctly. I haven't worked with it, so I don't know what to do with it.

But, Truecrypt aside, the space you left for ubuntu (only 5GB) is very very small. Plus you made that partition FAT32 and ubuntu needs to install onto linux filesystem. The same goes for the boot partition you plan for ubuntu. It's better to be larger than 100MB, and it can't be FAT32 either. Don't create partitions for linux from windows, it can't create linux filesystems. Leave the space unpartitioned and create them with the ubuntu installer.

Also I would suggest you delete all partitions you don't use, makes the layout easier to understand. If you are completely done with Truecrypt, delete its container too (but only if you are sure you don't need it).

---

### Post by jadtech on 2012-04-30
i don't know what truecrypt is or how it works either , but just to look at it I am thinking what ever it promises to be helping with and saving is going to cost you later in the end x2 some how later on in maybe not only lost or corrupt data but maybe even speed  ..

though you might be able to squeeze ubuntu in to the 5 gb  and you have a planned shared directory where is it you plan the space on that root  for home directory added programs scripts even system updates and upgrades ??

shared partition is good for like pictures docs and music files but you can do that too effectly enough  with ubuntu one or any other service of it kind and though  space on them is limited unless you pay for more it  would cost you less in end in gains in drive and computer speed and if you loose a system or hard drive  need to replace the computer   no need to worry your important files are safely tucked else where .

---

