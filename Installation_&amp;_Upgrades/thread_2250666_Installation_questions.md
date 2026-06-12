---
title: "Installation questions"
date: 2014-10-30
forum: Installation &amp; Upgrades
---

### Post by neel3 on 2014-10-30
OK, here's the **computer specs**:

3rd gen i7
8 GB RAM
GeForce GT 650M

300 GB HDD partition (7200rpm SATA)
256 GB SSD (mSATA)
256 GB SDXC (external)
256 GB USB flash drive (external)

Here's the **Questions**...

Which drive should I install Linux on, and why ? 
Does Linux on SSD need swap ? 
Where should the swap partition go ? 
Does partitioning the SSD reduce it's performance ? 
Does partitioning SDXC / USB drive reduce it's performance?

What is the recommended amount of swap to run a 100-200 GB Windows 7 VM  ? (using Stealth VM, mostly for incompatible games)
Would increasing RAM to 16 GB, or SSD to 512 GB help run the Windows 7 VM ?

---

### Post by fantab on 2014-10-30
If its going to be only Ubuntu on the system then:

Installing Ubuntu on SSD is a good idea, SSD is faster than HDD and is supposedly more reliable than HDD.
With 8gb of RAM it is unlikely that SWAP will be used, however having a SWAP partition is a very good idea. I would make a small SWAP on SSD itself of about 2-4Gb.
If you 'hibernate' your computer then SWAP should be equal to or more than your RAM in Gib, not Gb.
I don't think partitioning SSD will reduce its performance.

Do you have UEFI boot? 
I'd recommend that you use GUID Partition Table [GPT], as it has definite [advantages]("https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT") over legacy MBR table.

SSD 256gb
200Mb FAT32 ESP [EFI System Partition]  'boot' flag - a must with UEFI boot
5Mb unformatted partition (to boot Linux OS from GPT in legacy mode) - you won't need it if you use the ESP, but having it around is a good idea.
30Gb Ext4 '/' for Ubuntu system files
25Gb Ext4 free (If you want to dual boot another linux distro or another Ubuntu flavor or version)
???Gb Ext4 '/home' for your personal data and users files
2-4Gb linux_SWAP

I don't use VM, never have, so I am not sure about it. However what you have is more than enough IMO.

---

### Post by grahammechanical on 2014-10-30
I only have a very little experience with VM. I do not have enough RAM even to play a little bit. So, I would say RAM storage is needed by VMs more so than disk storage. Of course we need enough disk space for both operating systems and any applications that we install.

 I cannot say if 8GB RAM is too little. It really is coming to something if 16GB RAM was necessary to run Windows in a VM on Linux. What do you expect to do in Windows 7 that would require massive amounts of RAM?

Regards.

---

### Post by Bucky Ball on 2014-10-30
Which drive should I install Linux on, and why ? SSD, fastest and OS should go there.
Does Linux on SSD need swap ? Yes.
Where should the swap partition go ? On a HDD.
Does partitioning the SSD reduce it's performance ? Leave 20% empty space and no. 
Does partitioning SDXC / USB drive reduce it's performance? No. 

2Gb /swap unless you hibernate. Then same size as your installed RAM. Nothing to do with HDD size. 
RAM makes a difference with VMs. As long as you have the hard drive space to install VMs, bigger does not make any difference to speed or performance (if running on a large NTFS partition bigger will be slower eventually because they spit data all over).

Best to research these things some before posting. VMs share the RAM, so with 16Gb, and depending on the processor and if you have the hard drive space to install them, you could have eight VMs running using 2Gb of RAM each.

If you are intending to run a Ubuntu host with Windows as the VM then you don't need anything like 16Gb.

---

