---
title: "Can't dualboot; Ubuntu installer thinks drive is empty"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by tofagerl on 2011-08-20
I've installed win7, and now I want to dualboot with Ubuntu. Boot from installer goes fine, but partitioner and gparted both say that the drive is empty. Bootinfoscript shows all partitions correctly, and after running it I can mount the windows partitions, but the installer still says it's empty. 

Yes, it's got GPT.

```
     Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......X......0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1445848 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78161328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    61,442,047    61,235,200   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,458,175 1,953,456,128   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2017 MB, 2017525248 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3940479 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     3,940,460     3,940,398   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0AF22D72F22D62E5                       ntfs       System Reserved
/dev/sda2        88343A0D3439FEAE                       ntfs       
/dev/sdc1        D7A4-CC47                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 76 90 45 58 46 41 54  20 20 20 00 00 00 00 00  |.v.EXFAT   .....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  00 08 00 00 00 00 00 00  00 60 6f 74 00 00 00 00  |.........`ot....|
00000050  00 08 00 00 00 f0 00 00  00 f8 00 00 68 6e 74 00  |............hnt.|
00000060  0b 00 00 00 d9 4e 49 4e  00 01 00 00 09 08 01 80  |.....NIN........|
00000070  07 00 00 00 00 00 00 00  f4 f4 f4 f4 f4 f4 f4 f4  |................|
00000080  f4 f4 f4 f4 f4 f4 f4 f4  f4 f4 f4 f4 f4 f4 f4 f4  |................|
*
000001f0  f4 f4 f4 f4 f4 f4 f4 f4  f4 f4 f4 f4 f4 f4 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by tofagerl on 2011-08-20
Problem solved with fixparts.

---

### Post by YesWeCan on 2011-08-20
You need to get rid of the unused GPT. As there are both MBR PT and GPT the Ubuntu installer are freaking out.

From live CD (do this exactly as written or you may trash your disk)
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=1

Then try the installer again.

---

### Post by srs5694 on 2011-08-20
The only disk that seems to have GPT data is /dev/sda, and that data appears to be left over from a previous configuration. At the very least, /dev/sda is not currently a valid GPT disk, since it lacks a protective partition (of type 0xEE) in the MBR. Unless I'm very much mistaken in this analysis, the best way to proceed is to eliminate the old GPT data from /dev/sda. There are several ways to do this, but the quickest and most reliable is to use my [FixParts](http://www.rodsbooks.com/fixparts/) program. When you launch it on /dev/sda, it should offer to delete the old GPT data. Tell it to do so and the data will be erased, and thereafter GParted should be able to handle the disk. (The problem is caused by a bug in libparted, upon which GParted relies; libparted can't cope with MBR disks that have this leftover GPT data.)

If you're certain that the GPT data are valid, please elaborate. It's conceivable that restoring a valid protective MBR would be a better way to proceed; however, I think that's extremely unlikely. As it's configured now, Windows sees your disk as an MBR disk, not as a GPT disk, so even if you started with a GPT disk, it's now in a state in which Windows (and most OSes and tools) ignore the GPT data.

---

### Post by srs5694 on 2011-08-20
> **YesWeCan said:**
> You need to get rid of the unused GPT. As there are both MBR PT and GPT the Ubuntu installer are freaking out.

From live CD (do this exactly as written or you may trash your disk)
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=1

Then try the installer again.

As described [in this thread,](http://ubuntuforums.org/showthread.php?t=1826661) among other places, this is poor advice, since it *damages*, but *does not completely delete*, the GPT data. The result can be confusion or potentially even data loss in the future.

---

### Post by YesWeCan on 2011-08-20
> **srs5694 said:**
> As described [in this thread,]("http://ubuntuforums.org/showthread.php?t=1826661") among other places, this is poor advice, since it *damages*, but *does not completely delete*, the GPT data. The result can be confusion or potentially even data loss in the future.

Your arguments in that thread are irrelevant to this case. There is no protective MBR.

---

### Post by srs5694 on 2011-08-20
Although the details differ, there are still risks. If you damage GPT data as you advocate, even if the MBR contains regular MBR data and not a protective MBR, the backup GPT data will remain on the disk. As I've said repeatedly, GPT recovery tools can and will find backup GPT data -- the GPT backup data exists at the end of the disk so that it *can* be found in case of accidental damage to the primary data, and the intentional damage you're advocating is impossible for a utility to distinguish from accidental damge. If a user runs such a GPT data recovery program in the future (whether tomorrow or five years from now), therefore, the result could be confusion or even data loss, depending on what the program does and how the user uses the utility. Advocating damaging the primary GPT data and leaving the backup data intact, particularly without spelling out what the risks are, is *reckless*. Safer alternatives exist, and fortunately, tofagerl used one of them.

---

### Post by YesWeCan on 2011-08-20
> **srs5694 said:**
> Although the details differ, there are still risks. If you damage GPT data as you advocate, even if the MBR contains regular MBR data and not a protective MBR, the backup GPT data will remain on the disk. As I've said repeatedly, GPT recovery tools can and will find backup GPT data -- the GPT backup data exists at the end of the disk so that it *can* be found in case of accidental damage to the primary data, and the intentional damage you're advocating is impossible for a utility to distinguish from accidental damge. If a user runs such a GPT data recovery program in the future (whether tomorrow or five years from now), therefore, the result could be confusion or even data loss, depending on what the program does and how the user uses the utility. Advocating damaging the primary GPT data and leaving the backup data intact, particularly without spelling out what the risks are, is *reckless*. Safer alternatives exist, and fortunately, tofagerl used one of them.
Nonsense. You are unable to come up with any evidence of any risk of a problem. Please stop being alarmist and contrary and have some respect for other member's solutions.

---

### Post by srs5694 on 2011-08-20
> **YesWeCan said:**
> Nonsense. You are unable to come up with any evidence of any risk of a problem. Please stop being alarmist and contrary and have some respect for other member's solutions.

[http://ubuntuforums.org/showpost.php?p=11171908&postcount=11](http://ubuntuforums.org/showpost.php?p=11171908&postcount=11)

The scenario laid out there applies to this case.

As to respect, I can't respect the suggestion of using dd to damage GPT data; the result is just that -- ***damage***, not the desired solution of deletion. Better alternatives exist.

---

