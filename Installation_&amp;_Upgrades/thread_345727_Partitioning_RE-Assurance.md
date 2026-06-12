---
title: "Partitioning RE-Assurance"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by FeNoM on 2007-01-24
Well, I figured out [while browsing through the forums] that creating a extended partition and then 3 logical partitions will install Ubuntu. 

I have a 160 GB HD and I am planning to defragment it 3-4 times before Ubuntu install. I will then resize the HD to 100GB for the remaining windows. I will then create a 20 GIG primary FAT32 partition as a shared drive for both OS's. 

Then I will use the 40GB and partition it as follows.

2GB Linux swap partition <- I chose the Linux swap option when creating. Am i right?
500MB EXT3 Partition for the Boot <- How do I assign it to be the boot partition? Is it EXT3?
37.5 GB Partition for the Root <-- Is this right?

Basically, I want to reassure myself that I am using the correct types and I want to know how I assign each partition for that it is going to do. Please check that the above is correct if not please help. I need Linux becuase I want to expand my Computer Knowledge. Once I get this set up, it will be the best thing I have done I'm sure!

PS: The 20GB partition for being shared can be primary and has to be FAT32 in order to be shared right?

A lot of questions but I'm sure someone nice enough will be able to answer!

---

### Post by ucsdrake on 2007-01-25
> 2GB Linux swap partition <- I chose the Linux swap option when creating. Am i right?

yes you are right .. it is a Linux Swap

> 500MB EXT3 Partition for the Boot <- How do I assign it to be the boot partition? Is it EXT3?

yes thats an EXT3 ... you assign it as the boot partition at the next stage of installation

> 37.5 GB Partition for the Root <-- Is this right?

ya that will do for the Root ... also assigned during the next stage of installation

now the 20gb shared doesnt have to be FAT32 ... you can make it EXT3 or NTFS as well only difference is you have to d/l codecs for each in the opposing OS (ie a codec in Ubuntu to read the NTFS) which means you arent limited to 4gb file sizes max

hope that helps!

---

