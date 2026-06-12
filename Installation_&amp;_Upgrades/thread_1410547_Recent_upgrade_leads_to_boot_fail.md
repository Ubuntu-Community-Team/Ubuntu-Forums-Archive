---
title: "Recent upgrade leads to boot fail"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by rev9ers on 2010-02-18
Recently upgraded through Update Manager and on reboot Toshiba laptop no longer loads regular ubuntu GUI. 

Instead, it boots to <sh grub> or something similar with unfamiliar commands. Am now booted up on Ubuntu 9.10 livecd. 

I am pretty new at this, so specific help would be very appreciated.

Here's the output from a Boot Info Script I found on another thread:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x839a839a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b7b651a6-aff5-4471-8133-5fd55f73d66b   ext4                                     
/dev/sda1        FCD44ABBD44A77C2                       ntfs       The Home of Data              

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"


Thanks Y'all.

---

### Post by lidex on 2010-02-19
Have a look at this page:
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by meierfra. on 2010-02-20
Try this first:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

But since the script was not able to mount Wubi, you might  also have to run a file system check.
Boot from the Ubuntu LiveCD and

```
sudo mount /dev/sda1 /mnt
sudo e2fsck -fyv /mnt/ubuntu/disks/root.disk
```

If e2fsck  found some errors, run the last command again.

---

