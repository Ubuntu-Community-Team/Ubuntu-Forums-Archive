---
title: "Mounting &quot;choice&quot;"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by cyclister on 2005-10-20
I want to know how to get a prefect partitioning tabell their is.
When I mount the diffrent partitions in the installation part I can choose some choice for example usr (something) what should I choose for home?
Swap I cant choose so their isent a problem
But for root I should choose something?
This I think is a big thing to not have trobules later on with the system. my system works but with some hick ups that is really half sad, not so I cant surf.But when I try the high receptories I get some false message error in ba ba ba, then when I trying the compilation part I get some fales message, but now it's works better.But not as it should

---

### Post by hajk on 2005-10-20
Well, there isn't a single solution that is best for everyone. The standard Breezy setup installs to one big partition (probably OK for a single home user). A site with multiple users may also want to make separate partitions to mount /usr, /var, and /home on.

My own (recommended) partitioning for home use is to have a small (50 MB) bootable partition with an ext2 file system with mount point /boot; and a large
partition with a Reiser filesystem with mount point root (/). I also kept Windows XP on my Dell computer, so the total partition table looks like

Primary partitions:
/dev/hda1  -- Hidden Dell partition, no mount point
/dev/had2  -- Bootable NTFS partition (/media/windows) 19GB
/dev/hda3  -- Bootable ext2 (Linux) partition (/boot) 50MB   

Logical partitions:
/dev/hda5  -- Linux swap 512MB
/dev/hda6  -- reiserfs (Linux) partition (/) 20GB

This is my perfect table... I made the free space for Linux with PartitionMagic.

---

