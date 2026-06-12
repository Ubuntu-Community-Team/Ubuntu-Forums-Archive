---
title: "Install 10.04 to RAID drive with root on RAID0"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by HankB on 2011-03-21
I ran into this and found a non-trivial solution so I thought I'd share in case anyone else ran into it.

I have two 200GB drives so I thought I'd install my system with RAIDed partitions for /boot, / and /home. I would use RAID1 for /boot and /home because GRUB2 can load the kernel from a RAID1 and I thought the extra reliability for /home would be nice. (I may second guess /home on RAID1 once I get to test performance.) I chose RAID0 for / to provide faster application loading.

I prepared the drives using a Live CD because I'm not confident that I can do what needs to be done during installation.

First I partitioned the drives as:
```
hbarta@olive:~$ sudo fdisk -luc /dev/sda

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014d21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1992059      995998+  fd  Linux raid autodetect
/dev/sda2         1992121   390716864   194362372    5  Extended
/dev/sda5         1992123    21992984    10000431   fd  Linux raid autodetect
/dev/sda6        21993048    29993354     4000153+  82  Linux swap / Solaris
/dev/sda7        29993418   390716864   180361723+  fd  Linux raid autodetect
``` (/dev/sdb was identically partitioned.)

Next I installed mdadm (unfortunately not installed by default on the Live CD) and created the three RAID partitions resulting in:

```
hbarta@olive:~$ cat /proc/mdstat
Personalities : [raid0] [raid1] [linear] [multipath] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      995904 blocks [2/2] [UU]
      
md2 : active raid1 sdb7[1] sda7[0]
      180361600 blocks [2/2] [UU]
      [=====>...............]  resync = 26.0% (47041344/180361600) finish=41.7min speed=53198K/sec
      
md1 : active raid0 sda5[0] sdb5[1]
      20000640 blocks 64k chunks
      
unused devices: <none>
hbarta@olive:~$ 

```
(I did need to reboot between partitioning and creating the RAID devices because the new partition tables were apparently not read back into RAM.)

Finally, I created ext4 file systems on all MD devices:
```
mkfs.ext4 /dev/md0
mkfs.ext4 /dev/md1
mkfs.ext4 /dev/md2
```

I found that if there were not file systems in the MD devices, the installer wanted to partition them before formatting them and I did not wish to do that.

With that done, I was ready to start the installation from the Live CD. At the point where the installer asks to partition the devices, I selected manual. When presented with the choices to select partitions, I selected the second entry for each RAID device for the respective partitions. I found it was necessary to indicate that / and /boot be reformatted even though they were empty. Otherwise the installer would later complain that it could not delete existing files from the system partition and refuse to proceed.

Installation completed and upon first boot I was dumped into a console window with the error that the root device had timed out and a busybox prompt '(initramfs)'. Apparently the RAID devices were not started at the point where the kernel needed to mount them. Through some research and trial and error, I came up with the following procedure to resolve this using a Live CD boot. The basic idea is to add modules and mdadm to the initramfs so that the RAID devices are started early enough in the boot sequence. After opening a terminal window when booted from the Live CD, I executed the following commands:

Install mdadm and start the RAID devices
```
sudo apt-get install mdadm
sudo mdadm -A /dev/md0
sudo mdadm -A /dev/md1
sudo mdadm -A /dev/md2
cat /proc/mdstat
```

Mount them:
```
sudo mount /dev/md1 /mnt
sudo mount /dev/md0 /mnt/boot
```

Make bind mounts and start a chroot:

```
sudo mount --bind /dev/ /mnt/dev
sudo mount --bind /proc/ /mnt/proc
sudo mount --bind /sys/ /mnt/sys
sudo chroot /mnt
```

Add raid0, raid1, dm_raid4 modules to the following file:
```
hbarta@olive:~$ cat /etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
raid0
raid1
dm_raid45
hbarta@olive:~$
``` 

Install mdadm in the chroot (e.g. the environment I hope to boot.)
```
sudo apt-get install mdadm
```

At this point I could restart and boot from the system hard drives and proceed with configuring my system. :guitar:

I'm not positive that it is necessary to add the modules to /etc/initramfs-tools/modules but I do know that alone is not sufficient.

An earlier attempt was to install grub (install-grub /dev/sda; install-grub /dev/sdb) within the chroot and I found that also was not sufficient. I have not listed it above because I think it was not necessary. But on these two issues, I'm not going to reinstall again from scratch just try...

I also found this post helpful and gave me some hints to help with what I was doing:

[http://ubuntuforums.org/showthread.php?t=1653682](http://ubuntuforums.org/showthread.php?t=1653682)

Another possibility is to install using the Alternate CD. I did not try that but it may provide better RAID handling. Last week I installed 10.04.2 LTS Server to a RAID1 and it did not experience this problem. However I do not know if it is RAID in general or RAID0 that led to the issues I encountered.

I hope this helps someone.

thanks,
hank

---

### Post by bpb_21 on 2011-04-19
Yes - quite helpful.  I was trying to install on RAID10 without much progress.  This should be quite helpful.

---

