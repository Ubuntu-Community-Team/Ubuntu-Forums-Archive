---
title: "Cannot boot - stack on grub console"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by Tomino2112 on 2014-01-17
Hi,

My HDD died, so I bought new one and installing ubuntu (12.04). Everything went well, but when I tried to boot after installation, I got only black screen with cursor.
So I went back to live cd, and installed and ran the boot-repair tool. That helped a bit, but now I am stuck on grub console screen. 

For about half a second before it goes to grub console, I see eroor: "error: efidisk read error"

Here is the link from boot-repair: [http://paste.ubuntu.com/6769294/](http://paste.ubuntu.com/6769294/)

Thanks for any help!

---

### Post by fantab on 2014-01-17
```

parted -l:

Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
**Partition Table: msdos**

Number  Start   End     Size    Type      File system     Flags
1      2096kB  47.7GB  47.7GB  **extended**
5      2097kB  41.9GB  41.9GB  logical   ext4
6      41.9GB  47.3GB  5348MB  logical   linux-swap(v1)
**7      47.3GB  47.7GB  416MB   logical   fat32           boot**
2      47.7GB  153GB   105GB   primary   ext4
3      153GB   195GB   41.9GB  primary   ext4
4      195GB   1000GB  806GB   primary   ntfs
```


```
sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 92372992.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi
```


You have installed both Windows and Ubuntu in EFI mode. (I wonder how you managed that on a 'MBR' disk).
To boot an OS in EFI mode your HDD needs to have GUID Parition Table [GPT], but your HDD has 'msdos'/MBR table. **EFI will NOT work on 'msdos'/MBR**.
Check in your UEFI/BIOS to see if EFI boot is enabled/disabled....

Your options:
**--I--**
Delete partition /dev/sda7.
[Fix Windows Boot]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html").
Run Boot-Repair again. (Make sure you boot Ubuntu in 'legacy/MBR' mode).

**--II--**
Reformat the HDD with GPT. (All partitions and data will be lost)
Reinstall both Windows and Ubuntu in EFI mode.

Good Luck

---

