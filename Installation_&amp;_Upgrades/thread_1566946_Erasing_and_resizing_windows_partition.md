---
title: "Erasing and resizing windows partition"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2010-09-03
Hello,

This might be more of a windows question, but since the repartitioning of the computer is a first step towards installing Ubuntu, I've decided to put it here anyways.

There are currently three partitions on my computer. In windows, they show up like this (see pic):
1st Partition: Unnamed - OEM Partition
2nd Partition: OS (C:) - Boot, Page File, Crash Dump, Primary Partition
3rd Partition: RECOVERY - System, Active, Primary Partition

From Ubuntu, I determined that the System on the third partition means that the boot is located there, despite the fact that the OS itself is on the 2nd partition. Thus, if I delete partition 3, windows will lose the ability to boot and I won't be able to fix it without a CD that I don't have. What I would like to do is to erase the contents of this partition (using Gparted or something like that) and then shrink it to some small size so that I can reclaim this lost space. I need to know if there is some way of doing this which won't screw up the booting (I plan to make this a dual boot computer).

Thanks

---

### Post by plucky on 2010-09-03
If you are running Vista or Windows 7,use the tools provided under disk management to shrink the windows partition is the safest bet.

But as always when changing partitions,**backup your data**

When creating the Ubuntu partition,use an extended partition,so that you can have a number of logical partitions within the extended partition.That will give you 4 primary partitions,which is the maximum allowed per disk.

For an Ubuntu install,you need to create two partitions which is why you need the extended partition.

Good Luck

---

### Post by garvinrick4 on 2010-09-03
Run this in your ubuntu, you are running from live CD.

```
sudo fdisk -l  (small L)
``````
sudo blkid (2nd letter small L)
```If you can open gparted and take a screen shot of it and make a attachment here when you post the results of commands.
And what type of machine are you running? Dell, HP, so on.
There is away of doing it so boot is just fine.

---

### Post by Mark Phelps on 2010-09-03
> **EricDallal said:**
> Hello,

There are currently three partitions on my computer. In windows, they show up like this (see pic):
1st Partition: Unnamed - OEM Partition
2nd Partition: OS (C:) - Boot, Page File, Crash Dump, Primary Partition
3rd Partition: RECOVERY - System, Active, Primary Partition

From Ubuntu, I determined that the System on the third partition means that the boot is located there, despite the fact that the OS itself is on the 2nd partition... 
If this is Win7, you are wrong... 

The default Win7 install uses two partitions:
1) Boot partition
2) System partition

The win7 OS boot loader is on the second partition, not the third.

---

### Post by wilee-nilee on 2010-09-04
Just so we are all on the same page.
[http://ubuntuforums.org/showthread.php?t=1566730](http://ubuntuforums.org/showthread.php?t=1566730)

In this basically identical thread the bootscript has been posted.

---

### Post by EricDallal on 2010-09-04
I ended up solving the problem. Thanks for the help. Basically, I asked the same question on a windows 7 forum (I probably should have mentioned the OS). They led me to a program that did what I wanted, after which I needed to do repair disk three times before I could use windows again. Unfortunately, I couldn't find the ISO for the program so I just downloaded their installer and tried to do it while running windows. *Big* mistake. It led to the most catastrophic thing I have ever done to a computer. Luckily, I spent some more time on other forums, found some commands for the recovery disk command line and managed to get everything working again.

---

### Post by presence1960 on 2010-09-04
Mark is correct if you are doing a windows 7 clean install from a retail windows 7 DVD. In the case of OEM Windows 7 in most cases there is no boot partition. Most OEM manufacturers such as Dell, HP & Toshiba have the 3 partitions mentioned above: 1) system or utility partition, 2) Windows 7 & 3) Recovery Partition.

So depending on which computer you have and/or which installation method used you all are correct. It comes down to finding out which method the OP  has on his/her machine. 

Again I like to add that is why I usually insist on running the boot info script prior to giving any advice on boot/partitioning problems/questions.

P.S. After looking back at the link on the thread nilee-wilee posted the OP has a dell OEM setup. personally I would suggest creating a set of recovery DVDs if your machine has the option to do that, this way you can always restore your factory image. 

If you do not have the option of burning a set of recovery disks then I would opt for shrinking the Windows partition through windows disk management which you can find in Control Panel > Administrative Tasks. Create unallocated space by shrinking C:.

Then boot a gparted Live CD/USB and create an extended partition from the unallocated space. Once that is created create a logical ext 4 partition & a linux-swap partition inside the extended partition.

Boot the Ubuntu Live CD/USB and choose manual partitioning & use those 2 newly created partitions to install ubuntu.

**_Note: failure to create recovery disks or eliminating the Recovery Partition may lead to you being unable to restore the factory image unless you purchase the factory Image Disk(s) from Dell._**

---

