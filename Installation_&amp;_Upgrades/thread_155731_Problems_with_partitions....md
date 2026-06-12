---
title: "Problems with partitions..."
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by sha_man on 2006-04-05
Hello I want to install Ubuntu. I have 2 Hds, both NTFS (atm), one is a 40 GB, the other 120GB (Samsung). On the 40 Gb, I have windows 2000 installed and I want to install Ubuntu on the 120 Gb. 
However, I was not able to create partitions on the 120GB HD with Ubuntu install CD, Live CD or Gparted... :( Either an error occured or simply it didn't make anything.
I made a chkdsk with windows on the drive to check for errors -> no errors with it. 
So I tought about Partitionmagic 8 (which I have). I checked for errors and I received this one: 

[I]#1529 Information mismatch in directory entry
A file attribute stored in a file record is different from the attribute stored in its directory entry. If this error is in a system file (file 0–10), Windows NT CHKDSK does not fix it, but Windows NT rebuilds the root directory on the partition the next time the operating system is started.[/I]

(to be seen on this page: [http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e?OpenDocument&src=bar_sch_nam&seg=ag](http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e?OpenDocument&src=bar_sch_nam&seg=ag))
I rebooted, same error :(
I also started to defragment my disc but it takes a very LONG time (in 10 hours only 20 %). :confused: 

What can I do? :( 

Thanks!

---

### Post by gerbman on 2006-04-05
[QUOTE=sha_man]Hello I want to install Ubuntu. I have 2 Hds, both NTFS (atm), one is a 40 GB, the other 120GB (Samsung). On the 40 Gb, I have windows 2000 installed and I want to install Ubuntu on the 120 Gb. 
However, I was not able to create partitions on the 120GB HD with Ubuntu install CD, Live CD or Gparted... :( Either an error occured or simply it didn't make anything.
I made a chkdsk with windows on the drive to check for errors -> no errors with it. 
So I tought about Partitionmagic 8 (which I have). I checked for errors and I received this one: 

[I]#1529 Information mismatch in directory entry
A file attribute stored in a file record is different from the attribute stored in its directory entry. If this error is in a system file (file 0–10), Windows NT CHKDSK does not fix it, but Windows NT rebuilds the root directory on the partition the next time the operating system is started.[/I]

(to be seen on this page: [http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e?OpenDocument&src=bar_sch_nam&seg=ag](http://service1.symantec.com/SUPPORT/powerquest.nsf/6c360f88152ecfce88256e91005066ac/e6223d1630e8ad8388256e8d006a841e?OpenDocument&src=bar_sch_nam&seg=ag))
I rebooted, same error :(
I also started to defragment my disc but it takes a very LONG time (in 10 hours only 20 %). :confused: 

What can I do? :( 

Thanks![/QUOTE]It's tough to tell really. It could be a bad drive. Do the error messages provide any other information? Can you wipe the drive clean with Partition Magic and start over?

---

### Post by Sef on 2006-04-05
> So I tought about Partitionmagic 8 

Don't use Partition Magic.  There are known issues with it and Linux.   If you must use commercial software, then use something else, like System Commander.

> However, I was not able to create partitions on the 120GB HD with Ubuntu install CD, Live CD or Gparted...  Either an error occured

What was the error?  Did you check out this site with an excellent tutorial on dual booting:  [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by gerbman on 2006-04-05
> Don't use Partition Magic. There are known issues with it and Linux. If you must use commercial software, then use something else, like System Commander.What are the issues?

---

### Post by sha_man on 2006-04-06
Well I didn't want to use partitionmagic, but the others didn't work.
Also, I followed [this Guide]("http://users.bigpond.net.au/hermanzone/"), but the thing is that I'm not able to create partitions, exactly like described [here]("http://ubuntuforums.org/showpost.php?p=836085&postcount=5"). However, I was NOT able to do it with QTParted, GParted or Ubuntu install-CD (All of them were newest version).
I will post the error message again later. Thanks anyway.

---

### Post by plors on 2006-04-06
[QUOTE=sha_man]Well I didn't want to use partitionmagic, but the others didn't work.
Also, I followed [this Guide]("http://users.bigpond.net.au/hermanzone/"), but the thing is that I'm not able to create partitions, exactly like described [here]("http://ubuntuforums.org/showpost.php?p=836085&postcount=5"). However, I was NOT able to do it with QTParted, GParted or Ubuntu install-CD (All of them were newest version).
[/QUOTE]
Are you sure you used the newest version of gparted? The newest version in ubuntus repository doesn't have to be the real newest version.
The last version of gparted is 0.2.4 and was released only 2 days ago, see [http://gparted.sourceforge.net]("http://gparted.sourceforge.net/") for more information.

---

### Post by sha_man on 2006-04-06
i used the live-cd version, yes.

---

### Post by sha_man on 2006-04-06
yes! :) :) :) 
Finally, I was able to create my partition with GParted! For that I backed up (to another disc) 80 Gb of 120 GB, and the disc was over 65% empty (free space). After that I defragmented touroughly and made my partition. It's working flawlessly at the moment :)

---

### Post by RomanIvanov on 2008-07-12
sha_man ,thanks a lot! I succeed by 56% of free space on disc and thorough defragmentation to make half of may disc absolutely free of data. I changed partition while installing of Ubuntu.

---

