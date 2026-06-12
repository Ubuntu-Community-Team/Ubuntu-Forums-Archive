---
title: "Multiple Boot / Will not recognize existing partitions"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by FFFFreddie on 2007-01-16
New to Ubuntu and Linux, experienced with other software installs... but **in trouble** !

Have multiple partitions on one hard drive, placed using a program which installs an EMBR to get over the maximum 4 partitions limitation on one disk.

Have formatted all the partitions using that program (Bootit NG - latest version - [http://www.terabyteunlimited.com/bootitng.html)](http://www.terabyteunlimited.com/bootitng.html)). It is a boot manager, drive imager, and partitioning program which works very well.

I have the following partitions: DOS, Ubuntu partitions ( /, swap, and a Fat 32 multi-access partition), plus Win XP and other data partitions, in that order, on the drive.

Tried to use the Live CD to install to the second partition, but that wants to install Grub to the MBR, which overwrites the partition information, rendering the others inoperable.

The bug in the 6.1 live CD installer ([https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130](https://launchpad.net/ubuntu/+source/ubiquity/+bug/67130)) also causes problems as I can not get the install to recognize existing partitions – this requires a workaround of removing partition, reformat, then install. Using this workaround pooches the existing partition structure... (tried a few times)...

I also tried the alternate CD, but this gets to the last partition stage and again then will not recognize the existing partitions, other than the “/” one flagged with the boot code by Bootit. I read about this workaround ([http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)) , but that is for the Live CD, and can not get it to work with the alternate CD.

I can get installer to see (and install to) the “/” partition (first Linux partition), but it does not see the other partitions (6 more) that exist after that one. I can not install with a swap partition (despite one being there), without messing up the partition table.

Need an expert here – with an idea as to how to get Ubuntu installed without having to reformat the partition (that is; to recognize the existing ones) AND not have to have Grub written to the MBR…

Long post  – sorry, complex subject.

HELP !

FFFFreddie

---

### Post by louieb on 2007-01-17
Good I like it when partitions are planed and the disk is partitioned in advance of installation.
I have install half a dozen Linux distros including Ubuntu 6.06.  Haven't install 6.10.  
The one thing they have in common is they will let you install in an existing partition.
When you get to the partition part of the install choose manual partitioning. 
You then choose you mount points for your / and swap partitions, and if you want the / partition  formatted, the file system type. 

A GRUB install does not overwrite the partition table section of the MBR. It places some code in the boot code section of the MBR. If you have another boot loader this may not be what you want. 
The hard drive has a boot sector, and each partition also has a boot sector. When you get to the GRUB part of the install (usually the last thing) it to will let you choose where to install it. In GRUB speak (hd0) is the MBR, (hd0,0) is the 1st partition, (hd0,1) is the 2nd partition ... and so on. It look like you want GRUB in the second partition so use (hd0,1). This will leave the MBR untouched. And you will have to manually add Ubuntu  to whatever boot loader you are using. 

Question what is an EMBR never heard of that? 
For a lot more detail checkout Herman's Dual Boot site. The link is in my signature.

---

### Post by salvo on 2007-02-03
> **louieb said:**
> Question what is an EMBR never heard of that?

Here is my simple understanding of EMBR.  It is a proprietary specification of TeraByte Unlimited, BootIt NG's (aka, BING) vendor.  It is capable of managing up to 255 boot partitions.  You can read more about it [here]("http://www.terabyteunlimited.com/kb/article.php?id=173").  I have been enjoying it on a W2K3 Server, and plan to use it for my upcoming Edgy Eft box, to be assembled next week.  

As for GRUB, it looks like you have the right idea, louieb.  I plan to consult [this]("http://bootitng.com/kb/article.php?id=171") article when I install Kubuntu next week.

---

