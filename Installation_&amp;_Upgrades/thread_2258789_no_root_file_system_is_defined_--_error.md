---
title: "no root file system is defined -- error"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by arunachalam2 on 2014-12-30
[COLOR=#000000]Hi friends. I am a newbie to ubuntu and I have installed ubuntu 13.10 inside Windows(Wubi).But when I boot into ubuntu I get an error message "[/COLOR][B]no root file system is defined".

[/B]I saw some similar threads in this forum... related to this error... Everyone has asked **To RUN bootinfoscript... **so after running bootinfoscript... i am posting my RESULTS.txt here... Friends please see this and help me. Thanks in advance.

```
 
                 Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


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
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 16424 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848 1,332,027,391 1,331,308,544   7 NTFS / exFAT / HPFS
/dev/sda3       1,332,027,392 1,465,143,295   133,115,904   7 NTFS / exFAT / HPFS




GUID Partition Table detected, but does not seem to be used.


Partition    Start Sector    End Sector  # of Sectors System


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 4010 MB, 4010803200 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7833600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048     7,833,599     7,831,552   b W95 FAT32




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        EE5EA6CA5EA68AC3                       ntfs       System Reserved
/dev/sda2        9892D10492D0E830                       ntfs       
/dev/sda3        E6C46C70C46C44C1                       ntfs       New Volume
/dev/sdb1        505B-20C1                              vfat       UUI


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ubuntu/9892D10492D0E830 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/ubuntu/New Volume fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sdb1/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== StdErr Messages: ===============================


./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-rlOz5WKZ/Tmp_Log: No such file or directory
  No volume groups found

``` 

Friends check this and help me .

---

### Post by QIII on 2014-12-30
Hello!

Two things:

1.  WUBI is no longer maintained.  Although you may be able to install using WUBI on Win 7, it is not recommended.

2.  11.04 is well beyond its End Of Life and is no longer supported.  We would rather that the volunteers here not spend their time and effort providing support for unsupported releases of Ubuntu.  Please see the Staff Recommendations [here]("http://ubuntuforums.org/showthread.php?t=2229730").

---

### Post by arunachalam2 on 2014-12-31
Now i tried UBUNTU 13.10 ..... still the same problem.... please help...

---

### Post by Maximilian_F._Blas on 2014-12-31
You need to install 14.04.1 LTS. and furthermore, its always best to do a dual boot instead of using virtualization which I assume you are using.

---

### Post by hakuna_matata on 2014-12-31
> **arunachalam2 said:**
> Now i tried UBUNTU 13.10 ..... still the same problem.... please help...
13.10 is beyond its End Of Life, too. Do you mean 14.10 ?

For 14.10, it could be [bug 1385930.]("https://bugs.launchpad.net/wubi/+bug/1385930")

So, try to avoid Wubi. 

But if you must use it, it is possible to patch it: [workaround]("http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861"). If you trust me, you can use a patched version, too: [wubi1410.exe]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AABxUTQhS1RHUHuzXl5Zvl5xa/wubi1410.exe?dl=0")

---

### Post by arunachalam2 on 2015-01-01
[FONT=arial]Hi.. I am running Windows 8.... When i try to install UBUNTU 14.10 via USB.... My windows 8.1 is not getting detected during that partition window.... So i ran boot repair... But still i am experiencing the same problem.. So please help..[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Here is my Boot repair URL[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]http://paste.ubuntu.com/9654656/[/FONT]

---

### Post by yancek on 2015-01-01
Your bootrepair link is broken.  Did you select the "Something Else" option when booting the Ubuntu from usb?  From other posts I have read here, you will get problems if you select any other option.  You're not still trying wubi are you as that is definitely not expected to work with windows 8.

---

### Post by hakuna_matata on 2015-01-01
I think, I know your problem:
> ```
GUID Partition Table detected, but does not seem to be used.
```
It is not a Wubi issue. It should be a stray GUID Partition Table (GPT) data. 

You can remove this with [fixparts]("http://www.rodsbooks.com/fixparts/"). fixparts is part of package gdisk
```
sudo apt-get install gdisk
```

```
sudo fixparts /dev/sda
```
and follow the[ tutorial]("http://www.rodsbooks.com/fixparts/"):
> [..] FixParts checks for this condition when it starts. If it finds leftover GPT data, it warns you of this fact and asks you what to do:

  ```
NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):
```
 If you're not sure whether to delete the GPT data, don't do it; type **N**, exit from the program by typing **q** at the main prompt, and investigate further. If you're certain you want to keep just the MBR partitions, go ahead and type **Y**. If the stray GPT data was your only problem, you can then exit from the program by typing **q**, leaving the original MBR partition table untouched, although the errant GPT data will now be gone.



[URL="http://www.rodsbooks.com/fixparts/"]



[/URL][URL="http://www.rodsbooks.com/fixparts/"]

[/URL]

---

