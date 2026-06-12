---
title: "installing ubuntu in vista problems"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by katya_sehgal on 2011-10-12
I am very new to ubuntu.
Either through wubi or through cd installation, I am unable to see my existing vista partitions. I don't get the option that lets me install 'alongside vista'. 
while installing ubuntu, there was a 'prefix' error.
I had partitioned hard drive using acronis. 
How do I get vista and ubuntu working together?

I am not used to terminal commands. And I am eagerly looking forward to trying out openshot editor. 
Since I am in need, I have not extensively checked the internet. 

Regards.

---

### Post by mastablasta on 2011-10-12
i am not sure this has anything to do with acronis, but it is better to just use native windows disk manager for creating partitions.
 
now the important thing here is porbably how many partitions you have and what type are the partitions. does the linux see windows drive if you boot into live session ("try it" option)?
 
also when booting live session, you can run gparted from terminal to see which disk the Ubuntu actually sees..

---

### Post by katya_sehgal on 2011-10-12
using acronis, I divided C into C and F. Windows is in C. My other data is in F. D is for recovery as designed by Vista.

i get 3 options with ubuntu. i chose the 'try demo' one. I got into Ubuntu, checked gparted. it does not show windows. i clicked on install ubuntu. it gave me 2 option. Erase disk and install and 'try something else'. When I click try something else it does not show windows in the disk partition option.

any other way to see?

---

### Post by katya_sehgal on 2011-10-12
i'd be glad to have the problem solved. would be installing ubuntu for 2 people more. 
I, especially, am in a hurry to try it.

---

### Post by Quackers on 2011-10-12
Please boot from the Ubuntu live cd/usb and select "try Ubuntu".
When the desktop loads please open up a terminal and post the output of this command. ```
sudo fdisk -lu
```

---

### Post by katya_sehgal on 2011-10-12
as you asked.

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326   de  Dell Utility
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *   323516976   483138809    79810917    7  HPFS/NTFS
/dev/sda4        21157605   488394751   233618573+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5        21157668   323516969   151179651    7  HPFS/NTFS
/dev/sda6       483153920   488394751     2620416   dd  Unknown

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 



---

### Post by Quackers on 2011-10-12
Sorry for the delay katya_sehgal

It seems that Dell in their original installation used all 4 available primary partitions. When you created more partitions you exceeded the maximum number available.
As a result your partition table now has a problem.

/dev/sda4 is an extended partition, which holds logical partitions /dev/sda5 and /dev/sda6. 
Unfortunately if you look at the start and end sectors of the extended partition (21157668 and 488394751) and then look at the start/end sectors of /dev/sda3 (323516976 and 483138809) you will see that /dev/sda3 resides completely within the extended partition.
As /dev/sda3 is a primary partition (which cannot reside within an extended partition) this constitutes an "illegal" partition table.
I am not surprised that the Ubuntu installer refuses to show the partitions as it baulks at such things, to stop further errors being made.

It is almost certainly the case that partition sda6 (a Dell Datasafe partition, I think) was once a primary partition too.
I am unclear where sda5 came from, as 4 primary partitions probably existed before that one appeared.

These partition problems is the reason why you are not getting the "install alongside" option from the Ubuntu installer.

In short I am extremely unsure as to how to advise you.
The first thing I would recommend is to backup everything you would not want to lose from your Vista installation.
It may be that the whole system will need to be re-installed.

I will ask other forum members to look at your situation and give their views.

---

### Post by oldfred on 2011-10-12
First backup the partition table with this from the Ubuntu liveCD terminal. Copy the file partssda.txt to another device as a backup. This is inaddition to full backups of any important data.

sudo sfdisk -d /dev/sda > partssda.txt

Then download this program that will analyze your partitions and suggest corrections. 

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I think the rodsbooks site explains the process but if you have questions post (copy & paste) the output from the fixparts program and we may be able to help.

---

### Post by Quackers on 2011-10-12
Thanks oldfred.
I may also be inclined to delete /dev/sda5 first - but that's based on it being your new F: drive in Windows - and hopefully still empty.

---

### Post by oldfred on 2011-10-12
+1 on Quackers suggestion.

