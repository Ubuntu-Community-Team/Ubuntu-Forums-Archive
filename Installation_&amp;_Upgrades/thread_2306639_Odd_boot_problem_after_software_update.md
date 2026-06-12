---
title: "Odd boot problem after software update"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2015-12-17
After doing a software update/upgrade (apt-get update, apt-get dist-upgrade), on reboot: no bootable parition was found. I've had this occur once before and running boot-repair fixed the problem. So I tried running boot-repair from a live disk, but this time the problem persisted (on boot, couldn't find a bootable parition). I had an empty partition, so I loaded ubuntu (15.10) from a live image, and ... all is good. The new install found all bootable partitions, and installed grub correctly (I assume), etc.

So short story:
1) Sometimes, updating software corrupts/moves/changes the boot process in a way it fails to see any bootable partition (this has happened twice now).
2) boot-repair does not currently work as it causes the same problem (failure to see a bootable partition).
3) loading a new ubuntu from live CD works (recognizes all bootable partitions).

Thoughts?

My current setup:
sda1  /boot/efi
sda2 swap
sda3 14.04
sda4 15.10 (what I use daily)
sda5 15.10 (loaded only to fix the problem above)
sda6 an ext4 partition for backups, files, etc.

---

### Post by kc1di on 2015-12-17
the problem lie in the efi boot partion not being over written with new info /or being over written with new info.

Boot-repair is supposed for fix that but it's flaky, in how it does it at the moment. at least that's been my experience.
In my case I used the Live DVD to reinstall grub-efi and it worked. 
So when you did the new install it created a new grub efi file. 

Glad you Got in going and thanks for posting for others who may be having the same problem.

---

### Post by aeronutt on 2015-12-17
Interesting!   What's the command for (re)installing grub-efi?

---

### Post by kc1di on 2015-12-17
> **aeronutt said:**
> Interesting!   What's the command for (re)installing grub-efi?

I followed the commands found at this [site.]("http://superuser.com/questions/376470/how-to-reinstall-grub2-efi")

---

### Post by aeronutt on 2016-01-02
Ok, so finally getting some time to work on this problem.

Reinstalling grub-efi didn't work for me. (At least the way I reinstalled grub-efi as shown on the web site above, didn't work for me.)

I'm looking at boot-repair, and I'm confused by its default settings. Specifically, 'grub location' is shown as:

[img]http://i.imgur.com/KedN18i.png[/img]

However, when I install ubuntu from a live CD (which is the only way I get now get my machine to boot), it says it's loading grub at /dev/sda

So, is this the problem with boot-repair? (eg, the fact that's it's loading grub at /dev/sda1 rather than /dev/sda ?

---

### Post by aeronutt on 2016-01-06
Ok, very frustrated because whenever I update the kernels (via sudo apt-get dist-upgrade) of my current version of 15.10, my computer fails to boot and I have to load a 'fresh' version of 15.10 onto another partition. Boot-repair won't fix it. This is one of those 'no wonder Linux will never be mainstream as a personal OS' frustrations.

---

### Post by yancek on 2016-01-06
> I'm looking at boot-repair, and I'm confused by its default settings. Specifically, 'grub location' is shown as

It indicates the OS you want to boot is on sda4, that is the root filesystem.  In your initial post you show that you have an EFI partition so installing the Grub boot files to sda1 is correct.  If you were using a standard MBR, you would install to /dev/sda.  If you do that with an EFI system, it won't boot.

You have mentioned using boot repair in multiple posts.  Is there any specific reason why you haven't posted the output here where some of the more experienced users in EFI can take a look at it?

---

### Post by aeronutt on 2016-01-06
Good idea! (Although running boot-repair will mean I'll have to reload 15.10 again. :))  I'll run it, save log, and post.
Just to be clear, updating using 'apt-get dist-upgrade' causes the same problem. So it's not inherent to just boot-repair. Although agree, looking at boot-repair log may give a clue.

---

### Post by chodar on 2016-01-06
Similar situation in my xubuntu after a update. won't boot.
Even when im still can't resolve my problem, maybe you can try a couple of links that I menction in my post [here]("http://ubuntuforums.org/showthread.php?t=2308928").

Good luck!

---

### Post by aeronutt on 2016-01-06
> **yancek said:**
> It indicates the OS you want to boot is on sda4, that is the root filesystem.  In your initial post you show that you have an EFI partition so installing the Grub boot files to sda1 is correct. ** If you were using a standard MBR, you would install to /dev/sda.  If you do that with an EFI system, it won't boot.**

You have mentioned using boot repair in multiple posts.  Is there any specific reason why you haven't posted the output here where some of the more experienced users in EFI can take a look at it?

Odd, because when I load 15.10 onto a partition, it says its putting grub at /dev/sda, and this is the ONLY way it works.

[img]http://i.imgur.com/J75XVVM.jpg[/img]

---

### Post by aeronutt on 2016-01-06
So the boot-repair log file is 2600 lines, anything in particular to post?

---

### Post by chodar on 2016-01-06
Maybe the bootinfo Summary can help the experts.

---

### Post by aeronutt on 2016-01-06
First few sections of the boot-repair log (run from 15.10 at /dev/sda4) is below.
Symptoms:
Running boot-repair from 15.10 at /dev/sda4 causes computer to FAIL to boot.
Updating 15.10 (apt-get dist-upgrade) when kernels are updated, which is loaded at /dev/sda4, causes computer to FAIL to boot.
Loading a new copy of 15.10 to /dev/sda5 fixes boot problems.


```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2       1,026,048     9,218,047     8,192,000 Swap partition (Linux)
/dev/sda3       9,218,048    41,959,423    32,741,376 Data partition (Linux)
/dev/sda4      41,959,424    66,531,327    24,571,904 Data partition (Linux)
/dev/sda5      66,531,328    82,947,343    16,416,016 Data partition (Linux)
/dev/sda6      82,948,096   488,396,799   405,448,704 Data partition (Linux)

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048    16,775,167    16,773,120 Intel Fast Flash (iFFS) partition (for Intel Rapid Start technology)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        xxxx-xxxx                              vfat       
/dev/sda2        xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   swap       
/dev/sda3        xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   ext4       
/dev/sda4        xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   ext4       
/dev/sda5        xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   ext4       
/dev/sda6        xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   ext4       datapartition
/dev/sdb1                                                          

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jan  6 16:34 ata-HL-DT-ST_DVD+_-RW_GU90N_KM6D8KI4034 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan  6 17:45 ata-LITEONIT_LMS-32L6M_mSATA_32GB_TW0H9R7V5508537G5186 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan  6 17:46 ata-LITEONIT_LMS-32L6M_mSATA_32GB_TW0H9R7V5508537G5186-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P -> ../../sda
lrwxrwxrwx 1 root root 10 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan  6 17:45 ata-Samsung_SSD_840_EVO_250GB_S1DBNSADA73680P-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Jan  6 16:34 wwn-0x5001480000000000 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan  6 17:45 wwn-0x50025388a0093fcb -> ../../sda
lrwxrwxrwx 1 root root 10 Jan  6 17:45 wwn-0x50025388a0093fcb-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan  6 17:45 wwn-0x50025388a0093fcb-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan  6 17:45 wwn-0x50025388a0093fcb-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan  6 17:45 wwn-0x50025388a0093fcb-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan  6 17:45 wwn-0x50025388a0093fcb-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan  6 17:45 wwn-0x50025388a0093fcb-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda4        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda6        /mnt/datapartition       ext4       (rw,relatime,errors=remount-ro,data=ordered)
```

---

