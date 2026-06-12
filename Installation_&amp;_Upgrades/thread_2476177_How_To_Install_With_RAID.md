---
title: "How To Install With RAID"
date: 2022-06-18
forum: Installation &amp; Upgrades
---

### Post by turtley-linux on 2022-06-18
Hello,
I know absolutely nothing about RAID and would like to install Ubuntu Desktop onto my Lenovo TS140 with three hard drives. Are there any good resources to help me get started, because I do not know the first thing about how to go about installing on this kind of setup?
Thanks in advance.

---

### Post by TheFu on 2022-06-19
> **turtley-linux said:**
> Hello,
I know absolutely nothing about RAID and would like to install Ubuntu Desktop onto my Lenovo TS140 with three hard drives. Are there any good resources to help me get started, because I do not know the first thing about how to go about installing on this kind of setup?
Thanks in advance.

RAID solves 2 problems and only 2 problems.   Nothing else.
* High Availability
* Higher Read Performance (sometimes)

Canonical has different installers, so the exact version to be installed will matter.
Will you be using 
* software RAID
* hardware RAID
* Fake RAID

They each have issues, pros/cons.  FakeRAID and Hardware RAID tie you to specific hardware and unless you have a spare of that hardware, accessing the information stored in those formats will be difficult/impossible if the controller isn't identical.

SoftwareRAID is the most flexible, but I haven't seen any Canonical installer support it.  There are 2 sub-versions of SW-RAID.  mdadm and LVM-RAID.  I've used LVM-RAID for the OS in a RAID1 setup mainly as a challenge. None of my production systems use it for the OS.

In general, I've used RAID for data storage, DBMS, and Virtual Machines only in production.  

RAID never, ever, replaces backups.  If you don't have an excellent backup plan, don't bother with RAID.  Backups solve 1001 issues. RAID solve 2 issues and sometimes the fix for RAID is to wipe the array and restore from backups.

The file system used will impact RAID choices too. If you are using ZFS or BTRFS, there are specific choices with those.  Be very careful if you choose BTRFS on a system with more than1 storage device.  There are some not-great failure modes with it.  [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)
If you use LVM, you'll probably use ext4 or xfs for the file system. Setting up a mirror can happen before or after the install. This means you do a normal install to 1 disk, being certain to check the "Use LVM" box during install, then you can follow LVM instructions to make it RAID1 (a mirror) with a second drive post-install.

If you have SSDs, or better, Enterprise SSDs, the failure rates on those are so low that using RAID doesn't actually make sense unless you are a business and dropping 1 transaction could end your business.  Must have been about 5 yrs ago when a high-end RAID vendor presented the failure rates of their enterprise RAID + SSDs.  He said they were happy to sell people 2x more storage than was necessary, but that the numbers and failures just made that unwise for most businesses besides banks and credit transaction agencies.  Of course, you and I aren't going to have one of those enterprise SSD-RAID systems at home.

Before doing an LVM install, I like to pause the installer and setup the LVM PV, VG, and LVs in the way I prefer to prevent the boneheaded solution that the defaults provide. It is like the installer hasn't any clue of LVM best practices.  Then, during the install - choose "Do something Else" when the Storage setup part happens and just pick which LV will be used for each mount location.  The main greatness in using LVM is flexibility. That comes from LVMs really easy way to extend the size of a running LV as needed, where needed, but that only works when we don't pre-allocate all the storage in the PV/VG to all the LVs.  In short, use only what you need in the initial install - which is probably less than 40G total across all the LVs.  There are a few posts in these forums about disk layouts which go into LVM layouts.  I'd recommend finding those, doing a little reading, and practice a few test installations, assuming you choose to use LVM.

I don't know how to use SW-RAID that uses mdadm as the solution for the boot/OS drive. Perhaps someone else here does?  I've only used mdadm on data drives and it has worked well, though without the same flexibility that LVM-RAID provides.  20 yrs ago, we would setup mdadm RAID, then lay down LVM on top of that.  About 7 yrs ago, the LVM guys stole the mdadm code and merged it into LVM where only LVM commands are used to manage the LVM-RAID storage.

For pure data storage these days, I'd use ZFS, but that is still experimental for the OS/boot.

---

### Post by turtley-linux on 2022-06-19
@TheFu Thank you so much for the extremely detailed response! I will definitely look into more information about this to try to implement these things pre-install. I appreciate the time you spent answering my question.

---

