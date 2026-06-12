---
title: "Ubuntu 14.04 Install Hangs at &quot;Preparing to install Ubuntu&quot;"
date: 2017-01-03
forum: Installation &amp; Upgrades
---

### Post by ostrumvulpes on 2017-01-03
Hello folks,

I asked a question over at Ask Ubuntu but didn't get any responses, so I thought I should try out this forum. The original Ask Ubuntu post can be found [here]("http://askubuntu.com/questions/860496/ubuntu-14-04-install-hangs-at-preparing-to-install-ubuntu").

I am trying to install Ubuntu 14.04 (64-bit) onto an SSD on a desktop that already has Windows 10 on another SSD and HDD. However, the installation hangs at the stage: **Preparing to install Ubuntu**. I've done the following:
[LIST=1]
[*]Used Rufus to load the Ubuntu 14.04 ISO onto a USB flash drive
[*]Disabled secureboot/fastboot on the MOBO's BIOS
[*]Boot into either the "Try Ubuntu" or "Install" option with option **nomodeset**.
[/LIST]

The layout of my drives is such:
[LIST]
[*]/dev/sda - Windows 10 SSD
[*]/dev/sdb - HDD used as storage by Windows 10
[*]/dev/sdc - Unformatted SSD to be used for Ubuntu
[*]/dev/sdd - USB flash drive containing Ubuntu
[/LIST]

I am getting the following printout from System Log when it hangs, and I am having trouble interpreting it and figuring out what to do next to resolve the issue.

