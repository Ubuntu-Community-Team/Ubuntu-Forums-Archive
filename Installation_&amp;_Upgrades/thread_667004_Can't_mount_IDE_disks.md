---
title: "Can't mount IDE disks"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by Kablooie!! on 2008-01-13
Hi all,

This is a strange one (to me, anyway).

I did a fresh install of the latest Ubuntu on my machine.  It's a dual 1.7GHz Xeon Compaq EVO  machine with 1G of RAM.  The boot/OS disk is an old 40G drive.  

I have a 320G IDE drive installed (had it in previous Linux install on this machine - no hardware has changed).  It worked fine.  

After successfully installing the latest Ubuntu, I made a mount point for the disk and mounted it via this entry in /etc/fstab:

```
/dev/sdb1      /video          xfs     rw,user,noauto,exec 0   1

```
Initially mounted it manually with:

```
mount /video
```

Worked fine.  I verified that it was there and that I could access the data. 

Then I rebooted the machine and found that I couldn't access the disk any more!

It wasn't mounted, and when I tried to mount it, I got:

```
root@mythbox:~# mount /video
mount: /dev/sdb1 already mounted or /video busy
root@mythbox:~# df -k /video
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   4000088  30971552  12% /
root@mythbox:~# fuser /video
root@mythbox:~# df -k|grep sdb
root@mythbox:~# umount /video
umount: /video: not mounted
```

I tried moving the mount point aside and using a different mount, no joy.  I tried manually mounting it with:

```
root@mythbox:~# mount -t xfs /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
```


I was able to run xfs_check and xfs_repair on /dev/sdb fine.  I did a 

```
dd if=/dev/sdb1 of=/tmp/foo bs=8132
```

waited a bit, hit Control C, and then "file /tmp/foo" and it said it was an XFS filesystem, as expected.

... strange...

I had been meaning to install the second 320G IDE drive, so this seemed like a good time to do it.

I popped the drive in, partitioned it as one big primary partition, set the partition type to Linux, and created an ext3 filesystem on it.  Then I created a /video2 mount point and mounted the new disk just fine.  Verified that I could write to it, and added it to /etc/fstab as follows:

```
/dev/sdc1      /video2         ext3    rw,user,noauto,exec 0   1
```

The next time I rebooted, I couldn't access EITHER disk!  The bootup process failed partway through, indicating that /dev/sdb1 and /dev/sdc1 couldn't be checked by fsck because they were already mounted, or the mount point was busy.  It left me in administrative mode.  I commented out the fstab entries (after trying to mount them, fsck them, etc with the same failure), and booted up.

Does anyone have any idea what the heck is going on?  Is there perhaps some sort of hardware/BIOS thing that is preventing linux from mounting these things properly?

Here's some reference material that might be useful (sorry for making this post so long-winded but I wanted to try to pre-answer all the questions you might ask):

```
root@mythbox:~# fdisk -l /dev/sdb

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


root@mythbox:~# fdisk -l /dev/sdc

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x998b6635

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

root@mythbox:~# mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy

root@mythbox:~# df -k /mnt
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   4000088  30971552  12% /
root@mythbox:~# df |grep sdb
root@mythbox:~# mount /dev/sdc1 /mnt
mount: /dev/sdc1 already mounted or /mnt busy

root@mythbox:~# df |grep sdc

root@mythbox:~# dmesg |grep sdb
[   66.937580] sd 1:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   66.937604] sd 1:0:1:0: [sdb] Write Protect is off
[   66.937609] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   66.937644] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.937753] sd 1:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   66.937774] sd 1:0:1:0: [sdb] Write Protect is off
[   66.937778] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   66.937812] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.937817]  sdb: sdb1
[   66.957336] sd 1:0:1:0: [sdb] Attached SCSI disk
root@mythbox:~# dmesg |grep sdc
[   66.957468] sd 2:0:1:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   66.957493] sd 2:0:1:0: [sdc] Write Protect is off
[   66.957498] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   66.957533] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.957633] sd 2:0:1:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   66.957658] sd 2:0:1:0: [sdc] Write Protect is off
[   66.957663] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   66.957696] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.957703]  sdc: sdc1
[   66.975678] sd 2:0:1:0: [sdc] Attached SCSI disk
```


