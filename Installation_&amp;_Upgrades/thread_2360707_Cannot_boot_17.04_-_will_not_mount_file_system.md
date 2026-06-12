---
title: "Cannot boot 17.04 - will not mount file system"
date: 2017-05-07
forum: Installation &amp; Upgrades
---

### Post by doctordruidphd on 2017-05-07
Sorry if this duplicates an existing issue, but I cannot locate the same problem, or a solution. No help from the kubuntu forum.

I cannot boot into 17.04 (the problem also existed with 16.10, but that is gone from my system); the LTS (16.04, I think) works file. It hangs while trying to mount the file systems, times out, and drops to recovery shell. The shell shows sda1 mounted as ro, no other /dev file systems mounted. If I try to do a mount command, it appears to execute without errors, but it doesn't actually mount anything. The interesting thing is that it will boot, but takes about 10 tries before it completes successfully.

I have searched for this, and it seems to be a common problem with 4.8 and 4.10 kernels, but I have found no solution that works.

NVIDIA drivers have been removed/purged, I am using nouveau.

booting with acpi=noirq did not work.

Has a solution to this been found?

Thanks for your assistance.

---

### Post by Bashing-om on 2017-05-07
doctordruidphd; Hey - a thought

```

sudo blkid -c /dev/null -o list

```
verify that the UUIDs in the files /etc/fstab and /boot/grub/grub.cfg all agree, and that the system is not attempting to mount something that is currently not available to mount.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-07
Thanks for your reply.  Yes, I have checked that, and it looks like the uuid's in grub.cfg are OK.

---

### Post by Bashing-om on 2017-05-07
doctordruidphd; Huumm ...

file system consistent ?
[https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html](https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html)