After discussion with coffeecat, I think fixparts would move sda3 into the extended and then Windows would not boot. If sda5 is deleted first then you would not have to move sda3 into the extended to resolve the overlap. If there is any data in sda5 back it up first and just delete it. Some of the partition tools may not make it easy to delete as the overlap causes confusion.

---

### Post by katya_sehgal on 2011-10-12
thank you.
i shall re-read and understand and then revert. I do have data in the f drive, the one I created.

---

### Post by katya_sehgal on 2011-10-13
> **oldfred said:**
> First backup the partition table with this from the Ubuntu liveCD terminal. Copy the file partssda.txt to another device as a backup. This is inaddition to full backups of any important data.

sudo sfdisk -d /dev/sda > partssda.txt

Then download this program that will analyze your partitions and suggest corrections. 

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I think the rodsbooks site explains the process but if you have questions post (copy & paste) the output from the fixparts program and we may be able to help.

This is what I typed and got: Is this alright? Does this ' back up'? How do I copy partssda to another device. In windows I have backed up important data and software. 

```
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > partssda.txt 
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ clear

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > partssda.txt
ubuntu@ubuntu:~$ 
```

If I run the software you have suggested, would it delete anything anywhere? The additional F drive I had created contains much of the data. 

C and D drive are the naturals.
E is cd rom drive
F is my creation through Acronis and it contains data. 

I wonder if **'delete Stray gpt data from MBR drives'** is a warning.

---

### Post by katya_sehgal on 2011-10-13
From fix parts
> I do *not* recommend using FixParts for routine partitioning tasks such as deleting partitions, changing the active/bootable flag, or changing type codes. Although the program can do these things, these features are provided as conveniences when repairing more serious problems.

Since I am unaware about ubuntu and terminals, I am going just by indications.



> **Quackers said:**
> Thanks oldfred.
I may also be inclined to delete /dev/sda5 first - but that's based on it being your new F: drive in Windows - and hopefully still empty.

F drive is not empty. C and D came with the system. E is cd drive and F is my creation, in the case something happens to C.

Also, please check the posts above with regards to partition table backups.

---

### Post by Quackers on 2011-10-13
The command ```
sudo sfdisk -d /dev/sda > partssda.txt
``` having been run should have created a text file in your home folder called ```
partssda.txt
``` This file is a written record of your partition table and can be copied somewhere for safe keeping.

I suspect that 4 primary partitions were already being used by your system, originally.
When you split C: into C: and F: you created a 5th partition. This 5th partition can not legally exist, so your system made one of your primary partitions an extended partition and changed one of your NTFS (Windows) partitions (probably F:) into a logical partition - along with the Dell Datasafe partiton.

It may be that no other partitioning program will "see" your partition layout due to the illegality of sda3. Therefore you may have no choice but to use Fixparts to delete sda5 and then try to fix the other inconsistencies.

Good luck  :-)

Edit  Actually, are all partitions "seen" in Windows Disk Management screen?

---

### Post by katya_sehgal on 2011-10-21
I get that there was no 'straight' solution for the program. Has it been documented anywhere? It may not be isolated and may discourage others from adopting Ubuntu... Like a few people to whom I proposed Ubuntu.

To QUACKERS

c - basic NTFS Healthy 
d (recovery) - basic ntfs healthy (primary partition)
f (I created this) - basic ntfs healthy (logical drive)

thanks for your time. anything I may do? 



> **Quackers said:**
> The command ```
sudo sfdisk -d /dev/sda > partssda.txt
``` having been run should have created a text file in your home folder called ```
partssda.txt
``` This file is a written record of your partition table and can be copied somewhere for safe keeping.

I suspect that 4 primary partitions were already being used by your system, originally.
When you split C: into C: and F: you created a 5th partition. This 5th partition can not legally exist, so your system made one of your primary partitions an extended partition and changed one of your NTFS (Windows) partitions (probably F:) into a logical partition - along with the Dell Datasafe partiton.

It may be that no other partitioning program will "see" your partition layout due to the illegality of sda3. Therefore you may have no choice but to use Fixparts to delete sda5 and then try to fix the other inconsistencies.

Good luck  :-)

Edit  Actually, are all partitions "seen" in Windows Disk Management screen?

---

