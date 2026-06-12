---
title: "RAID Issues"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by gsoft on 2007-09-10
I am having some issues in the installation with RAID 1. On my first attempt I forgot to setup the Root filesystem. (My setup was RAID 1, RAID 5). And got the error about the / missing. I rebooted the system. And my configuration stayed the same so setup the root this time and tried to install the system. Got errors whilst installing the software and couldnt setup grub or LILO (not too good), so rebooted the system and tried to start back from the beginning however I cannot remove my RAID 1 system.

I setup 2 spares and 4 active devices. I can remove all 5 except 1. Which I get the device or resource busy error when running ```
mdadm /dev/md0 --remove /dev/sda1
``` Ive tried doing ```
mdadm  /dev/md0 --zero-superblock /dev/sda1
``` (Not sure if this is totally correct), however get the cannot write to device no zeroing.

How can I remove it, the RAID only becomes active when I go to Configure RAID and finish (As I cannot setup another RAID Device) ?

Another issue is each time gone to the partition setup the partitions do not seem to be removed as they are all setup as RAID K which is why I go to Configure RAID. This is quite fustrating, as I am not sure what else I can do.

Some other points to note are there is no raidtool or mdadm.conf files in /etc

Ive googled and searched here but none have had a similar situation (at least that I can determine) and no one that comes close has ever noted exactly what they did.

---

### Post by gsoft on 2007-09-11
Anyone ? [bump]

---

### Post by gsoft on 2007-09-15
I seemed to fix the issue with the RAID, however afterwards I have now noticed that when re-doing the partitioning that the SCSI labels are similar previously it was

SCSCI 1 (0,0,0) to 6

Now it is:

SCSI 1 (0,0,0)
SCSI 1 (0,1,0)
SCSI 2 (0,0,0)
SCSI 2 (0,1,0)
SCSI 3 (0,0,0)
SCSI 4 (0,0,0)

Should I be concerned about this ?

---

### Post by Pumalite on 2007-09-15
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

