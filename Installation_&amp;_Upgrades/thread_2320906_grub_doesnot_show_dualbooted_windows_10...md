---
title: "grub doesnot show dualbooted windows 10.."
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by satyam_kapoor on 2016-04-18
Whenever  i boot into system, linux loads without grub.. when holding Shift, Grub loads but doesnt show Windows 10.. i think i have installed linux wrong way.. whats the solution of it without loosing data..I have attached the fdisk and update-grub details if it could help.. pls give me solution.. i m a new user..

---

### Post by LostFarmer on 2016-04-18
You do have a GPT partitioned disk, now we need to know how linux was installed EFI/legacy mode.  In a terminal run both commands and post outputs.
```
ls /sys/firmware 
sudo parted -l     NOTE:-l is a small L
```


Added:  westie457 recommendation will give more information.  You can run Boot-Repair instead.

---

### Post by westie457 on 2016-04-18
[COLOR=#000000]Welcome to the Forum.[/COLOR]

[COLOR=#000000]While you have Ubuntu running go here. [/COLOR][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[COLOR=#000000]Use the 2nd option to install Boot Repair. When it is running do not attempt any repairs, just click on 'Create a Boot Info summary' and post the generated link here so we can peruse the situation and make informed suggestions to help you fix this.

ps I am going to ask for this thread to be moved to the correct area.[/COLOR]

---

### Post by slickymaster on 2016-04-18
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by grahammechanical on 2016-04-18
Did you by any chance install Ubuntu by installing wubi.exe from inside Windows 10?

There is something strange about the printout from fdisk -l. It only shows one partition and it does not have a file system on it. I do not have Windows on my system but I do have 2 hard drives. One with GPT partitioning & one with DOS partitioning and 2 installs of Ubuntu on each. This is my printout.
```

Disk /dev/sda: 232.9 GiB, 250000000000 bytes, 488281250 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 711AFC71-CB9D-498E-AE26-87126F2AF9D5

Device         Start       End   Sectors   Size Type
/dev/sda1       8192     16383      8192     4M BIOS boot
/dev/sda2      16384    147455    131072    64M EFI System
/dev/sda3     147456   8536063   8388608     4G Linux filesystem
/dev/sda4    8536064  16924671   8388608     4G Linux filesystem
/dev/sda5   16924672 447743999 430819328 205.4G Linux filesystem
/dev/sda6  447744000 488280063  40536064  19.3G Linux filesystem


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0008e2df

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         4096  78386908  78382813  37.4G 83 Linux
/dev/sdb2        78389246 976773119 898383874 428.4G  5 Extended
/dev/sdb5       972503040 976773119   4270080     2G 82 Linux swap / Solaris
/dev/sdb6        78389248 856629247 778240000 371.1G 83 Linux
/dev/sdb7       856631296 972500436 115869141  55.3G 83 Linux
```

With GPT & Windows 10 you should be showing a EFI boot partition as well as partitions for Windows & Ubuntu + swap

Regards.

---

### Post by LostFarmer on 2016-04-18
Posting only to clarify the fdisk output of the OP.

> **grahammechanical said:**
> 
There is something strange about the printout from fdisk -l. It only shows one partition and it does not have a file system on it. .

grahammechanica--That will be the correct output from an old version of fdisk.  The fdisk he is using if for MBR partitioned disk only.

---

