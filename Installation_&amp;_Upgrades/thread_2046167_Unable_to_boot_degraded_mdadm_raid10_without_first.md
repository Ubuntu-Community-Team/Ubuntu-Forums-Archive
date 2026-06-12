---
title: "Unable to boot degraded mdadm raid10 without first device"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by ikcalb on 2012-08-22
Hello!

I'm running
> "Debian squeeze 6.0.5" (stable)
> Linux server 2.6.32-5-amd64
on my Fujitsu ESPRIMO P5915 homeserver.


I do have almost the same problem as the threadstarter in:
[[SOLVED] RAID 1 boot with degraded works with 1 HHD not the other (grub-install already run)]("http://ubuntuforums.org/showthread.php?t=1983795&page=2") 



  
     **mount point**   |       device-node (comments) 
   
  
     **/ **     on /dev/md0  (raid10f2) 
     **swap**      /dev/md5  (raid10f2 - thaught of changing to non-raid) 
     **/home**      on /dev/md6  (raid10f2)
     **/backup**       on /dev/md3  (raid10f2, mounted --noauto, just when executing backups) 

My machine is able to boot from (chosen via bios boot-menu)
- any hd (if both are present)
- sda, degraded

But NOT bootable from sdb degraded.


The solution of @rubylaser, as well as everything else didn't work for me.
Any suggestion welcom!

Best regards, Florian

P.S.: partition layouts are identical, mdstat & fstab fully configured:

/etc/mtab (when running:  **update-initramfs -k all -u**)
```
/dev/md0 / ext4 rw,noatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
/dev/md2 /home ext4 rw,noatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0

```/etc/fstab:
```
root@server:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                            <mount point>   <type>  <options>                  <dump>  <pass>
proc                                        /proc           proc    defaults                    0       0
# /dev/md0                                  /               ext4    noatime,errors=remount-ro   0       1
UUID=12f0eaad-de67-49d0-a6da-8ed3be42bfe4   /               ext4    noatime,errors=remount-ro   0       1
# /dev/md1                                   none           swap    sw                          0       0
UUID=a90cbcd0-82ff-4172-a623-b8498f21d42c    none           swap    sw                          0       0
# /dev/md2                                  /home           ext4    noatime                     0       2
UUID=4c97a56e-8e78-403d-b07d-1204c4d48260   /home           ext4    noatime                     0       2
# /dev/md3                                  /backup         ext4    noatime                     0       2
UUID=9a5bc3c1-9e1a-4835-b49a-5a22340396c7   /backup         ext4    noatime,noauto              0       2
## FLOPPY ##
/dev/fd0                                    /media/floppy0  auto    rw,user,noauto              0       0
### Not Connected ###
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto                                         0       0


```FDisk:
```

root@server:~# fdisk -l /dev/sda /dev/sdb

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bcc86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   fd  Linux raid autodetect
/dev/sda2            1216        4508    26443599    5  Extended
/dev/sda3            4509        9730    41939968   fd  Linux raid autodetect
/dev/sda5            1216        1563     2783232   fd  Linux raid autodetect
/dev/sda6            1563        4508    23658496   fd  Linux raid autodetect



Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dda9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9764864   fd  Linux raid autodetect
/dev/sdb2            1216        4508    26443599    5  Extended
/dev/sdb3            4509        9730    41939968   fd  Linux raid autodetect
/dev/sdb5            1216        1563     2783232   fd  Linux raid autodetect
/dev/sdb6            1563        4508    23658496   fd  Linux raid autodetect

```/etc/mdadm/mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=587b4c02:46132727:34b62a64:e230a3d8 name=server:0
ARRAY /dev/md/1 metadata=1.2 UUID=a27df475:c9f21d6e:8a1eda7f:519bce5c name=server:1
ARRAY /dev/md/2 metadata=1.2 UUID=63120152:4c2be3d1:6d76972c:560585e5 name=server:2 
ARRAY /dev/md/3 metadata=1.2 UUID=bad9620c:33958c8f:f45918df:a7a6f70b name=server:3
```P.P.S.: Excuse my English

---

