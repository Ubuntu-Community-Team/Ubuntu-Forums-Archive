---
title: "Ubuntu error 'The computer has no operating systems on it'"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by j_vinayak on 2010-06-16
Hi All,

    I have Windows XP installed on my computer. I am trying to install UBUNTU 10.04 through CD. However, at step 4 of Installation GUI, it displays 'The computer has no operating systems on it' though Windows XP is already installed. 

   I have attached the screenshot of error. I am not able to proceed further with installation. Please help.

:confused:

Thanks and Regards,
Vinayak

---

### Post by walle1357 on 2010-06-16
Please post a bit more information. Try running 
"cat /proc/partition" in the terminal and post the results here.

---

### Post by ajgreeny on 2010-06-16
What happens if you click on the "specify partitions manually" and then click on "Forward"?  Does it then see you windows installation?

---

### Post by j_vinayak on 2010-06-17
Clicking on 'specify partitions manually' also doesn't help. It doesn't detect XP partition and displays a single empty partition.

---

### Post by darkod on 2010-06-17
> **j_vinayak said:**
> Clicking on 'specify partitions manually' also doesn't help. It doesn't detect XP partition and displays a single empty partition.

The message that it doesn't have OS is not important that much. What is a big problem is that it doesn't see the partitions on it. Usually this happens if there is some error in the partition table.

From live mode can you run:

sudo fdisk -l

to see what it says?

---

### Post by j_vinayak on 2010-06-21
> **walle1357 said:**
> Please post a bit more information. Try running 
"cat /proc/partition" in the terminal and post the results here.

Following is the output of command 'cat /proc/partitions':

[B]ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   7        0     687976 loop0
   8        0   78150744 sda
   8        1    7622811 sda1
   8        2          1 sda2
   8        3   30716248 sda3
   8        5    2441817 sda5
   8        6     176683 sda6
   8        7   30716248 sda7
   8        8    6466131 sda8[/B]

Can you please Help?

---

### Post by j_vinayak on 2010-06-21
> **darkod said:**
> The message that it doesn't have OS is not important that much. What is a big problem is that it doesn't see the partitions on it. Usually this happens if there is some error in the partition table.

From live mode can you run:

sudo fdisk -l

to see what it says?


Hi Darko,

  I executed the commad 'sudo fdisk -l'. It displays the following:

[B]ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf266f266

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         949     7622811    7  HPFS/NTFS
/dev/sda2             950        9728    70517317+   f  W95 Ext'd (LBA)
/dev/sda3            1276        5099    30716248+   7  HPFS/NTFS
/dev/sda5             950        1253     2441817   83  Linux
/dev/sda6            1254        1275      176683+  82  Linux swap / Solaris
/dev/sda7            5100        8923    30716248+   7  HPFS/NTFS
/dev/sda8            8924        9728     6466131    7  HPFS/NTFS[/B]

I think it is detecting the partitions in this command. But while installing UBUNTU, it doesn't. Please Help. :(

---

### Post by darkod on 2010-06-21
Did you already install ubuntu? In that list you have linux partitions sda5 and sda6.

---

### Post by louieb on 2010-06-21
The Ubuntu partitioner does not see any partitions - you have a non-standard partition table 

primary partition sda3 is inside extended partition sda2 -  

```

[B]Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         949     7622811    7  HPFS/NTFS
/dev/sda2             [COLOR=Red]950        9728[/COLOR]    70517317+   f  W95 Ext'd (LBA)
/dev/sda3            [COLOR=Red]1276        5099[/COLOR]    30716248+   7  HPFS/NTFS
/dev/sda5             950        1253     2441817   83  Linux
/dev/sda6            1254        1275      176683+  82  Linux swap /  Solaris
/dev/sda7            5100        8923    30716248+   7  HPFS/NTFS
/dev/sda8            8924        9728     6466131    7  HPFS/NTFS[/B]


```

You will need to get the partition table in standard form before the Ubuntu installer will detect your partitions.

---

### Post by j_vinayak on 2010-06-22
Hi,

   I removed my Windows XP OS which was earlier on NTFS file system and re-installed it using FAT32 File System.
   After that, I performed UBUNTU installation and it detected my Windows XP! :)

  Now I have installed UBUNTU 10.04 on a separate partition and things are running smooth .... :)


Thanks a lot for all those who replied and provided inputs!
Cheers!

:p

---

