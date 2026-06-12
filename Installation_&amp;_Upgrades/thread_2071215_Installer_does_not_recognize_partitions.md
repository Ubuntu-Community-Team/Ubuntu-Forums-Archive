---
title: "Installer does not recognize partitions"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by arlindi on 2012-10-14
I recently purchased an ASUS A55V laptop with Windows 7 Home Premium installed (upgrading in windows 8 professional in a few weeks). Since I've just started my computer engineering major I need gnu/linux and I chose Ubuntu. 

I've been trying to get it working for like 7 hours now but without success.


1) I start the installation from a live cd and everything goes well until it asks for a partition/drive. The installer doesn't recognize my windows partitions.(I had already made a 30gb partition for ubuntu + I had my Windows partition and an additional partition). I poke around for half an hour or so and can't fix it so I decide to install wubi.

2) Wubi installs just ok but give me an error when booting. I find out that Wubi + UEFI booting = BUG. So I give up after another wasted hour.

3) I go back in the live cd for a "Native" installation. I search and search the net for hours. Try a lot of guides and all but nothing seems to work.
-gParted shows my drive as one big unallocated storage.
-fdisk shows only dev/sda 
- i tried poking around with parted and fixparts but I couldn't do anything.

I'm sorry if this has been answered before but I'm really kinda desperate atm. I'm looking for an answer as I need to start learning/practicing on Linux and exercising with C.

I was also wondering if this is a problem only for Ubuntu or a global problem (meaning same thing will happen if I try to install fedora, which I will if this doesnt get resolved in the next 2-3 days).

Thanks a lot,
Arlind

---

### Post by oldfred on 2012-10-14
Is this a new system with Intel Smart Response Technology? That uses RAID which does not have drivers on the Desktop installer.

Or is this system using all 4 primary partitions?

Post this from liveCD or USB.

Install this first:

sudo apt-get install mdadm

Then list partitions:

sudo parted /dev/sda unit s print

---

### Post by arlindi on 2012-10-16
Thanks for your answer.

The system has a 3rd Generation i7 3610QM processor. I think the Intel Smart Response Technology was only for 2nd generation Interl CPUs but I'm not sure.

I've been very busy with classes and I haven't had time to make another liveCD session but I will in a few hours and I'll post the results.

Thanks again!

> **oldfred said:**
> Is this a new system with Intel Smart Response Technology? That uses RAID which does not have drivers on the Desktop installer.

Or is this system using all 4 primary partitions?

Post this from liveCD or USB.

Install this first:

sudo apt-get install mdadm

Then list partitions:

sudo parted /dev/sda unit s print

---

### Post by darkod on 2012-10-16
Just to add, when you say "you made a 30GB partition for ubuntu", I hope you actually mean you made unallocated space of 30GB ready for ubuntu.

If you literary make a partition in windows, it will be ntfs and linux doesn't install on ntfs. The space needs to be unallocated, or you can make linux partitions from live mode in advance but that beats the point since you can make them when installing too.

If you did make a 30GB ntfs partition, delete it.

---

### Post by arlindi on 2012-10-16
> **darkod said:**
> Just to add, when you say "you made a 30GB partition for ubuntu", I hope you actually mean you made unallocated space of 30GB ready for ubuntu.

If you literary make a partition in windows, it will be ntfs and linux doesn't install on ntfs. The space needs to be unallocated, or you can make linux partitions from live mode in advance but that beats the point since you can make them when installing too.

If you did make a 30GB ntfs partition, delete it.

Yes I left 30 gb unallocated space but ubuntu shows all 500 gb of my hard drive as unallocated.

---

### Post by oldfred on 2012-10-16
You may still have the 4 primary partition issue.

From post #2

Post this from liveCD or USB.

Install this first:

sudo apt-get install mdadm

Then list partitions:

sudo parted /dev/sda unit s print

---

### Post by arlindi on 2012-10-16
> **oldfred said:**
> You may still have the 4 primary partition issue.

From post #2

Post this from liveCD or USB.

Install this first:

sudo apt-get install mdadm

Then list partitions:

sudo parted /dev/sda unit s prin

I just did that and this is the result:

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s prin
Error: Unable to satisfy all constraints on the partition.

---

### Post by oldfred on 2012-10-16
I fixed my post above, I left off the t in print.

sudo parted /dev/sda unit s print

---

### Post by arlindi on 2012-10-16
> **oldfred said:**
> I fixed my post above, I left off the t in print.

sudo parted /dev/sda unit s print

Same results seems.

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: Unable to satisfy all constraints on the partition.

EDIT: That is the same message I get in gParted when I click on the unallocated space.

EDIT 2: Here's my sudo fdisk -lu
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2902cc6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-10-16
Because it is gpt, fdisk does not work. That is normal. If using gpt, you can download gdisk which is the fdisk equivalent for gpt partitioned drives. Also if gpt then there is no limit (actually 128 )  on the number of primary partitions.

Did you install the RAID driver first? as posted above?

---

### Post by arlindi on 2012-10-16
> **oldfred said:**
> Because it is gpt, fdisk does not work. That is normal. If using gpt, you can download gdisk which is the fdisk equivalent for gpt partitioned drives. Also if gpt then there is no limit (actually 128 )  on the number of primary partitions.

Did you install the RAID driver first? as posted above?

No I didn't install the RAID driver. Can you link to a guide on how to install it? What should I do?

Thanks a lot :)

---

### Post by oldfred on 2012-10-17
See post #2.

I do not know RAID, driver should let you at least see RAID partitions, but you have to use RAID to modify RAID. I think that is why most have turned off the RAID, modified system and maybe then turned it back on. Not sure if it is that easy or not.

---

