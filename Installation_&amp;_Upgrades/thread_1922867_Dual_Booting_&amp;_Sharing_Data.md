---
title: "Dual Booting &amp; Sharing Data"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by leehamer on 2012-02-09
I have just purchased a laptop and it has come pre installed with Windows 7, I bloody hate the OS (use it at work all the time). On my desktop and other laptop I am running ubuntu which I prefer. 
 
My better half has asked that I keep windows on this machine as there are a few bits of software that dont work under wine and I cant be arsed with using VM as I have had a few head aches with that in the past.
 
Basically I would like to have this laptop as a dual boot, but what I would like is to have all the documents/videos/pictures etc where both OS can have access. 
 
I have read a few blogs about this but I am a bit confused on the best method about doing this, I would like both OS to have a small partition and then store my files on a seperate.
 
What is my best method of doing this? I guess I am going to need 3 partitions at least??
 
Many thanks in advance

---

### Post by sudodus on 2012-02-09
I suggest that you have a common ***data*** partition with the NTFS file system. *This can be a separate logical partition inside an extended partition. There is a problem if you already have four primary partition, because there can be only 3 primary + 1 extended partition with the most common partition table system.*

Have a look at the following thread, where it is explained step by step

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1914298_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1914298")

---

### Post by WasMeHere on 2012-02-09
> **leehamer said:**
> ... I would like both OS to have a small partition and then store my files on a seperate.
 
What is my best method of doing this? I guess I am going to need 3 partitions at least??
 
Many thanks in advance
I suggest something like this (you edit with gparted when booted from the Ubuntu install CD or USB drive)

Partitions:
1. Windows NTFS
2. Data  NTFS
3. Extended
4.  Logical linux ext4 / (root file system)
5.  Logical swap

The data partition may also be inside the extended partition.

The setup may be altered by the partitions delivered (there might be one or several extra partitions), so please post the output of
```
sudo fdisk -lu
```

---

### Post by leehamer on 2012-02-09
cheers guys, I will follow the links provided and see how I get on... Would rather just bin Windows tho lol

---

### Post by darkod on 2012-02-09
Just a note that preinstalled laptops will usually come with more than a single win7 partition. In fact, lately they come with all four primary partitions used. Something like:
1. 100MB or 200MB System Reserved for win7 boot files (won't boot if you delete it)
2. Win7 OS partition (C: )
3. Restore partition
4. Tool partition

Take a look at all existing partition either in Gparted from live mode (before installing), or in windows Disk Management. Once you know what you have you can start making the plans.

---

### Post by Mark Phelps on 2012-02-10
If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

