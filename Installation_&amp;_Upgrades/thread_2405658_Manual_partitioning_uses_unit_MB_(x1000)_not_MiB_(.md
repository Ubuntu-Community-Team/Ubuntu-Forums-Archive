---
title: "Manual partitioning uses unit MB (x1000) not MiB (x1024), why?"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by dinkidonk on 2018-11-09
During installation of Ubuntu I would like to manually partition my drive. But for some irrational reason the partitioning tool uses unit MB (1.000.000 bytes) and not MiB (1.048.576 bytes) and this makes it impossible to do a decent partitioning job since the partitions must me 4KiB aligned. If I want to create a 500MiB partition for EFI that is not possible, specifying 500MB will create a partition of (500.000.000 / 4.096 = 122.070,3125 : 4.096 * 122.070 = 499.998.720 bytes) 499MB or ~476,84MiB and this annoys me quite a lot!

Does anyone know why the MB unit is used in favour of MiB? Is there a workaround to make the installation process use MiB instead? Or should I simply start the live media and use whatever partitioning tool (eg. parted CLI) to partition the drive prior to installation?

---

### Post by The Cog on 2018-11-09
Why do you want to create a partition of exactly 524.288 Megabytes anyway? Sounds like an odd number to me. If you're that hung up on using powers of two, perhaps you should be trying to partition 536.870912 megabytes instead. 

If you are worried about alignment, I really doubt that parted would attempt to start a partition partway through a sector. I think I read somewhere that for best performance, partitions should start on a cylinder boundary though I could be wrong there.

What tool are you using? parted has an option to accept units of MiB, use the command "unit MiB".

---

### Post by dinkidonk on 2018-11-09
The installation tool allows you to create a partition of 500MB even though this is not a valid size due to alignment. The size is then corrected to 499.something which is not what I want and this seems not right to me. If I wanted to create a swap partition of (2xRAM) 32GiB to use for hibernation, it would also end up being something else (lesser) than 32GiB and this seems wrong. I think it would be much better if it was possible to select units (MB, MiB, GB, GiB etc.) as it is possible with parted and other tools. Using a floating point to specify a partition size is downright silly..

---

### Post by QIII on 2018-11-09
Mechanical hard drive engineers design/manufacture in MB.  It's easier to count by 1000s on your fingers than 1024s.

The MB/MiB disparity will always be there.

Memory engineers are forced to think in 1024s by the nature of binary computing, and they can count that way.

---

### Post by oldfred on 2018-11-09
Do not force odd alignments, new hard drives & SSDs need correct alignment.
[https://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](https://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Generally if you have lots of RAM, you only need 2MB of swap, just to have some. It will not normally be used and you do not want it used as it makes system really slow. And normally best not to hibernate.Now Ubuntu's default is a swap file of 2GB.

---

### Post by dinkidonk on 2018-11-10
> **QIII said:**
> Mechanical hard drive engineers design/manufacture in MB.  It's easier to count by 1000s on your fingers than 1024s.

I do not recall ever seeing a hard drive with a size which is a multiple of 1MB (1.000.000 bytes). My current hard drive is a 1TB HGST drive of 1.000.204.886.016 bytes and my system drive is a 250GB Crucial SSD of 250.059.350.016 bytes, both are a multiple of 1KiB and not 1KB. When you manually partition your drive and ask for a partition of 500MB, click OK and see a partition of 499MB in the list this appears like a bug. You cannot align partitions with the MB unit so it seems odd to use it as a hard-coded unit anyway.

---

### Post by mitesh.agrwl on 2018-11-10
> **dinkidonk said:**
> I do not recall ever seeing a hard drive with a size which is a multiple of 1MB (1.000.000 bytes). My current hard drive is a 1TB HGST drive of 1.000.204.886.016 bytes and my system drive is a 250GB Crucial SSD of 250.059.350.016 bytes, both are a multiple of 1KiB and not 1KB. When you manually partition your drive and ask for a partition of 500MB, click OK and see a partition of 499MB in the list this appears like a bug. You cannot align partitions with the MB unit so it seems odd to use it as a hard-coded unit anyway.

The Technology has improved a lot. 
>  					[IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **QIII** 					[[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13815079#post13815079") 				

 				Mechanical hard drive engineers design/manufacture in MB.  It's easier to count by 1000s on your fingers than 1024s.

 

The above statement may be obsolete but not completely wrong. With the arrival of SSD devices I guess the mechanical engineering had got reduced but still manufacturers do not tell you all that you need to know!

[Informative Thread on Bad Sectors and dealing with them]("https://askubuntu.com/questions/241944/how-to-fix-the-hard-drive-bad-sector")

The above thread reveals a lot about the hard disks we do not know!

---

### Post by dinkidonk on 2018-11-10
> **mitesh.agrwl said:**
> The Technology has improved a lot.

What do you mean by that? Since the implementation of Advanced Format drives, sector sizes have been 4096 bytes natively and this does not comply with a manufacturing process which uses MB.

---

### Post by oldfred on 2018-11-10
My drives per inxi:

Dell Haswell based or about 4 years ago:
Drives:    HDD Total Size: 1000.2GB (4.2% used)
           ID-1: /dev/sda model: ST1000DM003 size: [COLOR=#ff0000]1000.2GB[/COLOR] temp: 40C

Asus Z97motherboard system
Drives:    HDD Total Size: 1159.2GB (11.7% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: [COLOR=#ff0000]128.0GB[/COLOR] temp: 0C
           ID-2: /dev/sdb model: WDC_WD10EZEX size: [COLOR=#ff0000]1000.2GB[/COLOR] temp: 31C
           ID-3: /dev/sdc model: Name n/a size: 31.0GB temp: 0C

Gigabyte Z170 system 
Drives:    HDD Total Size: 1250.3GB (7.0% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: [COLOR=#ff0000]250.1GB[/COLOR] temp: 0C
           ID-2: /dev/sdb model: HGST_HTS721010A9 size: [COLOR=#ff0000]1000.2GB[/COLOR] temp: 41C

But once formatted it is less and only formatted size really counts.

---

### Post by dinkidonk on 2018-11-10
**@oldfred**: Those GB numbers does not tell anything about the accessible byte size of the drives, use: "sudo parted /dev/sd*X* unit B print" instead. I bet all your HDD's are a multiple of 4096 and all SSD's are a multiple of 4096 or 512 because that is how they are physically formatted / constructed. I also bet than no one owns a HDD with an accessible byte size which is a multiple of 1MB (1.000.000 bytes) and that makes the MB unit seem like a weird choice to hard code into a partitioning tool. Cannot remember if this is inherited from the Debian installer or if this is introduced by canonical / ubuntu, though..

---

### Post by oldfred on 2018-11-10
On my Z170 system parted agrees with inixi. 1000.2 
Historically various Linux tools used MB or MiB, or not always consistent to add to confusion.
The only info that really matters is the formatted available space.

fred@Bionic-Z170N:~$ sudo parted /dev/sdb unit B print
[sudo] password for fred: 
Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000204886016B

---

### Post by mitesh.agrwl on 2018-11-10
> **dinkidonk said:**
> **@oldfred**: Those GB numbers does not tell anything about the accessible byte size of the drives, use: "sudo parted /dev/sd*X* unit B print" instead. I bet all your HDD's are a multiple of 4096 and all SSD's are a multiple of 4096 or 512 because that is how they are physically formatted / constructed. I also bet than no one owns a HDD with an accessible byte size which is a multiple of 1MB (1.000.000 bytes) and that makes the MB unit seem like a weird choice to hard code into a partitioning tool. Cannot remember if this is inherited from the Debian installer or if this is introduced by canonical / ubuntu, though..

Linux users or Canonical/Ubuntu did not introduced it. This was an age old representation which they followed. For proof check the images attached.

Image source: Operating Systems Design and Implementations, Second Edition, by William Stallings, Published by Pearson Education.

---