```

Dec 13 01:51:43 ubuntu ubiquity[4098]: switched to page prepare
Dec 13 01:51:45 ubuntu ubiquity[4098]: debconffilter_done: ubi-prepare (current: ubi-prepare)
Dec 13 01:51:45 ubuntu ubiquity[4098]: Step_before = stepPrepare
Dec 13 01:51:45 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Dec 13 01:51:45 ubuntu partman:   No matching physical volumes found
Dec 13 01:51:45 ubuntu partman:   Reading all physical volumes.  This may take a while...
Dec 13 01:51:45 ubuntu partman:   No volume groups found
Dec 13 01:51:45 ubuntu partman-lvm:   No volume groups found
Dec 13 01:51:50 ubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Dec 13 01:51:50 ubuntu ntfsresize: Device name        : /dev/sda4
Dec 13 01:51:50 ubuntu ntfsresize: NTFS volume version: 3.1
Dec 13 01:51:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Dec 13 01:51:50 ubuntu ntfsresize: Current volume size: 118536270336 bytes (118537 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Current device size: 118536273920 bytes (118537 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Checking filesystem consistency ...
Dec 13 01:51:50 ubuntu ntfsresize: Accounting clusters ...
Dec 13 01:51:50 ubuntu ntfsresize: Space in use       : 83905 MB (70.8%)
Dec 13 01:51:50 ubuntu ntfsresize: Collecting resizing constraints ...
Dec 13 01:51:50 ubuntu ntfsresize: You might resize at 83904434176 bytes or 83905 MB (freeing 34632 MB).
Dec 13 01:51:50 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Dec 13 01:51:50 ubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Dec 13 01:51:50 ubuntu ntfsresize: Device name        : /dev/sda5
Dec 13 01:51:50 ubuntu ntfsresize: NTFS volume version: 3.1
Dec 13 01:51:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Dec 13 01:51:50 ubuntu ntfsresize: Current volume size: 470807040 bytes (471 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Current device size: 470810624 bytes (471 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Checking filesystem consistency ...
Dec 13 01:51:50 ubuntu ntfsresize: Accounting clusters ...
Dec 13 01:51:50 ubuntu ntfsresize: Space in use       : 351 MB (74.4%)
Dec 13 01:51:50 ubuntu ntfsresize: Collecting resizing constraints ...
Dec 13 01:51:50 ubuntu ntfsresize: You might resize at 350404608 bytes or 351 MB (freeing 120 MB).
Dec 13 01:51:50 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Dec 13 01:51:50 ubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Dec 13 01:51:50 ubuntu ntfsresize: Device name        : /dev/sda6
Dec 13 01:51:50 ubuntu ntfsresize: NTFS volume version: 3.1
Dec 13 01:51:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Dec 13 01:51:50 ubuntu ntfsresize: Current volume size: 471855616 bytes (472 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Current device size: 471859200 bytes (472 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Checking filesystem consistency ...
Dec 13 01:51:50 ubuntu ntfsresize: Accounting clusters ...
Dec 13 01:51:50 ubuntu ntfsresize: Space in use       : 347 MB (73.4%)
Dec 13 01:51:50 ubuntu ntfsresize: Collecting resizing constraints ...
Dec 13 01:51:50 ubuntu ntfsresize: You might resize at 346177536 bytes or 347 MB (freeing 125 MB).
Dec 13 01:51:50 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Dec 13 01:51:50 ubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Dec 13 01:51:50 ubuntu ntfsresize: Device name        : /dev/sdb1
Dec 13 01:51:50 ubuntu ntfsresize: NTFS volume version: 3.1
Dec 13 01:51:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Dec 13 01:51:50 ubuntu ntfsresize: Current volume size: 314569216 bytes (315 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Current device size: 314572800 bytes (315 MB)
Dec 13 01:51:50 ubuntu ntfsresize: Checking filesystem consistency ...
Dec 13 01:51:50 ubuntu ntfsresize: Accounting clusters ...
Dec 13 01:51:50 ubuntu ntfsresize: Space in use       : 251 MB (79.7%)
Dec 13 01:51:50 ubuntu ntfsresize: Collecting resizing constraints ...
Dec 13 01:51:50 ubuntu ntfsresize: You might resize at 250695680 bytes or 251 MB (freeing 64 MB).
Dec 13 01:51:50 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Dec 13 01:51:56 ubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Dec 13 01:51:56 ubuntu ntfsresize: Device name        : /dev/sdb4
Dec 13 01:51:56 ubuntu ntfsresize: NTFS volume version: 3.1
Dec 13 01:51:56 ubuntu ntfsresize: Cluster size       : 4096 bytes
Dec 13 01:51:56 ubuntu ntfsresize: Current volume size: 894321029632 bytes (894322 MB)
Dec 13 01:51:56 ubuntu ntfsresize: Current device size: 894321033216 bytes (894322 MB)
Dec 13 01:51:56 ubuntu ntfsresize: Checking filesystem consistency ...
Dec 13 01:51:56 ubuntu ntfsresize: Accounting clusters ...
Dec 13 01:51:56 ubuntu ntfsresize: Space in use       : 482198 MB (53.9%)
Dec 13 01:51:56 ubuntu ntfsresize: Collecting resizing constraints ...
Dec 13 01:51:56 ubuntu ntfsresize: You might resize at 482197037056 bytes or 482198 MB (freeing 412124 MB).
Dec 13 01:51:56 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Dec 13 01:51:56 ubuntu ntfsresize: ntfsresize v2013.1.13AR.1 (libntfs-3g)
Dec 13 01:51:56 ubuntu ntfsresize: Device name        : /dev/sdb5
Dec 13 01:51:56 ubuntu ntfsresize: NTFS volume version: 3.1
Dec 13 01:51:56 ubuntu ntfsresize: Cluster size       : 4096 bytes
Dec 13 01:51:56 ubuntu ntfsresize: Current volume size: 471855616 bytes (472 MB)
Dec 13 01:51:56 ubuntu ntfsresize: Current device size: 471859200 bytes (472 MB)
Dec 13 01:51:56 ubuntu ntfsresize: Checking filesystem consistency ...
Dec 13 01:51:56 ubuntu ntfsresize: Accounting clusters ...
Dec 13 01:51:56 ubuntu ntfsresize: Space in use       : 349 MB (73.9%)
Dec 13 01:51:56 ubuntu ntfsresize: Collecting resizing constraints ...
Dec 13 01:51:56 ubuntu ntfsresize: You might resize at 348536832 bytes or 349 MB (freeing 123 MB).
Dec 13 01:51:56 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Dec 13 01:51:56 ubuntu kernel: [  649.426236] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.426326] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.426400] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.426490] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda3
Dec 13 01:51:56 ubuntu kernel: [  649.426601] FAT-fs (sda3): bogus number of reserved sectors
Dec 13 01:51:56 ubuntu kernel: [  649.426602] FAT-fs (sda3): Can't find a valid FAT filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.427283] XFS (sda3): Invalid superblock magic number
Dec 13 01:51:56 ubuntu ubiquity: mount: you must specify the filesystem type
Dec 13 01:51:56 ubuntu kernel: [  649.493457] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.493612] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.493736] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.493915] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sdb3
Dec 13 01:51:56 ubuntu kernel: [  649.494036] FAT-fs (sdb3): bogus number of reserved sectors
Dec 13 01:51:56 ubuntu kernel: [  649.494038] FAT-fs (sdb3): Can't find a valid FAT filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.494585] XFS (sdb3): Invalid superblock magic number
Dec 13 01:51:56 ubuntu kernel: [  649.577154] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.577231] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.577361] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.577458] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda3
Dec 13 01:51:56 ubuntu kernel: [  649.577531] FAT-fs (sda3): bogus number of reserved sectors
Dec 13 01:51:56 ubuntu kernel: [  649.577533] FAT-fs (sda3): Can't find a valid FAT filesystem
Dec 13 01:51:56 ubuntu kernel: [  649.578060] XFS (sda3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  649.598377] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  649.598485] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  649.598574] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  649.598697] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sdb3
Dec 13 01:51:57 ubuntu kernel: [  649.598792] FAT-fs (sdb3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  649.598793] FAT-fs (sdb3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  649.599236] XFS (sdb3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.010459] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.010540] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.010615] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.010679] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda3
Dec 13 01:51:57 ubuntu kernel: [  650.010762] FAT-fs (sda3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.010763] FAT-fs (sda3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.011276] XFS (sda3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.054578] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.054678] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.054767] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.054855] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sdb3
Dec 13 01:51:57 ubuntu kernel: [  650.054942] FAT-fs (sdb3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.054943] FAT-fs (sdb3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.055466] XFS (sdb3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.163349] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.163421] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.163478] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.163536] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda3
Dec 13 01:51:57 ubuntu kernel: [  650.163594] FAT-fs (sda3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.163595] FAT-fs (sda3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.164110] XFS (sda3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.184738] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.184857] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.184952] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.185075] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sdb3
Dec 13 01:51:57 ubuntu kernel: [  650.185170] FAT-fs (sdb3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.185171] FAT-fs (sdb3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.185628] XFS (sdb3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.420601] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.420700] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.420789] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.420866] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda3
Dec 13 01:51:57 ubuntu kernel: [  650.420948] FAT-fs (sda3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.420950] FAT-fs (sda3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.421467] XFS (sda3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.442600] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.442708] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.442819] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.442920] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sdb3
Dec 13 01:51:57 ubuntu kernel: [  650.443013] FAT-fs (sdb3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.443015] FAT-fs (sdb3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.443537] XFS (sdb3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.528251] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.528326] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.528385] EXT4-fs (sda3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.528442] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sda3
Dec 13 01:51:57 ubuntu kernel: [  650.528500] FAT-fs (sda3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.528501] FAT-fs (sda3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.529042] XFS (sda3): Invalid superblock magic number
Dec 13 01:51:57 ubuntu kernel: [  650.549763] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.549860] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.549953] EXT4-fs (sdb3): VFS: Can't find ext4 filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.550053] squashfs: SQUASHFS error: Can't find a SQUASHFS superblock on sdb3
Dec 13 01:51:57 ubuntu kernel: [  650.550145] FAT-fs (sdb3): bogus number of reserved sectors
Dec 13 01:51:57 ubuntu kernel: [  650.550146] FAT-fs (sdb3): Can't find a valid FAT filesystem
Dec 13 01:51:57 ubuntu kernel: [  650.550634] XFS (sdb3): Invalid superblock magic number
```

