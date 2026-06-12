---
title: "Dual Boot with Pre installed Windows 8"
date: 2014-11-06
forum: Installation &amp; Upgrades
---

### Post by matt154 on 2014-11-06
I installed Ubuntu on my laptop with windows 8 pre installed. I followed every guide I could find on the internet. Now the laptop boots directly into windows 8. I figured out how to get into Ubuntu by shuting down windows to access the uefi settings then it lets me choose if I want to boot the OS Manager, UEFI DVD or CD, or Ubuntu.  So I choose Ubuntu and it boot fine. I ran boot-repair and clicked on created boot info summary; it gave me this  [http://paste.ubuntu.com/8855476/](http://paste.ubuntu.com/8855476/) which is my boot order. I was hoping someone could look at it and tell me what is the problem. The summary is below. Disregard anything but sda

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Acronis/asrm.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 60372 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /EFI/BOOT/grubx64.efi

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1         821,248     1,353,727       532,480 EFI System partition
/dev/sda2       1,353,728     1,615,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3       1,615,872   562,227,199   560,611,328 Data partition (Windows/Linux)
/dev/sda4     562,227,200   582,227,967    20,000,768 Swap partition (Linux)
/dev/sda5     582,227,968   625,141,759    42,913,792 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 31.6 GB, 31625052160 bytes
255 heads, 63 sectors/track, 3844 cylinders, total 61767680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    61,767,679    61,765,632   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,192    31,116,287    31,108,096   c W95 FAT32 (LBA)


```


Can anyone help??

---

### Post by ajgreeny on 2014-11-06
You have not shown all the output from boot-repair, so it's difficult to know what the problem might be, so please run it again and copy back here the link to the report that it gives, or if you must copy the report again, please put it in code tags (see my signature for how to do that).

---

### Post by oldfred on 2014-11-06
Your problem is that it is an HP. What model?

HP has modified UEFI to only boot a system in UEFI mode with Windows in the description. But we have several work arounds for HP.

Several options that others have posted that work:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Other HP's, most manually renamed files like bootx64.efi.

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

