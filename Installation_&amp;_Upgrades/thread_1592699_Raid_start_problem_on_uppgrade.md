---
title: "Raid start problem on uppgrade"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by willenfort on 2010-10-10
Hi  this is my first post and I will try to be brief.

I just made a complete reinstall of my fileserver.   
After the installation the system cannot autostart my Raid1.  

For some reason it seams that only one of the identical disks are found by mdadm
"disk utility" states "not running, partially assembled"
If i immediately stop the raid in the disk utility I can restart it and mount it.

some diagnostics
mdadm.conf
> # by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 metadata=1.2 num-devices=2 devices=/dev/sdb1,/dev/sdc1 
#DEVICE /dev/sdb1 /dev/sdc1
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=01.02 name=:DATA_RAID UUID=e3286dc3:36928335:502778d2:7451a046sudo blkid
> [sudo] password for master: 
/dev/sda1: UUID="80dda925-bf56-4ded-ac4c-9e9153c8509e" TYPE="ext4" 
/dev/sda5: UUID="34075122-4b19-42c2-9d2a-9ce77ff84689" TYPE="swap" 
/dev/sdc1: UUID="e3286dc3-3692-8335-5027-78d27451a046" LABEL=":DATA_RAID" TYPE="linux_raid_member" 
/dev/sdb1: UUID="e3286dc3-3692-8335-5027-78d27451a046" LABEL=":DATA_RAID" TYPE="linux_raid_member" 
/dev/sdd1: UUID="d7ec47f5-e038-44ce-8204-f001063771b9" TYPE="ext4" 
/dev/sdd5: UUID="04735940-b591-4816-9cbe-fe8bea276ae2" TYPE="swap" 
/dev/sde1: LABEL="Ny volym" UUID="5AC089BCC0899F3F" TYPE="ntfs" cat /proc/mdstat (directly after start)
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[1](S)
      781409465 blocks super 1.2
       
md_d127 : inactive sdc1[0](S)
      781409465 blocks super 1.2
       
unused devices: <none>

cat /proc/mdstat (After stopping and starting in disk utility)
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc1[0] sdb1[1]
      781409465 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

---

### Post by willenfort on 2010-10-11
None that have any ideas ?   This is very frustrating and i really need help

---

