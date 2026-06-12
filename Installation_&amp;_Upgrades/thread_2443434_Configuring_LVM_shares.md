---
title: "Configuring LVM shares"
date: 2020-05-15
forum: Installation &amp; Upgrades
---

### Post by tx836519 on 2020-05-15
I have a Dell T320 Server.  It is running on a RAID 10 disk array with LVM.  I am trying to mount shares in Ubuntu 20.04
I am trying to set up a server for rebuilding my home network.  I have Ubuntu 20.04 booting with the following drive setup:
Dell T320 Server
```
	sudo fdisk -l
Disk	/dev/loop0: 89.1 MiB, 93417472 bytes, 182456 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk	/dev/loop1: 38.7 MiB, 40583168 bytes, 79264 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk	/dev/loop2: 93.9 MiB, 98484224 bytes, 192352 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk	/dev/loop3: 9.1 MiB, 9510912 bytes, 18576 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 3.7 TiB, 3998614552576 bytes, 7809794048 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: gpt
Disk identifier: 926321AB-FFBB-44F1-91CA-C1ACDD4C4A5D

Device	Start	End	Sectors	Size	Type
/dev/sda1	2048	10506231	1048576	512M	EFI System
/dev/sda2	1050624	3147775	2097152	1G	Linux filesystem
/dev/sda3	3147776	7809791999	7806644224	3.7T	Linux filesystem

Disk /dev/mapper/ubuntu--vg-ubuntu-lv: 4 GiB, 4294967296 bytes, 8388608 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/ubuntu--vg-LV1: 200 GiB, 214748364800 bytes, 419430400 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/ubuntu--vg-LV2: 300 GiB, 322122547200 bytes, 129145600 sectors
Units: Sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

	```
sudo blkid
/dev/sda1: UUID=&#8221;xxxx-xxxx&#8221; TYPE=&#8221;vfat&#8221; PARTUUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&#8221;
/dev/sda2: UUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&#8221; TYPE=&#8221;ext4&#8221;PARTLABEL=&#8221;UbuntuLTS&#8221;
	PARTUUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx&#8221;
/dev/sda3: UUID=&#8221;xxxxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxxxx&#8221; TYPE=&#8221;LVM2_member&#8221;
	PARTLABEL=&#8221;shares&#8221; PARTUUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&#8221;
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx&#8221; TYPE=&#8221;ext4&#8221;
/dev/mapper/ubuntu--vg-LV1: UUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx&#8221; TYPE=&#8221;ext4&#8221;
/dev/mapper/ubuntu--vg-LV2: UUID=&#8221;xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx&#8221; TYPE=&#8221;ext4&#8221;
/dev/loop0: 	TYPE=&#8221;squashfs&#8221;
/dev/loop1: 	TYPE=&#8221;squashfs&#8221;
/dev/loop1: 	TYPE=&#8221;squashfs&#8221;
/dev/loop3: 	TYPE=&#8221;squashfs&#8221;
```

```
	cat /etc/fstab
# /etc/fstab: static file system information
	. . .
# <file system> <mount point>	<type>	<options>	<dump>	<pass>
# was on /dev/ubuntu-vg/ubuntu-lv during curtain installation
/dev/disk/by-id/dm-uuid-LVM-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx / ext4 defaults 0 0
# boot was on /dev/sda2 during curtain installation
/dev/disk/by uuid/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx /boot ext4 defaults 0 0
# /boot/efi was on /dev/sda1 during curtain installation
/dev/disk/by uuid/xxxxxxxxxx /boot/efi vfat defaults 0 0
/swap.img	none	swap	sw	0	0

```
My question is:  &#8220;Why can&#8217;t I see the LV1 and LV2 shares?  Do I need to add something else to fstab?&#8221;

---

### Post by TheFu on 2020-05-15
LVM has nothing to do with network storage sharing.  it is for storage management only.

For network storage access, something like NFS should be used on the LAN or one of the ssh-based tools (sftp/scp/rsync/sshfs) for over the internet.

if you want to mount LVM storage on the system containing the partitions, there are a few different ways.  The fstab is usually the most popular.  Usually, i would use the /dev/{vg}/{lv} symbolic links for the device part in the fstab.   They are shorter and easier.
```
/dev/vgubuntu-mate$ ls -F
home@  root@  swap_1@
```

So the fstab device would be
```
/dev/vgubuntu-mate/root      /       ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/home     /home   ext4    errors=remount-ro 0 1
/dev/vgubuntu-mate/swap_1  none  swap    sw      0       0  
```
on my 20.04 box.  There's a /boot/efi in there too.   i could use UUIDs instead, but why?  UUIDs are too obtuse.

Whenever posting terminal output/text files, please use the Advanced Editor and wrap the relevant parts in "code tags" so everything lines up clean.  

Also, removing the non-relevant parts cleans up the cruft.  We never need to see any loop devices unless snap mounts are part of the issue.

BTW, the fstab posted has a number of problems.  There aren't spaces in the device parts.  Those are just symlinks generated at boot time. There are a few different tools which do that.

---

