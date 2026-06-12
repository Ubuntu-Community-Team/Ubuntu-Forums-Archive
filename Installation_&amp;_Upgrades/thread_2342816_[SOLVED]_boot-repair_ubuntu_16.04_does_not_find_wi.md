---
title: "[SOLVED] boot-repair ubuntu 16.04 does not find windows xp on 2nd HDD"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by ferhue on 2016-11-10
Hi,
I have installed Ubuntu 16.04 on my first HDD drive (sda). My second one (sdb) contained a Windows XP installation.
I followed the [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) instructions to try to add my windows XP to the grub menu, but to no avail.

Here the info report:
[http://paste2.org/Y6DK3Ivv](http://paste2.org/Y6DK3Ivv)

Am I doing something wrong? Could you help me to correct this, or at least to add the entry manually? Thanks in advance.

---

### Post by yancek on 2016-11-10
You have no entry in the grub.cfg file (the menu you see on boot) for xp.  I would try opening a terminal in Ubuntu and running the command below, watch the output for a windows entry.

> sudo update-grub

Older windows systems often were troublesome when not on the first drive so you may need to use drive mapping.  Post back the results of the command above if you still need help.

---

### Post by oldfred on 2016-11-10
You show no boot.ini file which is required for booting Windows and for grub to find Windows to know what is a bootable Windows partition.

Were you booting from another Windows install? Only one Windows NTFS partition with boot flag on drive set in BIOS as default boot can be the Windows partition with boot files.

I would add a Windows boot loader to sdb's MBR and run Windows repairs. Windows XP really likes to be first drive and first partition but does not have to be, but some then have issues.

---

### Post by ferhue on 2016-11-11
sudo update-grub just returns to me the Linux entries, no Windows is found.

Note that I have Linux on /dev/sda (first drive), and Windows XP on the second one /dev/sdb. The sdb has to partitions, sdb1 and sdb2. Boot flag is on sdb1.

```
Device     Boot     Start       End   Sectors   Size Id Type
    /dev/sda1  *         2048   1046527   1044480   510M 83 Linux

     /dev/sda2         1046528  59639807  58593280    28G 83 Linux

     /dev/sda3        59639808 304769023 245129216 116.9G 83 Linux

     /dev/sda4       304769024 312580095   7811072   3.7G 82 Linux swap / Solaris

  
 
    Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors

     Units: sectors of 1 * 512 = 512 bytes

     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disklabel type: dos
     Disk identifier: 0x428bd3de
  
    Device     Boot     Start       End   Sectors   Size Id Type
     /dev/sdb1  *           63 319998734 319998672 152.6G  7 HPFS/NTFS/exFAT
     /dev/sdb2       319998735 976768064 656769330 313.2G  7 HPFS/NTFS/exFAT
```

Concerning the boot.ini, you are right, it is not present on Windows, I am trying to create it now based on this:
```

[boot loader]
        timeout=5
        default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
        [operating systems]
        multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional Edition" /fastdetect
```

but not sure if this is ok?

---

### Post by ferhue on 2016-11-11
Ok, I just added by hand this boot.ini file as explained before, and then run sudo os-prober and sudo update-grub2, images are now found. Rebooting shows the Windows entry, and it begins to start, but fails with the message that \system32\hal.dll is missing. I checked and the file does exist, so I guess that my hand-made boot.ini contains an error.

---

### Post by ferhue on 2016-11-11
Ok, the problem is now solved. I just replaced rdisk(1) with rdisk(0) and it works now. Thanks!

---

### Post by oldfred on 2016-11-11
Glad it worked.

Since Windows usually likes to be on first drive, grub usually does a map command to switch drives as posted by BIOS, so then Windows is still on first drive even though not really. Then boot.ini has to have correct drive as you found out.

---

