---
title: "software raid 5 after reinstallation"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by yanaek on 2010-12-09
I found similar topic, but it's not the same case: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1410563](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1410563), so..

I have:
[LIST]
[*]operating system installed on SSD drive (Kubuntu 10.10 amd64 on OCZ Vertex 64GB).
[*]software raid made of 6 normal hard disks (1TB each)
[/LIST]

I want to reinstall Ubuntu on SSD without loosing data from my software raid.

What will happen when i do this? Will new Ubuntu recognise all partitions that were made on hard disks? Or maybe i have to back up /etc/mdadm/mdadm.conf from my current installation and then, on new Ubuntu install mdadm and copy mdadm.conf there?

I have a lot of data on this  software raid 5 
```

$ sudo vgdisplay 
  --- Volume group ---
  VG Name               Storage
  System ID             
  Format                lvm2
...
  VG Size               4.55 TiB

```
it would be nice to not loose it without backup.

mdadm.conf 
```

DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=6 UUID=973ba49b:89a35e81:9615a9b1:92f14bda

```

So. any risks? I'd like to do the reinstallation because one year ago i installed Ubuntu 9.10 on this SSD and its partitions are not aligned well. Also i upgraded it from 9.10, through 10.04 to 10.10 and could be messy. I want clean new install of 10.10

---

### Post by SaturnusDJ on 2010-12-11
This should work.
How about trying it out by booting from Live CD and then mounting the RAID setup and LVM?

---

### Post by yanaek on 2010-12-13
perfect!, thanks for the hint

it works flawlessly

from live usb:

fdisk -l  # to check which disks are raid

$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdg1 /dev/sdh1

then it is possible to mount all raid/lvm partitions, great!

---

