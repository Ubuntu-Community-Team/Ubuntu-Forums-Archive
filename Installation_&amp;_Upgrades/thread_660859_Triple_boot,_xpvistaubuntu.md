---
title: "Triple boot, xp/vista/ubuntu"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by zurn on 2008-01-07
I there, here's the scenario:

I have a Sata 500G HD with 4 partitions. I also have another Sata 500G with 1 Partition and a 320G ide HD with 1 Partition.

On the 1st 500G
Partition 1: XP SP2 (40gigs)
Partition 2: Vista 64 bit (40 gigs)
Partition 3: Empty (40 gigs)
Partition 4: Remaining space for storage

Xp and Vista work fine in dual boot, then last night I wanted to install Ubuntu 7.10 64 Bit, so I installed it using the alternate cd (cause of my geforce 8800 gt) . Everything went fine, I told Ubuntu to use the 3rd partition and Grub defected my previous mbr and said it was added to grub.

After the installation is completed I reboot, but then I get an error telling me that I have chosen an invalid disc. At first I thought Ubuntu installed Grub on my 2nd 500G so I told my bios to use that for a boot drive but it gave me the same error.

Any ideas where grub is installed and how does Ubuntu chose on what partition it installs grub? Should it not install grub on the active partition? I have'nt tried booting from my 320G hd yet, i'll do that right now.

Thanks for the help.

---

### Post by Pumalite on 2008-01-07
Did you make the third partition FROM Vista?

---

### Post by zurn on 2008-01-08
I made that partition while installing XP, but it was not formatted.

---

### Post by Pumalite on 2008-01-08
You have to format it. Ubuntu does not install in unallocated space.

---

### Post by zurn on 2008-01-10
But why does it ask me what file system that I want on it? I thought it formatted the partition with the ext3 file system while installing?

---

### Post by PmDematagoda on 2008-01-10
What choice did you select when you reached the partitioning part?

---

### Post by zurn on 2008-01-11
> **PmDematagoda said:**
> What choice did you select when you reached the partitioning part?

I chose the empty partition and selected "auto" so it would create the ext3 partition and swap partition on its own.

---

### Post by DavidTangye on 2008-01-11
I cant say for sure, but I think your choosing auto cold have been a problem. I always choose manual partitioning, so I can see what is going to happen. I think I should have too. You wold explicitly select the 3rd partition, tell it to put the '/' there, and to format it ext3. (Plus also carve out 1Gig of the free space for a swap partition) Then it would do exactly that, and install Ubuntu there.

It must have installed ubuntu somewhere though. I wonder where it went :-). Perhaps it decided to leave the first disk alone and 
carved up a different disk? Cant you boot something, eg a 'Live Cd' or XP still, and run a partition manager to see what has happened?

---

### Post by zurn on 2008-01-11
I was able to restore my vista mbr so everything is back to normal. If I open Xp's disk management I can see the partitions Ubuntu has made. It's exactly what it told me it would do, it seperated my 40 gig partition in two (one is 37.41 GB and the other one is 1.65GB probably the swap.

---

### Post by deamon_knight on 2008-01-12
I'm building a new computer and thinking of doing this from the outset. I've got a couple complications.

I'm thinking of assembling a RAID 5 array so I have one Big Disk with Redundancy. Then I'll partition that into 4 sections, 1 NTFS for vista, 1 NTFS for XP, one Extended Partition that will have the Linux EXT3 parttion as well as swap partition, and finally a last partition to install software on so all O/Ss can access it.

Yea, I know, I'm nuts. 

Anyone with any advice on pitsfall to avoid? Install Ubunu last and have grub tak over booting, correct? Any problems with Ubuntu and RAID arrays?

---

