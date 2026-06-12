---
title: "Installing 12.04 alongside 13.10"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by walter.iandolo on 2013-12-10
Hi Everyone,

I just installed Ubuntu 13.10 on my PC.
In the installation, I wiped out the entire disk, which now has "standard" (= default) partitions and no available space.
I would like to stick with it but I realized that I cannot install the full (non-beta) AMD Catalyst drivers since they don't support Xorg 1.14.
I tried to install the beta drivers and while they "work" (= they don't crash) I cannot get OpenCL to run.
Since I need it for some very specific applications, I would like to install an older version of Ubuntu (12.04 would be good) alongside 13.10. (I don't want to downgrade Xorg).
Problem: when I pop in the USB disk with 12.04 I don't get the option to "Install alongside 13.10": I only get the option to replace it.
Is it because there's no available partition on the disk? 
What is the best/cleanest way to install an older version of Ubuntu alongside a newer one?

Walter

---

### Post by Bucky Ball on 2013-12-10
Welcome. Yes, because no available space on the partition.

What you need to do is boot from the LiveCD>Try Ubuntu>Launch Gparted>shrink the big partition (do you have a separate /home?). Could you perhaps open Gparted in the current install, take a screenshot of what you have, then, by clicking 'Go Advanced', attach the pic to a post using the paperclip icon, please?

Just a note: you can use the existing /swap partition for the 12.04 LTS install, also. No need to make a new one. More when we get there. ;)

---

### Post by fantab on 2013-12-10
Also post the output of:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by jan-goebel-g on 2013-12-10
maybe even post df -l output so we/you can see where u have space used.

[http://gerfficient.com/2013/11/11/getting-opencl-1-1-running-in-ubuntu-13-10/](http://gerfficient.com/2013/11/11/getting-opencl-1-1-running-in-ubuntu-13-10/)
U found and tried that without success?

---

### Post by walter.iandolo on 2013-12-12
Here we go:

 Disk /dev/sda: 2000GBSector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1996GB  1996GB  primary   ext4            boot
 2      1996GB  2000GB  4294MB  extended
 5      1996GB  2000GB  4294MB  logical   linux-swap(v1)



Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000216b5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3898640383  1949319168   83  Linux
/dev/sda2      3898642430  3907028991     4193281    5  Extended
/dev/sda5      3898642432  3907028991     4193280   82  Linux swap / Solaris


Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf2217c98


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001    c  W95 FAT32 (LBA)


df -l
Filesystem      1K-blocks      Used  Available Use% Mounted on
/dev/sda1      1918600240   9143376 1811974524   1% /
none                    4         0          4   0% /sys/fs/cgroup
udev              1981244         8    1981236   1% /dev
tmpfs              404860      1316     403544   1% /run
none                 5120         0       5120   0% /run/lock
none              2024288       636    2023652   1% /run/shm
none               102400        32     102368   1% /run/user


The disk (2TB) is practically empty, but I cannot resize the boot partition (I need to boot from USB, I suppose).

Any suggestion on the partitioning would be helpful, thanks.

Walter

---

### Post by Dennis N on 2013-12-12
For what it's worth, this would be my plan if I was doing it:

Delete sda5 and sda2. You wasted the only extended partition with just 4gb, all for swap. To be recreated later.
 
Resize sda1 to what you think is adequate for one os. The rest of the original sda1 is now unallocated. 
Make a new partition sda2 at the start of this unallocated space for swap. size = 4gb.
Make an extended partition sda3 of all the remaining unallocated space.
Create a logical partition at the start of sda3 for the new os. If you want a separate home, make two logical partitions.
Leave the rest of the extended partition for future use.

---

### Post by fantab on 2013-12-12
You must have let the Ubuntu's installer partition your HDD... the installer's partition method is very simple but stupid IMO.
You don't have separate '/boot' partitions, what you have is 1196Gb '/', root partition and 4Gb of SWAP.
No point in shrinking, repartition and re-install.

It is recommended that with 2Tb HDD you should use GUID Partition Table [**GPT**] instead of 'msdos'. You can use 'msdos' but it has limitations and cause worries for you in future.
[**Advantages of GPT**]("https://wiki.archlinux.org/index.php/GUID_Partition_Table").

If you are dual booting with Windows, Windows will install to GPT only in (U)EFI mode. And both must be in UEFI
Linux/Ubuntu can boot in both 'MBR' and 'UEFI' modes from GPT HDD.

Linux (and Windows) from GPT, UEFI mode, you need to create a separate Partition for EFI,
500Mb FAT32 'boot' flag.

Linux from GPT in 'MBR/Legacy/CSM/BIOS' mode, you should make a 50Mb Partition:
50Mb 'unformatted' 'bios_grub' flag.

If I were to manage my 2TB HDD with GPT, I'd do the following, In GPT all partitions are PRIMARY...
1. 50Mb Unformatted --- (put a 'bios_grub' flag only if I were to boot in 'MBR' mode, otherwise leave it unformatted).
2. 500Mb FAT32 'boot' flag (EFI partition)
3. 25Gb Ext4 '/' (Ubuntu 13.10)
4. 25Gb Ext4 '/' (Ubuntu 12.04)
5. 25Gb Ext4 'Free' (In case I want to try another flavor of Ubuntu or another distro later).
6. 4Gb SWAP
7. All the remaining GB Ext4 (A simple shared common DATA partition.)

So I would reinstall ubuntu in EFI mode, and would use GPT.

---

### Post by walter.iandolo on 2013-12-14
Hi,

a few comments:
1) Yes, I let Ubuntu installer do the partition for me. I knew it wouldn't be the best, but I didn't think it was going to be so bad.
2) I have no idea how to make/use a GPT. 
3) For now I don't plan to double boot, but that might change, depending on how successful I will be in installing some of the (Windows) games I have in Ubuntu.
4) I would really prefer not to re-install everything, unless there's some security/performance issue not doing so. Thoughts?

Thanks,
Walter

---

### Post by fantab on 2013-12-14
> **walter.iandolo said:**
> Hi,

a few comments:
1) Yes, I let Ubuntu installer do the partition for me. I knew it wouldn't be the best, but I didn't think it was going to be so bad.
2) I have no idea how to make/use a GPT. 
3) For now I don't plan to double boot, but that might change, depending on how successful I will be in installing some of the (Windows) games I have in Ubuntu.
4) I would really prefer not to re-install everything, unless there's some security/performance issue not doing so. Thoughts?



Dual Booting is good idea for Linux beginners. Some Windows games and applications can run in Ubuntu through Wine, some have Linux alternative but most will not. Until such time you are really comfortable with Ubuntu, I'd say, dual boot Windows and Ubuntu. 
Install Windows first, then Ubuntu... keeps things simple.
Making a GPT disk is damn easy with Gparted... open Gparted, In the menu look for 'Devices' -> 'create new partition table-> Advanced -> from dropdown choose 'GUID partition table or GPT'.
When you create a new partition table the HDD will be formatted and you need to re-install.
Partitioning is NOT something we do every often, if properly set up, you partitions will last as long as the HDD lasts. So setting the disk up properly is a major battle won.

If dual-booting then add NTFS partition:
1. 50Mb Unformatted --- 
2. 500Mb FAT32 'boot' flag (EFI partition)
3. 100Gb NTFS Windows C:
4. 25Gb Ext4 '/' (Ubuntu 13.10)
5. 25Gb Ext4 '/' (Ubuntu 12.04) or Free space
6. 4Gb SWAP
7. All the remaining GB Ext4 (A simple shared common DATA partition.)

---

