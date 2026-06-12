---
title: "grub2: grub-install /dev/sdx is destroying the partition table"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-10-08
does anyone have this bug/know of a bug report? Installing grub2 to the mbr of any of my hard drives scrambles the partition table

$grub-install /dev/sdb

leaves
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       20682      154408  1074152739    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      172234      289654   943175203   be  Solaris boot
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      190072      309207   956950144    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1           1           0   4f  QNX4.x 3rd part
Partition 4 does not end on cylinder boundary.
```luckily testdisk restores the partition table nicely to what it should be
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

```Note, the disk and partitions here are just to illustrate, it does the same on all disks/partitions no matter what size or type

---

### Post by VMC on 2009-10-08
Did this just start happening? How were you able to boot. 
This is the first I've heard about it. I wonder if your grub is defective somehow. Maybe a reinstall.

---

### Post by dinxter on 2009-10-08
I'm not sure when this started happening as i'm not sure when I last installed to the mbr. I think your right that something has corrupted as I have another karmic on another drive that works fine on install, this is why i haven't filed a bug yet. Sadly reinstalling grub2 or reverting to grub legacy doesnt fix it. as they both use the same grub-common i'm assuming something has gone wrong in there.
On the bright side, i didnt realise how terrific testdisk was!

---

### Post by kansasnoob on 2009-10-08
There have been instances of both legacy grub and grub2 being installed simultaneously after recent updates.

Go to Synaptic and click on Search (not quick or rebuilding search), then type grub. Make sure that not both "grub-pc' and 'grub' are installed.

If they are then you need to remove the one you weren't using.

It was a glitch, I suspect related in some way to interaction with startupmanager.

That is, if we're on the same page.

Apologies if I'm wrong.

If you need to know which version of grub is actually "installed" run the command:

```
grub-install -v
```

---

### Post by kansasnoob on 2009-10-08
Also, in unison with the dual grub debacle, it seemed like / was totally overloaded, so you might want to post the output of:

```
df -H
```

---

### Post by dinxter on 2009-10-08
grub/grub-pc are not both installed at the same time, grub-pc version
grub-pc/karmic uptodate 1.97~beta3-1ubuntu8
Neither are there multiple mounts on /,
```
$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb1               78G   5.4G    69G   8% /
udev                   4.2G   324k   4.2G   1% /dev
none                   4.2G   1.3M   4.2G   1% /dev/shm
none                   4.2G   123k   4.2G   1% /var/run
none                   4.2G      0   4.2G   0% /var/lock
none                   4.2G      0   4.2G   0% /lib/init/rw
/dev/sdc1              158G    49G   101G  33% /media/store160
/dev/sda1              501G   488G    13G  98% /media/store500

```

I get some odd errors on a clean grub-pc install, the entire grub directory cleaned out beforehand
```
Setting up grub-pc (1.97~beta3-1ubuntu8) ...

Creating config file /etc/default/grub with new version
stat: cannot read file system information for `%d': No such file or directory
stat: cannot read file system information for `%d': No such file or directory
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-12-generic
stat: cannot read file system information for `%d': No such file or directory
stat: cannot read file system information for `%d': No such file or directory
Found initrd image: /boot/initrd.img-2.6.31-12-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-11-generic
stat: cannot read file system information for `%d': No such file or directory
stat: cannot read file system information for `%d': No such file or directory
Found initrd image: /boot/initrd.img-2.6.31-11-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

```

Note, the error 'Cannot find a GRUB drive for /dev/sdb1.  Check your device.map' is due to the fact that by this point in the install the partition table on sdb is garbled

---

