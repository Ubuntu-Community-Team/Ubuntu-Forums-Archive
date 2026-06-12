---
title: "Weird UUID Problem on Bionic after disk-cloaning using Clonezilla"
date: 2018-09-15
forum: Installation &amp; Upgrades
---

### Post by manmath on 2018-09-15
The issue is both weird and annoying. So let me elaborate the case.

#1 I had bionic sitting on one hard drive, let's call it sda with partitions / (sda1), swap (sda2) and /home (sda3). It was an old and spinning drive, and definitely slow. So, last week I bought of an SSD, plugged to the system, created a partition (sdb1) and cloned sda1 to sdb1.
#2 When I rebooted it still booted that old spinning drive. Out of curiosity, I checked the UUID of the partitions, surprising both are the same.
#3 Then I changed the UUID of the SSD partition and made necessary changes in fstab. Annoying on reboot I saw the UUID has been changed on both the partition. A new UUID but that's the same on both partitions.

Please suggest me a solution.

---

### Post by oldfred on 2018-09-15
I am a believer in new installs to a new drive. Duplicate UUIDs not allowed & if gpt, duplicate GUIDs not allowed and you cannot (easily) clone one gpt partition as all data is in primary gpt partition, partition and backup gpt partition at end of drive. One advantage of gpt is the redundancy. 

You then can restore from your backups which also then is a good test that your backups are good. And you still have old drive to find any data you forgot to include in backup.

I backup /home and list of installed applications. You may want /etc, I typically only edit a couple of files & make copies into /home so it have them. If server type install, you may have database, web or other folders in / that must also be backed up.

You have to change UUIDs in grub, fstab, mount of swap and maybe some more places. Typically you have to reinstall grub to clean it up.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tea for one on 2018-09-15
> **manmath said:**
> The issue is both weird and annoying. So let me elaborate the case.

#1 I had bionic sitting on one hard drive, let's call it sda with partitions / (sda1), swap (sda2) and /home (sda3). It was an old and spinning drive, and definitely slow. So, last week I bought of an SSD, plugged to the system, created a partition (sdb1) and cloned sda1 to sdb1.
#2 When I rebooted it still booted that old spinning drive. Out of curiosity, I checked the UUID of the partitions, surprising both are the same.
#3 Then I changed the UUID of the SSD partition and made necessary changes in fstab. Annoying on reboot I saw the UUID has been changed on both the partition. A new UUID but that's the same on both partitions.

Please suggest me a solution.

Did you have both disks plugged in to the PC when you rebooted?

It seems that you had access to two root partitions (both with the same UUID), one home partition and one swap?

What was your intention when using Clonezilla e.g. move everything to the SSD or just move the OS?

---

### Post by manmath on 2018-09-15
Could not figure out what the problem was, but now it's working fine, the SSD is booting. What all did is:
#1 backed up data from spinning hard drive
#2 formatted the hard drive, then created just two partitions "/home" and "swap" (cos the root was cloned to ssd earlier).
#3 booted the system. there were hell lot of problems such as settings being lost, menus not invoking properly etc.
#4 then booted in rescue mode and deleted previous user and then created a new user.
#5 so far there has been no problem.

But the big question is -- should I assume that still will behave well now on? So far I've rebooted couple of times, run a couple of applications. All working fine.

> **tea for one said:**
> 
What was your intention when using Clonezilla e.g. move everything to the SSD or just move the OS?

Just to move the OS. That's why I cloned only root partition of the spinning drive. 

(The problem has been resolved. The hard drive had /, /home and swap partitions. I cloned the harddrive's / partition to ssd. Then I had 4 partitions with 3 UUIDs, One UUID for / partitions of both hard drive and ssd, and two UUIDs for /home and swap partitions in hard drive. Surprisingly, when I created new UUID for root partition of either hard drive or SSD, the same ID reflected in both the / partitions. As you noticed, it became a perfect setup for redundancy).

> **oldfred said:**
> Duplicate UUIDs not allowed & if gpt, duplicate GUIDs not allowed and you cannot (easily) clone one gpt partition as all data is in primary gpt partition, partition and backup gpt partition at end of drive.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Strange, but clonezilla did not complain during cloning the / partition of hard drive to the SSD. And now the problem has been resolved. I'm posting this reply booting from SSD (/ partition). I formatted the old hard drive (after backup) and created two partitions - swap and /. The process also led to deleting previous user and creation of a new user.

---

### Post by tea for one on 2018-09-15
> **manmath said:**
> But the big question is -- should I assume that still will behave well now on? So far I've rebooted couple of times, run a couple of applications. All working fine.

I would not assume that any PC will behave impeccably in the future.

For peace of mind, keep regular back ups of your personal data on an external device/cloud etc. 

In the event of an unforeseen catastrophe, you can always re-install Ubuntu from scratch.

Best wishes

---

