---
title: "wubi no file system defined"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by blackangelpr on 2012-06-13
greetings since i was having issues trying to install ubuntu native i give a try to wubi but it tells me when it load up: system file not define , so i run boot info script...  

can some one tell me whats wrong ?

just in case this is a Asus G73JH , it uses two HDD  the first one must be the windows 7 and the another one its used for installations of games 

Intel Core i7 
8 GIgs of memory 

thanks in advance:



                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64   976,768,064   976,768,001   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb121 74,917,697,194,063,94752,286,354,756,606,411-22,631,342,437,457,535 -
/dev/sdb122 2,930,316,326,153,938,327118,219,549,806,615,168-2,812,096,776,347,323,158 -
/dev/sdb123 1,699,667,730,382,387,714811,318,107,992,444,979-888,349,622,389,942,734 -
/dev/sdb124 357,811,176,877,263,0862,254,348,411,322,198,0941,896,537,234,444,935,009 -

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        265ACDC75ACD93C9                       ntfs       Games
/dev/sdb1        6E24C7EC24C7B57D                       ntfs       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
d841a0f5020002000b26025c53ca1920
Unknown GPT Partiton Type
db7b166c35a4d02324a5422f19360dec
Unknown GPT Partiton Type
c317cbbb6c80e98a2ae2bb286a5dc2a1
Unknown GPT Partiton Type
c5a04d0734c142b310c1286388ec328f
Unknown BootLoader on sdb1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

---

### Post by darkod on 2012-06-13
You see for /dev/sdb is says GUID Partition Table detected but doesn't seem to be used.

If sdb had gpt table and you tried to convert it to msdos table with windows, it often deletes only the main gpt table but leaves the backup gpt table and this confuses linux. I guess the first try to have proper dual boot didn't work because of that.

I would advise you to remove the remains of gpt if you are really using this disk as msdos. You can do that with fixparts running from ubuntu live mode (boot with the cd in Try Ubuntu).
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

After that is done, I would boot windows and remove wubi (ubuntu) from Programs. Once sdb is fixed, you can install the real dual boot as you planned to, don't use the virtual wubi.

---

### Post by blackangelpr on 2012-06-15
> **darkod said:**
> You see for /dev/sdb is says GUID Partition Table detected but doesn't seem to be used.

If sdb had gpt table and you tried to convert it to msdos table with windows, it often deletes only the main gpt table but leaves the backup gpt table and this confuses linux. I guess the first try to have proper dual boot didn't work because of that.

I would advise you to remove the remains of gpt if you are really using this disk as msdos. You can do that with fixparts running from ubuntu live mode (boot with the cd in Try Ubuntu).
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

After that is done, I would boot windows and remove wubi (ubuntu) from Programs. Once sdb is fixed, you can install the real dual boot as you planned to, don't use the virtual wubi.

need little helping hand (>_<) 

```
 
ubuntu@ubuntu:/dev$ fixparts
FixParts 0.8.4
Type device filename, or press <Enter> to exit:

```

what i should do ? i am very very lost

---

### Post by darkod on 2012-06-15
Start it as root user (sudo) and using the device name you want to fix, (/dev/sdb). So, it would be:
```
sudo fixparts /dev/sdb
```

I haven't used it in this situation but it should offer you immediately to fix the gpt backup table problem.

---

### Post by blackangelpr on 2012-06-15
> **darkod said:**
> Start it as root user (sudo) and using the device name you want to fix, (/dev/sdb). So, it would be:
```
sudo fixparts /dev/sdb
```I haven't used it in this situation but it should offer you immediately to fix the gpt backup table problem.

```

MBR command (? for help): a
Toggle active flag for partition: 1

MBR command (? for help): p

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x24DB55E4
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    64    976768064   primary     Y        Y      0x07

MBR command (? for help): 1
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): a
Toggle active flag for partition: 1

MBR command (? for help): p

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x24DB55E4
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             64    976768064   primary     Y        Y      0x07

MBR command (? for help): 



```


i guess i need to restart and try to see if ubuntu recognize windows to be able to install right?:lolflag:

---

### Post by darkod on 2012-06-15
Did it ask you anything about sorting out the gpt issue?

If you are happy with the fixparts procedure, you also need to use 'w' to write the changes.

After that restart and boot win7. Go into Programs and remove wubi (ubuntu). Then try to install again.

---

### Post by blackangelpr on 2012-06-15
> **blackangelpr said:**
> ```

MBR command (? for help): a
Toggle active flag for partition: 1

MBR command (? for help): p

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x24DB55E4
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    64    976768064   primary     Y        Y      0x07

MBR command (? for help): 1
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): a
Toggle active flag for partition: 1

MBR command (? for help): p

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x24DB55E4
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             64    976768064   primary     Y        Y      0x07

MBR command (? for help): 



```


i guess i need to restart and try to see if ubuntu recognize windows to be able to install right?:lolflag:


I restarted log in to windows 7 just in case and now Ubuntu recognize the windows partition to install side by size I give 200.5 gigs for Ubuntu yeah finally!!  Thanks a lot.):P

---

### Post by darkod on 2012-06-15
No problem. Don't forget that you seem to have a wubi install inside windows which you should remove to avoid any confusions.

---

