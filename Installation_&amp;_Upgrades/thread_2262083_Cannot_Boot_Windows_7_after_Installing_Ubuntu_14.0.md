---
title: "Cannot Boot Windows 7 after Installing Ubuntu 14.04"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by alperen_elci on 2015-01-22
I recently installed Ubuntu 14.04 and may have inappropriately partitioned the hard drive. After the installation, Windows 7 does not boot. The Windows (on /dev/sda2) seems to be mounted as a device in /media/username/.

I ran Boot Repair to no avail. The log: [http://paste.ubuntu.com/9826877/](http://paste.ubuntu.com/9826877/)
On "Boot Repar --> Advanced Options --> GRUB location", there is the option to choose "Windows (via sda3 menu)" as the default OS to boot, but selecting and applying this option seems to change nothing after.

Are there any means to restore the Windows in Grub?

---

### Post by fantab on 2015-01-22
```

parted -l:

Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
[COLOR=#8b4513]1      1049kB  106MB  105MB   primary[/COLOR]
2      106MB   190GB  190GB   primary  ntfs         boot
3      190GB   240GB  50.0GB  primary  ext4
```

The issue is not with Grub.
The issue appears to be with the location and encryption of swap partition. 
Did you format the partitions yourself?
If Windows was installed first then it must have been the 1st partition on the HDD and if location was moved since installation then Windows will have problems booting.

Why did you encrypt the Swap partition? Its not needed. 

What you can try is:
1. Try [fix MBR]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") in Windows. You will have to [re-install grub]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") after this process, (you can also use Boot-repair). And hope Windows boots. If not, 
2. Delete the first encrypted swap partition using [gparted]("http://www.dedoimedo.com/computers/gparted.html") from the Live Ubuntu DVD/USB. Merge the unallocated space with Windows partition.
(Recollect how the partition layout for the first partition was before it was changed). 
Exit.

Retry Step 1.  

If Windows still cant boot then consult the Windows7 related forums or Reinstall Windows. You can backup your Windows related data from Live Ubuntu.

If the Issue is fixed then from Live Ubuntu- Gparted create yourself a 2-4gb swap after Ubuntu partition by resizing it.
Boot Ubuntu from HDD, now edit the /etc/fstab file to delete the 'brown' line, to remove the '**#**' from the 'green' line and replace the SWAP UUID string with the latest UUID.
```

sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=de538408-8eec-4dd3-a473-b4f366ba98c1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
[COLOR=#b22222]**#**[/COLOR]UUID=[COLOR=#006400]d8026dc8-423e-4d7b-b71c-5d844d51dfd7[/COLOR] none            swap    sw              0       0[COLOR=#8b4513]
/dev/mapper/cryptswap1 none swap sw 0 0[/COLOR]

```
The present UUID of a partition can found out using:
```
sudo blkid
```
...copy/note the UUID of Swap. 

To edit the /etc/fstab file:
```
sudo gedit /etc/fstab
```
...edit and save the file. Restart Ubuntu. Swap will be loaded on boot.
Good Luck

---

### Post by alperen_elci on 2015-01-23
Solved by deleting and merging swap partition using GParted then running the Windows Repair Disc. Had to fix through command prompt by following the tutorial: [https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/).

---

