---
title: "Multiple partition mappings appear using dmraid &amp; kpartx"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by jlc2010 on 2011-12-11
Hi,

I'm running Ubuntu 11.10 with dmraid (RAID1) with several GPT partitions.  I have a dual boot configuration with different drives (MBR partitions) for Windows 7.  I'm using kpartx to activate the GPT partitions.  After booting, I have multiple partition mappings to the same devices:

$ ls -lR /dev/mapper/
/dev/mapper/:
total 0
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 35000cca35dc57988 -> ../dm-11
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 35000cca35dc57988-part1 -> ../dm-20
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 35000cca35dc57988-part2 -> ../dm-21
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 35000cca35dc7bc42 -> ../dm-9
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 35000cca35dc7bc42-part1 -> ../dm-18
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 35000cca35dc7bc42-part2 -> ../dm-19
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d6f9 -> ../dm-10
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d6f9-part1 -> ../dm-13
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d6f9-part2 -> ../dm-14
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d6f9-part3 -> ../dm-15
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d6f9-part4 -> ../dm-16
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d6f9-part5 -> ../dm-17
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d703 -> ../dm-12
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d703-part1 -> ../dm-22
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d703-part2 -> ../dm-23
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d703-part3 -> ../dm-24
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d703-part4 -> ../dm-25
lrwxrwxrwx 1 root root       8 2011-12-11 01:39 350024e920375d703-part5 -> ../dm-26
crw------- 1 root root 10, 236 2011-12-11 01:39 control
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_caadcjbaii_V0 -> ../dm-0
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_caadcjbaii_V0p1 -> ../dm-1
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_caadcjbaii_V0p2 -> ../dm-2
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_cdbceedjci_V1 -> ../dm-3
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_cdbceedjci_V1p1 -> ../dm-4
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_cdbceedjci_V1p2 -> ../dm-5
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_cdbceedjci_V1p3 -> ../dm-6
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_cdbceedjci_V1p4 -> ../dm-7
lrwxrwxrwx 1 root root       7 2011-12-11 01:39 isw_cdbceedjci_V1p5 -> ../dm-8

If you look at /dev/disk/by-id, you can see another symptom of the problem:

/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 ata-Hitachi_HDS721010CLA332_JP2921HQ0D1AYA -> ../../sda
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 ata-Hitachi_HDS721010CLA332_JP2921HQ0K0J3A -> ../../sdb
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 ata-HL-DT-ST_BD-RE_WH10LS30_K95A8C51822 -> ../../sr0
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 ata-SAMSUNG_HE103SJ_S2JBJ90Z900448 -> ../../sdd
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 ata-SAMSUNG_HE103SJ_S2JBJ90Z900458 -> ../../sdc
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-35000cca35dc57988 -> ../../dm-11
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-35000cca35dc57988-part1 -> ../../dm-20
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-35000cca35dc57988-part2 -> ../../dm-21
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-35000cca35dc7bc42 -> ../../dm-9
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-35000cca35dc7bc42-part1 -> ../../dm-18
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-35000cca35dc7bc42-part2 -> ../../dm-19
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d6f9 -> ../../dm-10
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d6f9-part1 -> ../../dm-13
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d6f9-part2 -> ../../dm-14
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d6f9-part3 -> ../../dm-15
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d6f9-part4 -> ../../dm-16
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d6f9-part5 -> ../../dm-17
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d703 -> ../../dm-12
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d703-part1 -> ../../dm-22
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d703-part2 -> ../../dm-23
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d703-part3 -> ../../dm-24
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d703-part4 -> ../../dm-25
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-name-350024e920375d703-part5 -> ../../dm-26
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_caadcjbaii_V0 -> ../../dm-0
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_caadcjbaii_V0p1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_caadcjbaii_V0p2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_cdbceedjci_V1 -> ../../dm-3
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_cdbceedjci_V1p1 -> ../../dm-4
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_cdbceedjci_V1p2 -> ../../dm-5
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_cdbceedjci_V1p3 -> ../../dm-6
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_cdbceedjci_V1p4 -> ../../dm-7
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-name-isw_cdbceedjci_V1p5 -> ../../dm-8
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-DMRAID-isw_caadcjbaii_V0 -> ../../dm-0
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-DMRAID-isw_cdbceedjci_V1 -> ../../dm-3
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-mpath-35000cca35dc57988 -> ../../dm-11
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-mpath-35000cca35dc7bc42 -> ../../dm-9
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-mpath-350024e920375d6f9 -> ../../dm-10
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-mpath-350024e920375d703 -> ../../dm-12
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part1-DMRAID-isw_caadcjbaii_V0 -> ../../dm-1
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part1-DMRAID-isw_cdbceedjci_V1 -> ../../dm-4
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part1-mpath-35000cca35dc57988 -> ../../dm-20
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part1-mpath-35000cca35dc7bc42 -> ../../dm-18
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part1-mpath-350024e920375d6f9 -> ../../dm-13
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part1-mpath-350024e920375d703 -> ../../dm-22
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part2-DMRAID-isw_caadcjbaii_V0 -> ../../dm-2
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part2-DMRAID-isw_cdbceedjci_V1 -> ../../dm-5
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part2-mpath-35000cca35dc57988 -> ../../dm-21
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part2-mpath-35000cca35dc7bc42 -> ../../dm-19
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part2-mpath-350024e920375d6f9 -> ../../dm-14
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part2-mpath-350024e920375d703 -> ../../dm-23
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part3-DMRAID-isw_cdbceedjci_V1 -> ../../dm-6
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part3-mpath-350024e920375d6f9 -> ../../dm-15
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part3-mpath-350024e920375d703 -> ../../dm-24
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part4-DMRAID-isw_cdbceedjci_V1 -> ../../dm-7
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part4-mpath-350024e920375d6f9 -> ../../dm-16
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part4-mpath-350024e920375d703 -> ../../dm-25
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 dm-uuid-part5-DMRAID-isw_cdbceedjci_V1 -> ../../dm-8
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part5-mpath-350024e920375d6f9 -> ../../dm-17
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 dm-uuid-part5-mpath-350024e920375d703 -> ../../dm-26
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_caadcjbaii_V0-part1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_caadcjbaii_V0-part2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_cdbceedjci_V1-part1 -> ../../dm-4
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_cdbceedjci_V1-part2 -> ../../dm-5
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_cdbceedjci_V1-part3 -> ../../dm-6
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_cdbceedjci_V1-part4 -> ../../dm-7
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 raid-isw_cdbceedjci_V1-part5 -> ../../dm-8
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-35000cca35dc57988 -> ../../dm-11
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-35000cca35dc57988-part1 -> ../../dm-20
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-35000cca35dc57988-part2 -> ../../dm-21
lrwxrwxrwx 1 root root 10 2011-12-11 01:39 scsi-35000cca35dc7bc42 -> ../../dm-9
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-35000cca35dc7bc42-part1 -> ../../dm-18
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-35000cca35dc7bc42-part2 -> ../../dm-19
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d6f9 -> ../../dm-10
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d6f9-part1 -> ../../dm-13
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d6f9-part2 -> ../../dm-14
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d6f9-part3 -> ../../dm-15
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d6f9-part4 -> ../../dm-16
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d6f9-part5 -> ../../dm-17
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d703 -> ../../dm-12
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d703-part1 -> ../../dm-22
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d703-part2 -> ../../dm-23
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d703-part3 -> ../../dm-24
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d703-part4 -> ../../dm-25
lrwxrwxrwx 1 root root 11 2011-12-11 01:39 scsi-350024e920375d703-part5 -> ../../dm-26
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 scsi-SATA_Hitachi_HDS7210_JP2921HQ0D1AYA -> ../../sda
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 scsi-SATA_Hitachi_HDS7210_JP2921HQ0K0J3A -> ../../sdb
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 scsi-SATA_SAMSUNG_HE103SJS2JBJ90Z900448 -> ../../sdd
lrwxrwxrwx 1 root root  9 2011-12-11 01:39 scsi-SATA_SAMSUNG_HE103SJS2JBJ90Z900458 -> ../../sdc
...

