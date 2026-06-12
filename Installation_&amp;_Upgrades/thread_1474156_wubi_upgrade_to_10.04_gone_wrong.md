---
title: "wubi upgrade to 10.04 gone wrong"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by oscillate on 2010-05-05
Hi, 

I really hope someone can help me with this. I have two disks in my machine, the larger main  disk has my Windows XP installation and the secondary disk has an older XP installation I don't boot to and a partition I made to hold an ubuntu install. I installed 9.10 using wubi and everything was going fine. After trying to upgrade last night, I'm now stuck at the "grub rescue>" prompt when booting up.

I was upgrading to 10.04 last night and the installation hung for hours at a point where it said '14 minutes remaining'. I had to restart, at which point I could not get back into ubuntu. I entered the recovery mode and selected 'fix broken packages', in that process the grub installer asked me where to install, I did not know which partition was the right one for it to go on and selected all (thanks, helpful message). Now on a fresh boot it immediately goes to the "grub rescue>" prompt and that's where I am.


[LIST]
[*]My goal is to get a couple of files out of my ubuntu filesystem and be able to reboot back into windows.
[/LIST]
 
I have burned half a dozen 10.04 live cds and none of them work, I keep getting the same issue: tons of "Input/output error"s and nothing works. (grep, rm, sed, chroot, anything & everything), finally ending with "Target filesystem doesn't have /sbin/init"...

I've found an old ubuntu7 disk and am using that.

I followed the instructions on [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector) , ran testdisk up to 'BackupBS'. Rebooted to primary hard drive, with exact same problem as before: "grub rescue>" prompt.

Went back into livecd. Trying to loopmount wubi install and get this message: 
```
sudo mount -o loop /media/nix/ubuntu/disks/root.disk /mnt
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
dmesg says: ```
dmesg | tail
[  839.409659] hdc: error code: 0x70  sense_key: 0x03  asc: 0x11  ascq: 0x05
[  839.409664] end_request: I/O error, dev hdc, sector 1425016
[  839.409668] Buffer I/O error on device hdc, logical block 356254
[  839.409672] Buffer I/O error on device hdc, logical block 356255
[ 1077.601010] EXT3-fs: loop1: couldn't mount because of unsupported optional features (240).
[ 1815.467031] EXT3-fs: loop1: couldn't mount because of unsupported optional features (240).
[ 2442.471732] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[ 2442.471739] hdc: drive_cmd: error=0x04 { AbortedCommand }
[ 2442.471741] ide: failed opcode was: 0xec
[ 2957.952351] EXT3-fs: loop1: couldn't mount because of unsupported optional features (240).
```

I ran the bootinfoscript and get the following output:

```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/hda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/hdb and looks on the same drive in 
    partition #256 for /boot/grub.

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

hdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of hdb1 and 
                       looks at sector 332448 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

hdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of hdb2 and 
                       looks at sector 332448 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

hdb2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


hdc: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29ab29aa

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63   781,401,599   781,401,537   7 HPFS/NTFS


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x17641764

Partition  Boot         Start           End          Size  Id System

/dev/hdb1    *             63   213,937,604   213,937,542   7 HPFS/NTFS
/dev/hdb2         213,937,605   234,436,544    20,498,940   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        2A5C23345C22F9E9                       ntfs                                     
/dev/hdb1        60B834A1B834781C                       ntfs                                     
/dev/hdb2        D0D83DF0D83DD606                       ntfs       nix                           
/dev/hdc                                                iso9660    Ubuntu 7.10 i386              
/dev/loop1       64db5211-88e1-458d-b587-7dc7529b682c   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hda1        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ hda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

================================ hdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 
```Should I try running lilo at this point?

Thanks so much in advance.

---

### Post by oscillate on 2010-05-05
Could the loopmount error be from using an old ubuntu livecd? If I can just get a few files out of that ubuntu install and get my windows boot back, I would consider that a success.

EDIT: Incidentally, I am able to use one of the ubuntu 10.04 live cds on my vista laptop, but I get all those errors and an unsuccessful boot in the WinXP machine. Could that be a dvd issue? I've tried removing each of my RAM sticks to see if that works, but it still won't boot with that live cd...

EDIT1: Ran ```
 sudo ./lilo -M /dev/hda mbr
/boot/boot.0300 exists - no /dev/hda backup copy made.
The Master Boot Record of  /dev/hda  has been updated.

```
Rebooting now...

---

