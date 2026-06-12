---
title: "Drive problem after unintalling via Wubi"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by wvcadle on 2011-11-14
I'm almost to the point at which I'm comfortable enough with Ubuntu to use it as my main OS.  I've got it running my laptop, so I decided to uninstall it from my desktop so I can prepare my desktop for a full Ubuntu installation.

My problem:  after uninstalling from within Windows, I still have two partitions on my 2nd hard drive that are 'unformatted', which I'm assuming are the locations of the former Ubuntu installation and swap file.  I thought that installing and uninstalling via Wubi would return my Windows machine to its former state?

Also, even though I installed via Wubi, I'm pretty sure Grub got installed as well, because when I boot my computer, I get a list of options, with 3 or 4 Ubuntu options at the top and a Windows option at the bottom.  Once I choose the Windows option, it then takes me to another prompt asking me if I want to boot into Windows or Ubuntu (only 2 options).

1. Why are the two unformatted partitions (or pieces of a partition) still there?
2. Does it sound like Grub is installed?  If so, how can I return my machine to its previous state, with only Windows 7 installed, with a Windows bootloader?

---

### Post by Mark Phelps on 2011-11-14
> **wvcadle said:**
> 1. Why are the two unformatted partitions (or pieces of a partition) still there?
Answer ... don't know.  Wubi does NOT create partitions; instead, it creates a file (root.disk) inside an existing MS Windows (NTFS) partition.  Removing Wubi is like uninstalling an existing Windows app -- it has no effect on partitions.

To see your partition info, boot into an Ubuntu desktop CD, choose Try Ubuntu, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one). That will list out the partitions on your drive.  Post the results back here.
> 2. Does it sound like Grub is installed?  If so, how can I return my machine to its previous state, with only Windows 7 installed, with a Windows bootloader?
Wubi does NOT install GRUB -- which is one of the reasons that it is recommended for use in TRYING Ubuntu -- it does not mess with the Windows MBR in any way.  If GRUB is there, you may have done an Update from inside Ubuntu -- and IT installed GRUB.

To remove GRUB, you need to restore your Windows MBR.  The Boot-Repair CD claims to be able to do that.  Read the details at the link below:  

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by wvcadle on 2011-11-14
Well, apparently, even though I uninstall Ubuntu (Wubi), it's still there.  Here are the results:

Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0xb04fb04f 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2055   155076607    77537276+   7  HPFS/NTFS/exFAT 
/dev/sda2       155076608   976771071   410847232    f  W95 Ext'd (LBA) 
/dev/sda5       155078656   976771071   410846208    7  HPFS/NTFS/exFAT 

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x4480ac6b 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1            2048  1397051339   698524646    7  HPFS/NTFS/exFAT 
/dev/sdb2      1638402048  1953519615   157558784    7  HPFS/NTFS/exFAT 
/dev/sdb3      1397051390  1638402047   120675329    5  Extended 
/dev/sdb5      1397051392  1630015487   116482048   83  Linux 
/dev/sdb6      1630017536  1638402047     4192256   82  Linux swap / Solaris 

Partition table entries are not in disk order 

Disk /dev/sdc: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x5c74ae42 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1            2048   488394751   244196352    7  HPFS/NTFS/exFAT 

Disk /dev/sdd: 18 MB, 18612224 bytes 
1 heads, 36 sectors/track, 1009 cylinders, total 36352 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x6f20736b 

Disk /dev/sdd doesn't contain a valid partition table 

Disk /dev/mapper/cryptswap1: 4292 MB, 4292870144 bytes 
255 heads, 63 sectors/track, 521 cylinders, total 8384512 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x531fc535 

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

---

### Post by bcbc on 2011-11-14
That's not a wubi install - it's a real dual boot. Since you are already booting with Grub, if you remove those partitions it will stop your computer booting.

---

### Post by wvcadle on 2011-11-14
So how do I get it back to a Windows only system until I'm ready?

---

### Post by bcbc on 2011-11-14
Step 1:
Reinstall the windows boot loader

Step 2:
Make sure your computer boots straight into Windows - no grub menu, no sign of Ubuntu.

Step 3: 
Remove the partitions. To see what they look like in Windows, check out the screenshot at this link: [http://askubuntu.com/questions/79086/remove-failed-ubuntu-installation/79237#79237](http://askubuntu.com/questions/79086/remove-failed-ubuntu-installation/79237#79237)

To do step 1, you can boot a Windows 7 repair CD to a repair command prompt and run (you can create a win 7 repair CD from within Win 7):
```
bootrec /fixboot
```

---

### Post by Mark Phelps on 2011-11-15
If you don't have a Win7 Repair CD, look at the last step in my post #2.  You can use that to rewrite the Windows MBR.

---

### Post by wvcadle on 2011-11-15
Thanks all.  I'll try to be a good steward and mark my posts as solved.  All is well again.

I'm not sure it's comfortably possible to complete go without a Windows partition, without knowing more Linux than I do.  There are certain things I use (MagicJack for instance) that just doesn't have a Linux counterpart or driver.  But, I'll get my disks where I want them, then reinstall Ubuntu again, and use it for everything but a handful of Windows programs (or tasks that are just easier in Windows).

---

