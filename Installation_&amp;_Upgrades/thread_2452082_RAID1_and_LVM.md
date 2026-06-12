---
title: "RAID1 and LVM"
date: 2020-10-16
forum: Installation &amp; Upgrades
---

### Post by alonaroll on 2020-10-16
HI Guys

I read that it is possible to implement RAID with LVM and that there is no need for MD. I would like to know if this is an well tested setup or should I create
my MD and than have my LVM on top. What are the implications of using encrypted LVM.

Thanks
Al

---

### Post by TheFu on 2020-10-16
RAID1, yes.  RAID0, yes.  I don't know about the others.  RAID1 performance is a tiny bit slower than the mdadm solution, but the added flexibility provided more than makes up for a 0-2% performance difference to me.

LVM and encryption are separate. Encryption as handed by LUKS can be deployed at different levels of the stack.  It can be above or below mdadm or LVM.  Most of the time, I've seen LUKS deployed at the partition level, below LVM.  One rule to keep in mind with LVM, don't span data across physical disks, unless RAID1 or RAID10 is involved AND you have excellent backups.  RAID1 can be enabled and disabled with LVM.  RAID10 has to be enabled before any data is written so the striping can occur. It is not possible to convert RAID1 into RAID10 later.  RAID01 should not be used. There are failure modes that end up with data loss.  Rather than RAID01, use 2 RAID1 configurations if the setup has to occur after the fact.

If I needed RAID1 today, I'd implement it using LVM. 

Some background, so you get where I'm coming from.

My first use of LVM on Linux was around 2000. I'd used logical volume managers on commercial Unix systems for about 5 yrs prior to that time. That use at home ended with 80% data lose due to a stupid admin choice.  I'd used LVM to concatenate data across 3 HDDs. I learned a hard lesson. At the time, I didn't have backup religion. That failure converted me.

I have 2 RAID1 arrays implemented with mdadm running today. These have been around since 2007 and were moved from RAID5 to RAID1 when my HDD sizes changed from 320G --> 2TB. I've had failed disks, loose SATA connections, and bone head admin mistakes over the years.
```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdf2[0] sdg2[1]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sde2[3] sdd3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
```
When these were spin up, I wasn't using LVM at home, so they are simple arrays with file systems.  The last 5-8 years, I've converted into an LVM believer for many reasons, but mainly for the added flexibility LVM provides.

Regardless, when you setup storage, it is worth running tests to tune the block sizes for your specific workloads.  **hdparm** is the tool for that and with a little effort, the trade-off for your situation can make a significant performance difference. Do the same for stripe sizing.

---

### Post by alonaroll on 2020-10-16
> **TheFu said:**
>  Most of the time, I've seen LUKS deployed at the partition level, below LVM. 

Thanks for for the feedback, how is LUKS implemented below the LVM at install time ?

---

### Post by TheFu on 2020-10-16
> **alonaroll said:**
> Thanks for for the feedback, how is LUKS implemented below the LVM at install time ?

I don't know the details, just what the results are.  Here's my encrypted laptop with 
Disk --> Partition --> LUKS container --> LVM --> PV/VG --> LVs
[https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)

I had to reduce the root LV, resize the swap LV, and create the other LVs for my desires post-install.  Doing it right after the install and first patching finish makes it easier and less risky.  The "Try Ubuntu" environment from the installation ISO is handy too, which is needed to decrypt the storage and vgchange -ay the internal HDD/SSD so access is there to lvreduce the "root" LV.  Last time I did an install, the entire sda3 was taken for the "root" LV, which isn't what I want, ever.  OTOH, effectively everything under the sda3 partition is encrypted as you can see by the disk layout in the link above.

I wish the installer doesn't use MSDOS partitions, but use GPT instead and I wish it would let me choose in a pretty layout way, what goes where and how much with a nice GUI and with the ability to leave some unencrypted storage outside sda3.

But we don't always get what we want, sometimes we get what we need.

---

### Post by alonaroll on 2020-10-18
> **TheFu said:**
> I don't know the details, just what the results are.  Here's my encrypted laptop with 
Disk --> Partition --> LUKS container --> LVM --> PV/VG --> LVs
[https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)



This was very useful thanks. I gather then to  have your LVM across multiple physical disks is not recommended - does it meant then that in enterprise each disk which is part of a VG, is also part of a physical RAID as well ?

---

