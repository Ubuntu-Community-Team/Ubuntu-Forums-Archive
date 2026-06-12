---
title: "RAID and LVM"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by srv on 2006-08-09
Hi

I'm trying to run a recovery test in case of a system crash. I have the following partition-layout:

sda1* 100 MB /boot
sda2 249 GB

sdb1 * 100 MB /boot
sdb2 249 GB

Configured as RAID-1 and with folloing LVM-groups and tables:

VolGroup00 (the 249 GB)
LogVol00 swap (512 MB)
LogVol01 / (15 GB)
LogVol02 /var (the rest)

Now, when I boot from the Ubuntu Dapper AMD-64 server cd and the partitioner starts up, I can't see the VolGroup or LogVol's. Only the to disks are shown. If I boot up from a Fedora CD, everything is shown.

How do I list the partitions so I can format / and reinstall ??

TIA

/SRV

---

### Post by mlind on 2006-08-09
> **srv said:**
> Hi

I'm trying to run a recovery test in case of a system crash. I have the following partition-layout:

sda1* 100 MB /boot
sda2 249 GB

sdb1 * 100 MB /boot
sdb2 249 GB

Configured as RAID-1 and with folloing LVM-groups and tables:

VolGroup00 (the 249 GB)
LogVol00 swap (512 MB)
LogVol01 / (15 GB)
LogVol02 /var (the rest)

Now, when I boot from the Ubuntu Dapper AMD-64 server cd and the partitioner starts up, I can't see the VolGroup or LogVol's. Only the to disks are shown. If I boot up from a Fedora CD, everything is shown.

How do I list the partitions so I can format / and reinstall ??

TIA

/SRV

Have you tried this using **Alternate install CD**? I believe that Desktop CD doesn't support LVM.

If you just want to destroy the partitions, use fdisk.

---

### Post by srv on 2006-08-09
I'm using ubuntu-6.06-server-amd64

---

### Post by mlind on 2006-08-09
> **srv said:**
> I'm using ubuntu-6.06-server-amd64

I'm not familiar with server install cd, but I suppose it's the same ncurses based installer interface?

There should be option to activate the LVM's, at least that's how alternate cd installer works.

---

### Post by srv on 2006-08-09
Yes, it's the same old interface. And you do have both LVM and RAID options in the partitioner, but no matter what I press, the LVM can't see any partitions.

---

### Post by mlind on 2006-08-09
> **srv said:**
> Yes, it's the same old interface. And you do have both LVM and RAID options in the partitioner, but no matter what I press, the LVM can't see any partitions.

I don't remember how the partitioner interface looks like, but there should be option at the top of that screen (probably second one?) which is something about activating LVM's. I'll check if I can find tutorial that includes screens somewhere.

---

