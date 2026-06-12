---
title: "partitioning"
date: 2014-11-03
forum: Installation &amp; Upgrades
---

### Post by kuraichi on 2014-11-03
hi, I'm trying to install ubuntu on my laptop but im not sure how I need to partition it?. I've read a few guides online but they all say different things :/

---

### Post by Bashing-om on 2014-11-03
kuraichi; Hi ! Welcome to the forum .

Partitioning will differ depending on each and every use case. Your usage will vary from mine and every one else's.
Do you plan to dual boot ? IF not may I suggest that you take the easy solution and accept the standard install option " erase disk and install ubuntu" .
Not with standing, generally, 10 gigs for '/', 30 Gigs for /home and an allowance ( depending on the amount of ram, and if you plan to hibernate ) for a swap partition, say 2 gigs .
Once you are familiar and comfortable with ubuntu, and know more what your requirements are, then partition to meet your needs.

There is no need to fret and worry, as a new user, the default install will do just fine.

Take the easy way.
[INDENT][INDENT][INDENT]get your feet wet
[INDENT][INDENT][INDENT][INDENT][INDENT]then jump in ( the water is fine !)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-11-03
We cannot give you advice unless you give information about the current setup. Is there an OS already installed? What partitions do you have at present? Does the machine have a BIOS or UEFI boot system? 

Ubuntu needs a minimum two partitions. One for Ubuntu ( / ) and one for swap. If we choose the Install Alongside option then the installer will create those two partitions.

Some of us choose to have three partitions. One for Ubuntu ( / ). One for the Home ( /home) and one for swap. In this case we need to use the Something Else option and use the partitioner to create the partitions and then instruct the installer which partition to use as /, which partition to use as /home and which partition to use as swap. This arrangement has the benefit of being able to re-install Ubuntu without losing our data or user configuration in the /home partition.

There is a third method which also uses three partitions. One for Ubuntu. One for swap and one formatted but left as a data partition. This again has the benefit of being able to re-install Ubuntu without putting our data at risk. Another benefit of this method applies if we have Windows installed and want to access data from both Windows and Ubuntu.

Things get a little bit more complicated if we have Windows 8 on the machine. But as yet we do not know if that is the case. So, I will not waste my time trying to explain that set up.

Regards.

---

