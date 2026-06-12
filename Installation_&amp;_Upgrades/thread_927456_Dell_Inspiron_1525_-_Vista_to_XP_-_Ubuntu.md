---
title: "Dell Inspiron 1525 - Vista to XP - Ubuntu"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by pizzipie on 2008-09-23
Boy, I'm so upset I'm about to split a gut!!!

My goal is to get rid of Vista, Install XP, Install as Dual boot - Ubuntu Hardy 8.04.1.

I just exchanged an Acer computer because of similar problems because I knew Dell supports linux. Acer must be owned by Microsoft. 

The new computer is Dell Inspiron 1525 w/Vista. June 2008.

Well I re-partioned the hard drive using SystemRescueCd into one 250 G partition w/NTFS.

When I tried to install XP  got this message "Setup did not find any hard disk drives installed in your computer"

I called Dell, did diognostics; all ok; Referred to Software people; they said they did not support XP, dual booting. GO SEE YOUR TECH!!! 

Well, there is no TECH where I live, or anywhere close. SO ...
 I thought I would try to partition using a fat32 partition with the following results;
 
Try to delete existing partion-got following
 
FDISK -l
reports -/dev/sda1 250 GB xx...xx Bytes 101 heads, 32 sectors per track, 151112 cylinders, units=cylinders of 3232*512 = 1,654,784 bytes;
Device-/dev/sda1, Boot   ;    Start 1; End 152; Blocks 244140+, ID 7, System HPFS/NTFS 

CFDISK
reports /dev/hda
size 191,901,696 bytes, 191 MB
Heads 255, Sectors per Track 63, cylinders 23
Name    ; Flags    ; Part Type primary/log; FS Type Free Space; Label    ; Size(MB) 189.19

PARTIMAGE - Says Partition to Restore Sda1 Unknown file system 238.42 MiB

Well I'm now totally over my head!!! Have I ruined the hard drive (yes there seems to be one) I just am at a total loss as to what to do next. The only other thing that I know may be to re-install Dell's Vist disk. (If that will even work now).

Please help!! 

Thanks in advance,

Rick P.

---

### Post by sonofusion82 on 2008-09-23
aha, the pain of installing XP into new machines.
i have a similar experience when installing win2k into a new machine
try google on "slipstream xp with sata driver"

---

