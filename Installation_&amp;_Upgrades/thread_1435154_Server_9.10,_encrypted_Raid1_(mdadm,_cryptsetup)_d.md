---
title: "Server 9.10, encrypted Raid1 (mdadm, cryptsetup) degraded after reboot"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by hrusu on 2010-03-21
hi everybody,

as you will notice I am quite new to working/setting up ubuntu. I yesterday created an encrypted raid 1 device, which worked fine until restart. My system consists of: EPIA V700, sys on compact flash, 2x WD 2TB hard disks, Ubuntu Server 9.10. Here's what happened so far
```

cfdisk                  #create full size primariy partitions on sda and sdb
mdadm -- create /dev/md0 --level ....... /dev/sda1 /dev/sdb1
cryptsetup luksFormat /dev/md0
cryptsetup luksOpen /dev/md0 storage
mkfs.ext4 ....

```
Everything was fine - appeared to be at least - according to "mdadm --detail". I put some files on it, reading and writing was nice and fast. After reboot, /prov/mdstat stated that the presence of two arrays with names "/dev/md_d0" und "/dev/md_d127". md_d0 was inactive with sda1 only sda1, md_d127 was active with sdb1 only, and thus raid 1 degraded.

First Question: why did my naming md0 not carry over to the new start?

After some hassle I deleted /dev/md_d0, repartitioned /dev/sda and restored the raid /md_d127 by adding sda1 back to it. This obviously took some hours. This morning, everything seemed fine again: I could decrypt and mount, the files where there, mdadm --detail showed nice stats and so did /proc/mdstat.
Alright, after reboot I got the following:
```

# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d127 : inactive sdb1[1](S)
      1953511936 blocks
       
unused devices: <none>

```
no mentioning sda at all!
"fdisk -l" on /dev/sda (and /dev/sdb, similarly) gives
```

# fdisk -l /dev/sda

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   fd  Linux raid autodetect

```
I then did the following:
```

# mdadm --detail /dev/md_d127
mdadm: md device /dev/md_d127 does not appear to be active.
# mdadm --run /dev/md_d127
mdadm: started /dev/md_d127
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d127 : active raid1 sdb1[1]
      1953511936 blocks [2/1] [_U]
      
unused devices: <none>
# ./mount_raid.sh                      %<--- contains cryptsetup luksOpen and mount -a
Enter LUKS passphrase: 
key slot 0 unlocked.
Command successful.

```

I have the feeling that I am now back where I found myself yesterday: a decrypted, degraded raid1 consisting of only sdb1. Any ideas what goes wrong during reboot? (I don't want to restore every time I reboot the system :) )

Thanks in advance!

---

### Post by hrusu on 2010-03-21
Next step: a was recommended to check into /etc/mdadm/mdadm.conf whether the array is listed in there, thus my step was "mdadm --examine --scan >> /etc/mdadm/mdadm.conf"
After reboot, the array is now rebuilding itself. We shall see (in about 5hrs).

---

