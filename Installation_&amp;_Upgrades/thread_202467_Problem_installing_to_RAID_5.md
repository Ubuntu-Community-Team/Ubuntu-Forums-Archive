---
title: "Problem installing to RAID 5"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by xplatform on 2006-06-23
I ran into a somewhat odd (and persistent) problem attempting to install dapper drake to a RAID volume ](*,). I am using the alternate install CD for RAID and LVM partitioning support, and have 4 ATA drives in the system. During partitioning, I defined the following partition configuration:

/dev/hda 200MB /boot
/dev/hda 317GB RAID

/dev/hdb 200MB swap
/dev/hdb 317GB RAID

/dev/hdc 200MB swap
/dev/hdc 317GB RAID

/dev/hdd 200MB swap
/dev/hdd 317GB RAID

with the intention to set up two volumes on the raidset, one for / and one for /data. When I attempt to commit this to disk (so I can start LVM) I get the following error:
[INDENT]
"error informing the kernel about modification to partition /dev/md/0p1 -- Invalid argument. This means Linux won't know about any changes you made to /dev/md/0p1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting." [/INDENT]

with a Ignore or cancel options. Ignoring the error allows the installation to continue, but fail. cancelling/rebooting loses all partition changes. I consider myself able enough to google, but I struck out; either I have a hardware problem, I'm the only idiot who has this problem, or this configuration is not supposed to work/not supported- thoughts?

---

