---
title: "Wubi no root file system defined..."
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by bernardosgr on 2013-04-12
Hi there, I've seen this problem around but considering there's no "protocol" steps to take in order to fix it I decided to post the diagnosis, help would be appreciated

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,465,145,343 1,464,938,496   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Kubuntu 12.04.2 LTS amd64
/dev/loop1                                              squashfs   
/dev/sda1        C8CE3005CE2FEB00                       ntfs       Sistema Reservado
/dev/sda2        64D43273D4324796                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=============================== StdErr Messages: ===============================

umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


```

---

### Post by bernardosgr on 2013-04-13
bump, sorry but I desperately need ths to complete a project for school

---

### Post by bcbc on 2013-04-14
The problem is this:
> [COLOR=#000000][FONT=Ubuntu Mono]GUID Partition Table detected, but does not seem to be used.[/FONT][/COLOR]

The installer (ubiquity) uses parted to check for partitions and this is considered an error, which means that it cannot find the selected partition and this results in the dialog you see.

The cause is that the disk once had a GUID partition table, but now has a MBR partition table. There is some leftover GUID data that parted considers ambiguous enough to fail.

The only way to fix this is to run: [fixparts]("http://www.rodsbooks.com/fixparts/")

Note the same error will occur on a normal dual boot (preferred method of installing). 
Note, once you fix it and install successfully, if you're using Wubi keep regular, preferably synchronized backups as the file system is virtual and corruption can result in total loss of data.

PS the other way to get around it is to run wubi.exe and install Ubuntu (without any ISO present). This uses a preinstalled disk image and therefore bypasses ubiquity and parted. So should work. You could always install [kubuntu-desktop afterwards]("http://www.psychocats.net/ubuntu/kde").

---

### Post by bernardosgr on 2013-04-14
If I use fixparts am I risking erasing my windows boot? or is it safe? Do I have to uninstall kubuntu from the add/remove programs in the control panel or can I just run wubi and Install ubuntu?

---

### Post by bcbc on 2013-04-14
There's always some risk and if you have important data that's not backed up, you should back it up.

That said, I've never heard any reports of problems using fixparts. And I can point you to this (the answer is by the author of fixparts): [http://askubuntu.com/questions/231987/if-i-need-to-erase-gpt-data-after-doing-a-fixpart-will-it-also-erase-all-my-fil]("http://askubuntu.com/q/231987/14916")

---

