---
title: "RAID 5 with Intel RST Ubuntu 16.04"
date: 2018-10-23
forum: Installation &amp; Upgrades
---

### Post by cbertin on 2018-10-23
I'm trying to get Intel RST RAID 5 working, but I need some guidance, and I also need it to be accessible from both Ubuntu and Windows 10 (dual boot machine). Is this possible? 
Here is some info of what I'm working with, any help and guidance will be greatly appreciated!

lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
> NAME          SIZE FSTYPE          TYPE MOUNTPOINT
sdb           3,7T isw_raid_member disk 
sr0          1024M                 rom  
nvme1n1     238,5G                 disk 
&#9500;&#9472;nvme1n1p3 237,1G ntfs            part 
&#9500;&#9472;nvme1n1p1   360M vfat            part 
&#9500;&#9472;nvme1n1p4   876M ntfs            part 
&#9492;&#9472;nvme1n1p2   128M                 part 
sdc           3,7T isw_raid_member disk 
sda           3,7T isw_raid_member disk 
nvme0n1     894,3G                 disk 
&#9500;&#9472;nvme0n1p3   976M swap            part [SWAP]
&#9500;&#9472;nvme0n1p1   512M vfat            part /boot/efi
&#9492;&#9472;nvme0n1p2 892,8G ext4            part /

cat /proc/mdstat 
> Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md127 : inactive sdc[2](S) sda[1](S) sdb[0](S)
      9459 blocks super external:imsm
       
unused devices: <none>



fdisk -l
> Disk /dev/nvme0n1: 894,3 GiB, 960197124096 bytes, 1875385008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3839B5FD-2E46-4BF1-9279-FBA5DFB9EA28


Device              Start        End    Sectors   Size Type
/dev/nvme0n1p1       2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2    1050624 1873385471 1872334848 892,8G Linux filesystem
/dev/nvme0n1p3 1873385472 1875384319    1998848   976M Linux swap




Disk /dev/nvme1n1: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B182B613-2C29-4310-A707-6395EE1F5C46


Device             Start       End   Sectors   Size Type
/dev/nvme1n1p1      2048    739327    737280   360M EFI System
/dev/nvme1n1p2    739328   1001471    262144   128M Microsoft reserved
/dev/nvme1n1p3   1001472 498313215 497311744 237,1G Microsoft basic data
/dev/nvme1n1p4 498313216 500107263   1794048   876M Windows recovery environment




Disk /dev/sda: 3,7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sdb: 3,7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sdc: 3,7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


---

