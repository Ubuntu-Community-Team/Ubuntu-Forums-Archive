---
title: "Installing ubuntu 19.10 alongside zorin os 15"
date: 2019-10-30
forum: Installation &amp; Upgrades
---

### Post by jithtitan007 on 2019-10-30
[COLOR=#000000]Hi guys,
I was planning to create a dual boot in my existing zorin os 15 system with the new ubuntu 19.10.
But the problem is that out of the 1TB hdd space i allocated all the remaining space after swap and other things to zorin os root partition. But when i tried to install ubuntu it gives me the option to install ubuntu alongside zorin and even i can slide the disk space between the two. Will this work? Or is it something error in the part of ubuntu installation setup?
is there a way i can install ubuntu without uninstalling zorin os in such a parition?
Thanks[/COLOR]

---

### Post by dee-2019 on 2019-10-31
Hi, I haven't done dual booting before but from what I read it's important to resize partitions before installing another OS. Therefore I would think that if you have 1 TB of data and allocated most to Zorin, it is just a matter of reallocation to allocate free space for Ubuntu installation, so you aren't just trying to squeeze it in. I never used Zorin, so not sure if it has GParted, and if so you can re-allocate disc space. I recommend though first reading up on partitioning for dual boot. This article may help, and it also suggests using virtual box instead of dual booting. https://askubuntu.com/questions/164179/please-recommend-partition-sizes-for-my-dual-boot-configuration-1tb-big-ntfs-p

---

### Post by yancek on 2019-10-31
Post the output of sudo fdisk -l or an image of the drive from GParted so we know specifically what partitions you have, how many and where they are located on the drive.

---

### Post by jithtitan007 on 2019-11-01
This is the reponse of the code```
[FONT=arial][B] [I]sudo fdisk -l

Disk /dev/loop0: 193.3 MiB, 202657792 bytes, 395816 sectors[/I]
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop1: 149.9 MiB, 157192192 bytes, 307016 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop2: 140.7 MiB, 147501056 bytes, 288088 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop3: 156 MiB, 163614720 bytes, 319560 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop4: 54.5 MiB, 57151488 bytes, 111624 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop5: 165.2 MiB, 173228032 bytes, 338336 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop6: 83.9 MiB, 87945216 bytes, 171768 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop7: 96.1 MiB, 100794368 bytes, 196864 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 4096 bytes*
*I/O size (minimum/optimal): 4096 bytes / 4096 bytes*
*Disklabel type: gpt*
*Disk identifier: C09A4242-5C41-4625-8569-D59E26EDC652*

*Device       Start        End    Sectors   Size Type*
*/dev/sda1     2048    3999743    3997696   1.9G Linux swap*
*/dev/sda2  3999744    4976639     976896   477M EFI System*
*/dev/sda3  4976640 1953523711 1948547072 929.1G Linux filesystem*


*Disk /dev/loop8: 140.7 MiB, 147501056 bytes, 288088 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop9: 54.9 MiB, 57499648 bytes, 112304 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop10: 89.1 MiB, 93454336 bytes, 182528 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop11: 44.2 MiB, 46325760 bytes, 90480 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop12: 136.2 MiB, 142786560 bytes, 278880 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop13: 145 MiB, 151998464 bytes, 296872 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop14: 54.5 MiB, 57139200 bytes, 111600 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop15: 57.1 MiB, 59863040 bytes, 116920 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop16: 193.3 MiB, 202657792 bytes, 395816 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop17: 57.1 MiB, 59920384 bytes, 117032 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop18: 66.5 MiB, 69758976 bytes, 136248 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop19: 96.1 MiB, 100794368 bytes, 196864 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop20: 110 MiB, 115302400 bytes, 225200 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop21: 202.9 MiB, 212713472 bytes, 415456 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop22: 165 MiB, 172953600 bytes, 337800 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop23: 84.3 MiB, 88367104 bytes, 172592 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop24: 144.7 MiB, 151724032 bytes, 296336 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop25: 125.3 MiB, 131346432 bytes, 256536 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop26: 42.8 MiB, 44879872 bytes, 87656 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop27: 66.8 MiB, 70066176 bytes, 136848 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop28: 206 MiB, 215994368 bytes, 421864 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop29: 144.6 MiB, 151646208 bytes, 296184 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop30: 89 MiB, 93327360 bytes, 182280 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*


*Disk /dev/loop34: 54.9 MiB, 57499648 bytes, 112304 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 512 bytes*
*I/O size (minimum/optimal): 512 bytes / 512 bytes*[/B][/FONT]
```

---

### Post by jithtitan007 on 2019-11-01
[https://ibb.co/HXNpSC3](https://ibb.co/HXNpSC3)

Here is the gparted output.

---

### Post by yancek on 2019-11-01
The info in your first post indicating he Ubuntu installer suggests installing itself alongside Zorin should work.  To have more control over it, you can use GParted which should be on the Ubuntu DVD/USB you are using.  Open GParted and make sure the Zorin partition is not mounted.  Then highlight /dev/sda3 in the main window and go to the Partition tab at the top of the GParted screen and select the option to Resize/Move and in the new window, set the size you want for the Zorin partition and the remaining space will be available as unallocated for you to use for Ubuntu.  After the Resize selection, you need to click on Apply.  Don't see that option in your image so if you don't have an Apply button there should be a check mark you can click.  Mouse over the options at the top and it should show.  

You should also read through the Ubuntu documentation at the site below.  It talks specifically about dual booting UEFI with windows but the Introduction and General Principles sections give important information on dual booting UEFI.  Since Zorin is UEFI, you need to make sure you install Ubuntu UEFI and that is explained at the link so read through the entire page.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-11-01
Best to use Something Else where you either create partition(s) in advance or during install.
Then you can have a separate /home and maybe not use existing swap partition. Ubuntu will use existing swap also, but normal install now uses a swap file. If you click do not use on swap partition then it will still create a swap file.

If using multiple installs often better to have smaller / (root) partitions and separate data partition(s). Then you can mount data in every install. Best not to share /home as settings in one system may conflict with other system.

Be sure to boot installer in UEFI boot moe.

---

