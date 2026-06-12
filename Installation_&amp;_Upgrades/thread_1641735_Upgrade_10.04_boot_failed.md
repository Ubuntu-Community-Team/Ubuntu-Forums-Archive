---
title: "Upgrade 10.04 boot failed"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by JVJB on 2010-12-09
I just got back from being away from my desktop for a few months and decided to upgrade to 10.04 from the gui. After the update was done I rebooted and got stuck at the "Starting Up" message. Tried Recovery mode and got an error, I typed it out below. I'm downloading the liveCD now to boot off of it, but I still don't know how to mount the drives. I do know that I have two HDD's in software raid using madam? or something, can't remember it was a while ago i set it up. Any help appreciate. thanks



Error: 
6.892513 Slow work thread pool: Ready
6.893035 CIFS: unknown mount option umask
6.912554 CIFS VFS: Error connecting to socket. Aborting operation
6.912632 CIFS VFS: cifs_mount failed w/return code = -101



update: Downloaded the liveCD and booted off it and ran the bootinfoscript I found referred to in the forum, but I can't see my drive, nautalis shows it as an Array but won't mount it.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   152,296,199   152,296,137  fd Linux raid autodetect
/dev/sda2         152,296,200   156,296,384     4,000,185  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   152,296,199   152,296,137  fd Linux raid autodetect
/dev/sdb2         152,296,200   156,296,384     4,000,185  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        11d8d5e1-b1b0-4f47-4e52-158d2518e6c8   linux_raid_member                               
/dev/sda2        e51cd4b1-4f60-79d4-2f94-ab831eef8549   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        11d8d5e1-b1b0-4f47-4e52-158d2518e6c8   linux_raid_member                               
/dev/sdb2        e51cd4b1-4f60-79d4-2f94-ab831eef8549   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

