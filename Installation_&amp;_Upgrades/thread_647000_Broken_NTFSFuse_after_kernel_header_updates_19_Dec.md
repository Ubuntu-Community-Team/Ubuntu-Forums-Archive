---
title: "Broken NTFS/Fuse after kernel header updates 19 Dec 07"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by zyg0t3 on 2007-12-21
Access to my NTFS partitions suddenly stopped after running the updater for the kernel headers. After reboot no access to drives. They are there but i cannot access them. Also on a subsequent reboot lost all modules (sound/network/mouse,etc). Did a "sudo depmod" and got them back but still no NTFS access. I think it's a problem with the fuse module but am not sure how to continue to troubleshoot.

---

### Post by zyg0t3 on 2007-12-22
So i dl'd and compiled/installed both the latest fuse and the latest ntfs-3g binaries and same thing/no change. I notice that i get a failed message on boot for filesystems.

Also i used synaptic to downgrade the headers back to the previous and no change.
When i run sudo ntfs-config, under the advanced tab it shows the devices with the mount points and total amount of memory but shows 0 for used which is wrong. and the writable box is checked for both.

When i try to access the drive (that appear in nautilus) with my normal user account it says
```

Cannot mount volume.
You are not privileged to mount 

```
if i sudo a nautilus instance it does not display the drives in the left panel or under the /media folder

but if i log in as root it does display them and it give me the error.
```

Cannot mount volume.
Unable to mount the volume 'myvolume'

under details it says

fuse: failed to access mountpoint /media/myvolume: No such file or directory.

```

dmesg
```

[    5.040000] Probing IDE interface ide0...
[    5.060000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.060000] sd 0:0:0:0: [sda] Write Protect is off
[    5.060000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.060000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.060000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.060000] sd 0:0:0:0: [sda] Write Protect is off
[    5.060000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.060000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.060000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    5.124000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.128000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.464000] Attempting manual resume
[    5.464000] swsusp: Resume From Partition 8:5
[    5.464000] PM: Checking swsusp image.
[    5.464000] PM: Resume from disk failed.

```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ec18ed93-d714-4052-9ae8-1952e506b548 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c4b367e9-ba53-403e-9eb0-1664fe7ca38a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
#ntfs-3g mount
/dev/sda2       /media/ACER     ntfs-3g   silent,umask=0,locale=en_US.utf8 0 0
/dev/sda3       /media/DATA     ntfs-3g   silent,umask=0,locale=en_US.utf8 0 0

```

/var/log/kern.log
```

Dec 22 13:24:00 zyg-laptop kernel: [    5.040000] Probing IDE interface ide0...
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 13:24:00 zyg-laptop kernel: [    5.060000]  sda: sda1 sda2 sda3 sda4 < sda5 >
Dec 22 13:24:00 zyg-laptop kernel: [    5.124000] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 22 13:24:00 zyg-laptop kernel: [    5.128000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 22 13:24:00 zyg-laptop kernel: [    5.464000] Attempting manual resume
Dec 22 13:24:00 zyg-laptop kernel: [    5.464000] swsusp: Resume From Partition 8:5
Dec 22 13:24:00 zyg-laptop kernel: [    5.464000] PM: Checking swsusp image.
Dec 22 13:24:00 zyg-laptop kernel: [    5.464000] PM: Resume from disk failed.

```
In syslog i found 2 seperate instances of fuse
```

Dec 22 13:24:00 zyg-laptop kernel: [    3.076000] fuse init (API version 7.8)
...
Dec 22 12:25:04 zyg-laptop kernel: [    3.088000] fuse init (API version 7.8)

```
mount -l
```

/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda on /media/cdrom0 type udf (ro,nosuid,nodev,user=zyg) [300]

```

sudo mount -a 
```

sudo mount -a
fuse: failed to access mountpoint /media/ACER: No such file or directory
fuse: failed to access mountpoint /media/DATA: No such file or directory

```
As i say it worked fine before the update.
Anyone help with this problem?? I'm stumped.
I need access to the files on the drive so i guess i'll be working in Vista because i dont have the time to reinstall ubuntu at the moment.

---

### Post by zyg0t3 on 2007-12-22
The fix was so simple as to be stupid.

sudo mkdir /media/myfolder

but as i never did that before i wonder what changed to make it thus. I am supposing that either fuse or ntfs-3g is not being run with root privileges when before it/they were. Oh well now on to the broken mic problem.

---

### Post by tomrob on 2008-01-17
Thanks! Helped me out aswell.

---