Only the set that begins with isw_ are the primary ones, but all of these are showing up as separate drives.  How do I determine what is causing this duplication?  Any help would be greatly appreciated.

Thanks.

    -John

---

### Post by jlc2010 on 2011-12-18
Looking at this further, I think I see what is happening.  I have 2 FakeRAID1 array sets with 2 drives each.  Each array drive is showing up separately, with a device mapping to each partition on each drive:

    ```

Win7:        isw_caadcjbaii_V0                               dm-0        
                     isw_caadcjbaii_V0-part1                 dm-1    
                     isw_caadcjbaii_V0-part2                 dm-2    

                 sda       5000cca35dc57988                 dm-11
                              5000cca35dc57988-part1       dm-20
                              5000cca35dc57988-part2       dm-21
                 sdb       5000cca35dc7bc42                 dm-9
                              5000cca35dc7bc42-part1       dm-13
                              5000cca35dc7bc42-part2       dm-14
        
    Ubuntu:     isw_cdbceedjci_V1                           dm-3        
                     isw_cdbceedjci_V1-part1                dm-4    
                     isw_cdbceedjci_V1-part2                dm-5    
                     isw_cdbceedjci_V1-part3                dm-6    
                     isw_cdbceedjci_V1-part4                dm-7    
                     isw_cdbceedjci_V1-part5                dm-8
    
                 sdc       50024e920375d703                dm-12
                              50024e920375d703-part1      dm-22
                              50024e920375d703-part2      dm-23
                              50024e920375d703-part3      dm-24
                              50024e920375d703-part4      dm-25
                              50024e920375d703-part5      dm-26

                 sdd       50024e920375d6f9                dm-10
                              50024e920375d6f9-part1      dm-15
                              50024e920375d6f9-part2      dm-16
                              50024e920375d6f9-part3      dm-17
                              50024e920375d6f9-part4      dm-18
                              50024e920375d6f9-part5      dm-19

```On top of this, I'm getting the following errors from dmraid before it lists the 2 raid sets:

# dmraid -s
ERROR: isw: seeking device "/dev/dm-22" to 18446744073709517312
ERROR: isw: seeking device "/dev/dm-15" to 18446744073709517312
ERROR: isw: Could not find disk /dev/dm-12 in the metadata
ERROR: isw: Could not find disk /dev/dm-11 in the metadata
ERROR: isw: Could not find disk /dev/dm-10 in the metadata
ERROR: isw: Could not find disk /dev/dm-9 in the metadata
ERROR: isw: seeking device "/dev/dm-4" to 18446744073709517312
...

I don't think I should be seeing separate dm-xx entries for each drive & partition.  At most, I should see dm-0 thru dm-8.  Has anyone seen this before?  How do I fix this?  Any help would be greatly appreciated.

Thanks.

    -John

---

