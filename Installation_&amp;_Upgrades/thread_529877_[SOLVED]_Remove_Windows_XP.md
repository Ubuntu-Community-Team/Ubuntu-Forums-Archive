---
title: "[SOLVED] Remove Windows XP"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by mickc1303 on 2007-08-19
Hi All.

I have been using Ubuntu on and off for several years and for the last week have been using Fiesty.  It does everything I want so I have decided to totally switch over to it.

My current setup is as follows.

/dev/hda1: TYPE="ntfs" (Win Xp Boot)
/dev/hda5: TYPE="ntfs" (Storage Partition)
/dev/hdc1: TYPE="ntfs" (Extra Storage Partition)
/dev/hdc2: UUID="5dd1ef6c-89ca-4fd7-b7ff-4a4e6a85d1ee" TYPE="swap" 
/dev/hdc3: UUID="2e05b05a-c379-4d75-a444-0c2c709f9d51" SEC_TYPE="ext2" TYPE="ext3" (Ubuntu Partition)

I basically want to format the win xp partition and use it for the main ubuntu system then replace the current ubuntu partition with /home

I have spent a long time tweaking the system and don't want to set it up all again so is there any easy way to accomplish this or would it be easier to remove win xp and use that partition as /home

EDIT:  I managed to copy my /home partition over to hda1, running fine with no problems

---

