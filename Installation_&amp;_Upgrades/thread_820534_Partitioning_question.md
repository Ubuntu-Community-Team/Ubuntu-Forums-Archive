---
title: "Partitioning question"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by bsamson on 2008-06-06
Good Morning. I am ATTEMPTING to install Ubuntu 8.04 on my notebook however I am running into a partitioning issue. This is what I have done so far:

In windows vista I went to DISK MANAGEMENT and shrank the vista partition and ended up with a 30gb partition for ubuntu. Then I booted up ubuntu via live cd and formated that 30gb parition in EXT2. Now, I am not familiar with the pros and cons of linux partition so in the past I have used guided. I was hoping there would be an option to use the linux partition present via guided. NOPE! Ubuntu wants to either use the entire harddrive, or shrink the vista ntfs parition. Which is NOT an option as this never seems to work (screws up my vista install.)

So, what do I need to do? I simply want ubuntu desktop on a dual boot setup (which I was successful with ubuntu 7.10.)

Thanks in advance for any assistance!

---

### Post by meindian523 on 2008-06-06
Go to manual and select the partition you have created for Ubuntu.Click Edit partition and set the mount points as you need them.

---

### Post by bsamson on 2008-06-06
Thanks for the help meindian523. Is there no way to use guided so ubuntu does it thing?? What are the default partitions / mount points that ubuntu uses w/ guided?

---

### Post by meindian523 on 2008-06-06
I'm not sure about the guided since I've never used it,coz it needs the entire HDD.As an educated guess,I can say,it might be using only / and swap areas.Please post ```
sudo fdisk -l
```from the Live CD,then I could advise you further about mount points you can use and the sizes of the partitions.
The attached pic can give you quite some info about what mount points to use.Usually,separate partitions are created for / /home and swap.

---

### Post by bsamson on 2008-06-06
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15541   124830720    7  HPFS/NTFS
/dev/sda2           15542       19457    31455270   83  Linux

Disk /dev/mmcblk0: 125 MB, 125698048 bytes
8 heads, 32 sectors/track, 959 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         959      122702+   6  FAT16

---

### Post by meindian523 on 2008-06-06
What you can do is make an extended partition out of your 30 GB partition (/dev/sda2)which you have set aside for Linux,use the Partition Editor in System>>Administration on the Live CD if you are not confident with using the in-installer partitioning utility.
Then create within the extended partition:

1]a swap partition of (2*size of RAM).This is optional if you have RAM more than 1.5 GB.Select filesystem as swap.

2]a partition approximately 6-8 GB.Select filesystem as ext3 and mount point as /.

3]a partition with size whatever is left of the 30 GB.Again select filesystem as ext3 and mount point as /home.

The last partition will enable you to graduate from upgrade to upgrade without losing your data.When you upgrade,you can simply opt out of formatting this partition and your data will be safe.Only take care that the username and password are same as the install you are replacing.

---