[INDENT][INDENT]tough to make a call
[/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-07
Yes, file systems are OK. As noted above, 16.04 boots fine. Have also run e2fsck on the systems individually, they are OK.

---

### Post by Bashing-om on 2017-05-08
doctordruidphd; Well,

Booting a liveDVD(USB) to a terminal.
What does the system see for the drive(s) ?
Post back:
```

sudo parted -l
sudo fdisk -lu

```
and we have a look at the problematic 17.04 install.

[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-08
Here is the info requested. Please do remember that they system boots 16.04 without any problems, so I suspect the problem is with something that changed from 16.04 -> 16.10 -> 17.04. File systems all check out as they should. The systems that won't boot (copies of each other) are on sda1 and sda2. 16.04 is on sda3, debian jessie (which also boots with no problems) is on sdb1.

Also, a couple of experiments that I tried: Booting with the "upstart" option does boot the system, with all file systems mounted, but not much else works. I tried installing the 4.4.0-??? kernel from 16.04, and booting with that has the same problem -- hanging while trying to mount the file systems. I don't know how well the 4.4 install worked, as there are probably unmet dependencies.

> 
greenman@Crynfyd17.04 ~$ sudo fdisk -lu
[sudo] password for greenman: 

Disk /dev/sda: 1000 GB, 1000202273280 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953520065 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1            2048   204802047   102406311   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sda2   *   204802048   409602047   102398310   83  Linux
Warning: Partition 2 does not end on cylinder boundary.
/dev/sda3       409602048   614402047   102398310   83  Linux
Warning: Partition 3 does not end on cylinder boundary.
/dev/sda4       614404094  1953523711   669565102    5  Extended
Warning: Partition 4 does not end on cylinder boundary.
/dev/sda5       614404096   679940095    32772600   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda6       679942144  1953523711   636792502   83  Linux
Warning: Partition 6 does not end on cylinder boundary.

Disk /dev/sdb: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976768065 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1            2048   133122047    66565296   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sdb2       133122048   952322047   409601272   83  Linux
Warning: Partition 2 does not end on cylinder boundary.
/dev/sdb3       952322048   976773119    12225465   82  Linux swap
Warning: Partition 3 does not end on cylinder boundary.

greenman@Crynfyd17.04 ~$ sudo parted -l
Model: ATA ST31000333AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  105GB   105GB   primary   ext4
 2      105GB   210GB   105GB   primary   ext4            boot
 3      210GB   315GB   105GB   primary   ext4
 4      315GB   1000GB  686GB   extended
 5      315GB   348GB   33.6GB  logical   linux-swap(v1)
 6      348GB   1000GB  652GB   logical   ext4


Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  68.2GB  68.2GB  primary  ext4
 2      68.2GB  488GB   419GB   primary  ext4
 3      488GB   500GB   12.5GB  primary  linux-swap(v1)




---

### Post by Bashing-om on 2017-05-08
doctordruidphd; Welp. 

The numbers do not add up !

we have "  total 1953520065 sectors " on sda
then: In the extended partition " 1953523711  " which is outside the bounds of the device, no ?
and in this badly formatted extended partition is the swap partition.

I can accept that this swap partition is shared for sda1/sda2 and maybe hammered up ?? such that when booting the system pukes trying to mount swap ? ( sda6 is also outside the device sector allotment . )

[INDENT][INDENT]hey. it's a thought
[/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-08
Thanks for your suggestions. Just to see what would happen, I commented the swap partitions out of fstab, but still no boot. Hard for me to see the problem is with the file systems, as jessie and 16.04 both boot fine, but I suppose anything is possible. From searching I have noticed that others have the same problem with 4.8 and 4.10 kernel systems, but I have yet to find any specific problem identified, or solution reached. I suspect that something changed in the way file systems are mounted from 16.04 to 16.10 and 17.04.

---

### Post by Bashing-om on 2017-05-08
doctordruidphd; Well.

'nother thought.
```

sudo blkid -c /dev/null

```
As we do not want duplicated UUIDs .

Still, need to fix those partitions .

[INDENT][INDENT]maybe this
[INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-08
There are no duplicate uuid's, and the uuid's from blkid correspond to the ones in fstab.  This does not seem to be the right direction, as if there were problems in the file systems, the other os's would also not boot. 

One thing that might be an issue, though, is if the options required in fstab have changed. Would you, if possible, post at least the lines from a working fstab that show the root file system and some other system (other than swap)? 
Example from my fstab:

---

### Post by Bashing-om on 2017-05-08
doctordruidphd; hummm ..

mine, though may not help ya much as I single boot on this multi-boot system . Presently booting an SSD.
```

sysop@x1604:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="x1604" UUID="d9c2a8e6-d014-42a6-846f-7e7892f4aef5" TYPE="ext4" PARTUUID="b6a9f0ca-01"
/dev/sda5: UUID="8d4743bc-8e47-4650-b5fd-1ea904d4ecda" TYPE="swap" PARTUUID="b6a9f0ca-05"
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" PARTUUID="0002ea65-01"
/dev/sdb2: LABEL="ubie1704" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" PARTUUID="0002ea65-02"
/dev/sdb3: LABEL="ubie1604" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" PARTUUID="0002ea65-03"
/dev/sdb5: LABEL="bups" UUID="bb6b5229-649a-4486-93e4-38a57844e9f2" TYPE="ext4" PARTUUID="0002ea65-05"
/dev/sdb6: LABEL="stuff" UUID="b8ea7b16-9bb4-43ec-85f7-711706723391" TYPE="ext4" PARTUUID="0002ea65-06"
/dev/sdb7: LABEL="swap" UUID="98c2d0d6-4425-4aea-9ef2-d952fb0ba3d4" TYPE="swap" PARTUUID="0002ea65-07"
sysop@x1604:~$ 

```
where I mount my data partitions on-demand ( no fstab entry )
with 2 other drives not presently plugged in
```

sysop@x1604:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d9c2a8e6-d014-42a6-846f-7e7892f4aef5 /               ext4    noatime,errors=remount-ro 0       1
#The noatime option fully disables writing file access times to the drive every
#time you read a file. This works well for almost all applications, except for
#those that need to know if a file has been read since the last time it was 
#modified. The write time information to a file will continue to be updated
#anytime the file is written to with this option enabled.
#
##relatime updates the access time only if the previous access time was earlier
#than the current modify or change time. In addition, since Linux 2.6.30,
#the access time is always updated if the previous access time was more than
#24 hours old. This option is used when the defaults option, atime option
#(which means to use the kernel default, which is relatime .
#
# swap was on /dev/sda5 during installation 18oct2016 extended/swap partition was changed
UUID=8d4743bc-8e47-4650-b5fd-1ea904d4ecda none            swap    sw              0       0

tmpfs /tmp tmpfs defaults,noatime,nodiratime,mode=1777 0 0
#
sysop@x1604:~$ 

```


[INDENT][INDENT]runn'n on empty
[/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-09
OK, I see nothing about my fstab that is essentially different from yours in terms of mount options, so that isn't where the problem is. Well what makes no sense at all is that sometimes I can boot 17.04 and sometimes I can't, without any changes to anything, but 16.04 always boots fine. As of this morning, neither 17.04 system will boot at all. I guess it's back to searching bug reports, which so far has just been a waste.

---

### Post by Bashing-om on 2017-05-09
doctordruidphd; Hummm ...

I can relate to you what I do - and it does happen (operator error ) - that I too have booting issues.
Boot to grub and start the OS manually from the grub prompt.
set "pager-1" and watch for errors .
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
You have to know where grub's config files are located for the respective system you want to boot ; and tell grub so .
If grub has a problem grub will scream and holler.
If the system boots then control is turned over to the kernel, and it is the log files one has to learn to read.

Great help to keep the mind straight is to label the partitions:
```

sudo tune2fs -L "ubie1-1604" /dev/sda1
sudo tune2fs -L "ubie2-1604-bad" /dev/sda2

```
Or some-such - for each partition - swap is already named .

[INDENT][INDENT]ain't no quit
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by doctordruidphd on 2017-05-09
This is really a work-around, and not a solution, but it does make booting possible.

[https://answers.launchpad.net/ubuntu/+question/631834](https://answers.launchpad.net/ubuntu/+question/631834)

---

### Post by Bashing-om on 2017-05-09
doctordruidphd; Good deal ...

But, over my head why it works when normal boot fails .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