Any help or suggestions would be greatly appreciated!

Thanks,
Grant

---

### Post by Matt Yun on 2008-01-13
Instead of options *rw,user,noauto,exec* in your fstab, what happens when you use option *default*?

---

### Post by Kablooie!! on 2008-01-13
Tried it:

root@mythbox:~# grep sdb /etc/fstab
#/dev/sdb1      /video          xfs     rw,user,noauto,exec 0   1
/dev/sdb1       /video          xfs     defaults        0       1
root@mythbox:~# mount /video
mount: /dev/sdb1 already mounted or /video busy


No joy.  I tried both "default" and "defaults".

But doing a "mount -t xfs /dev/sdb1 /video" skips what's in /etc/fstab anyway.

Any other ideas?  ;-)

Thanks,
Grant

---

### Post by Kablooie!! on 2008-01-14
bump

---

### Post by Matt Yun on 2008-01-15
Hi, sorry, I forgot that since Feisty, Ubuntu identifies IDE and SATA hard drives by UUID.  Your fstab is the old-fashioned way of doing it, which is the first way I thought of it too.

See these threads:  [fstab UUIDs]("http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid"), [How do you find UUID]("http://ubuntuforums.org/showthread.php?t=349376"), [Adding a new partition in fstab with UUID]("http://ralph.n3rds.net/index.php?/archives/175-Adding-a-new-partition-in-fstab-with-UUID.html").

My suggestion:  easiest way to get your hard drive UUIDs is to install all your hard drives first, then boot your machine with the Gutsy LiveCD.  Copy the fstab generated by the LiveCD and save it to the etc directory on the hard drive partition that you intend to boot from.

Edit the LiveCD-generated fstab.  You will see that all of the hard drives are referred to by UUID, rather than by /dev/sd* file.  Edit the mount points as desired (eg.  /media/sdb1 -> /video).  Save the fstab and reboot without the LiveCD.

---

### Post by jeffus_il on 2008-01-15
Did you know that the file manager Nautilus will mount unmounted partitions that are not in the fstab, and will give you full access.

---

### Post by Kablooie!! on 2008-01-16
Cool!  Thanks!  I'll give it a try.

Seems like a lot of hoops to jump through to mount a hard drive, though.  ;-)

Thanks again,
Grant

---

### Post by Kablooie!! on 2008-01-19
Hi again,

I tried as you suggested:
- booted using the Live CD (it didn't auto-mount the disks, but I was able to mount them with "mount /dev/sdb1 /video; mount /dev/sdc1 /video2" just fine.
- ran the vol_id command on each and saved the results
- booted back into normal mode and updated my /etc/fstab by adding these lines:

UUID=27459191-fc1d-4054-b642-f2aa78677441 /video          xfs    defaults,errors=remount-ro 0       1
UUID=fd75a000-e3b3-45ba-b9e0-c80f1d210be4 /video2         ext3    defaults,errors=remount-ro 0       1

And now I try to mount:

root@mythbox:~# mount /video2
mount: /dev/sdc1 already mounted or /video2 busy
root@mythbox:~# mount /video
mount: /dev/sdb1 already mounted or /video busy


Argh!  Why would it be that I can mount them fine when I'm running the live CD but not when I boot normally?

Thanks for any help you can offer.

Grant

---

### Post by Kablooie!! on 2008-01-19
Aha!

I found this thread:   [http://ubuntuforums.org/showthread.php?t=5644](http://ubuntuforums.org/showthread.php?t=5644)

Which talks about the device mapper.  I've found that I can mount /dev/evms/sdb1 and /dev/evms/sdc1!

Woo-hoo!

Thanks all,
Grant

---