I've tried various solutions from Stack Exchange and this forum itself, including: installing with/without internet connectivity; not installing updates; letting it run for hours; trying "Install Ubuntu" and "Try Ubuntu." However, none of these have allowed me to diagnose the problem any further.

I'd greatly appreciate any insight into this -- thanks! Even just upvoting the [Ask Ubuntu question]("http://askubuntu.com/questions/860496/ubuntu-14-04-install-hangs-at-preparing-to-install-ubuntu") if you think it is a worthwhile question would be of great help.

---

### Post by Autodave on 2017-01-04
I am assuming that you have the jumpers set correctly on all the drives: whether primary or slave? Each channel needs a primary drive.

---

### Post by ostrumvulpes on 2017-01-04
Hi Autodave, thanks for the reply. I'm using an Asus Z87 Pro ([http://dlcdnet.asus.com/pub/ASUS/mb/LGA1150/Z87-PRO/E7832_Z87-PRO.pdf](http://dlcdnet.asus.com/pub/ASUS/mb/LGA1150/Z87-PRO/E7832_Z87-PRO.pdf)) and am using the "top-most" three SATA ports.

Could you give me some insight into how I can determine if a drive is primary or slave? I've been able to try installation with /dev/sdc partitioned as a Linux drive and not partitioned at all with no further success.

---

### Post by ostrumvulpes on 2017-01-06
So I'm not sure why I didn't think of this sooner, but I decided to try the installation after disconnecting my Windows-related disks (in this case, /dev/sda and /dev/sdb) by disconnecting both the power and the SATA cables. When I tried to run the installation again, it worked instantly and I used the "Something Else" install option in Ubiquity to install it to the properly formatted 500GB SSD (with an EFI System Partition, swap partition, and ext4 partition).

I also ran sudo update-grub after reconnecting the Windows disks so that Grub could find the Windows bootloader.

I'm now in the process of fixing some post-install issues (seems like driver-related issues). Hope this proves useful to someone.

---

