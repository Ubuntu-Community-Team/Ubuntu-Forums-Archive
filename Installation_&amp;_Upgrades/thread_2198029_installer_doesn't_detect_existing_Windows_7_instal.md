---
title: "installer doesn't detect existing Windows 7 installation [12.04 LTS]"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by Niles M on 2014-01-06
Hi everybody

I am trying to install Ubuntu 12.04 LTS on my new laptop, which came with Windows 7. I would like a dual-boot, so I'm not going to format it. However, the installer **can't**  see the Windows 7 installation. What should I do here? I haven't been able to find a decisive answer online to why the installer can't see the installation.

I am a beginner with Ubuntu, but eager to learn. This is the output of fdisk:


------------------------------------------------------------------------------------
Disk /dev/sda: 3879 MB, 3879731200 bytes
120 heads, 62 sectors/track, 1018 cylinders, total 7577600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a4339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62     7573919     3786929    c  W95 FAT32 (LBA)

Disk /dev/sdb: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders, total 351651888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x58311bd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sdb2         3074048   294836223   145881088    7  HPFS/NTFS/exFAT
/dev/sdb3       294836224   336969727    21066752    7  HPFS/NTFS/exFAT
/dev/sdb4       336969728   351649791     7340032   84  OS/2 hidden C: drive
------------------------------------------------------------------------------------


Thanks in advance.

Niles.

---

### Post by varunendra on 2014-01-09
Hello Niles,

It looks like a typical factory installed Win7 system which has used up all 4 partitions which is the maximum limit of (primary) partitions for an MBR type partitioning scheme. But in this case, the installer should still see the Windows installation and offer the option to 'Overwrite' the windows installation *(since it can't create yet another partition to install Ubuntu as the limit of max partitions has been reached)*. Can you post a screenshot of its partition manager where you *think* it does not see the Windows installation?

In any case, you are not going to be able to install Ubuntu unless you delete at least one of the existing four partitions to make room for Ubuntu partition.

In this kind of setups, usually -
[list][*]The first partition is the 'System' or 'Boot' partitions where Windows keeps its boot files.
[*]The second partition is the main installation partition where windows is installed and in which all of your user data resides.
[*]The third partition is 'Recovery' partition where the backup of current installation is stored. In case of disaster, this backup is used to restore the laptop to the state you purchased it in.
[*]The fourth partition usually contains the vendor's software utilities which an average user never uses. But in some laptops, it can also contain the main recovery program which starts the recovery.[/list]

The size of your partitions (all approx. 1.5 GB, 139 GB, 20 GB and 6 GB) perfectly matches this scheme, indicating it is most probably the same or similar plan as described above. To confirm, you can take a look at partition sizes and corresponding volume labels using "sudo parted -l" and "sudo blkid" commands, or in the friendly GUI of **Gparted** program which is included on the Live CD.

My recommendation is to create a set of **Windows Recovery DVDs** *(from control-panel > Backup & Restore)*, as well as a Windows Repair disk, in case you need to just restore/repair its booting. Once these disks are created and verified for data integrity, keep them safe somewhere and there would be no more use for the recovery or utility partitions. Delete one or both of them using Gparted and run Ubuntu Live CD again. This time, it should present you the option to install 'alongside windows'.

For more detailed help, if you need it, please post either a screenshot of the Gparted program (showing your Hard disk), or post the outputs of commands -
```
sudo parted -l
sudo blkid
```

---

