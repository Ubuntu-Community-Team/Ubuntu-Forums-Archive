---
title: "Cannot Reinstall Dual Boot Ubunto with Windows 7"
date: 2018-11-29
forum: Installation &amp; Upgrades
---

### Post by josephconvert on 2018-11-29
I have Windows 7 dual booting with Ubuntu. A Ubuntu upgrade went wrong and could not be mended.
 
 
 So I followed instructions from Ubuntu forums to remove Ubuntu so that I could reinstall it with the latest version. I removed the Ubuntu partitions and then mended Windows boot with the Windows repair disk. This let me boot directly into Windows 7.
 
 
 I left the empty space where Ubuntu had been so that I could reinstall it there, on the same hard drive as Windows 7.
 
 
 So I booted into the Ubuntu live DVD and when it was loaded I clicked on Install Ubuntu. I followed the steps until it said there was no operating system on the computer, and it gave the optin to either install on the used partitions, or in the free space.
 
 
 I stopped at this point because it could not find Windows 7 to install alongside.  
 
 
 I have looked at the forums for a solution to this problem but found none. One talks of UEFI but my computer is old and does not have UEFI but the old BIOS.  
 
 
 I am assuming that although the Windows MBR is restored, the boot partition still has something Grub left behind, which is why the new install of Ubuntu cannot detect Windows 7.
 
 
 I have SuperGrub 2 live CD and this detects Windows 7 and lets me boot from it.  
 
 
 Help for this problem would be appreciated.

---

### Post by oldfred on 2018-11-29
Is Windows hibernated. With Windows 7 you have to do that, where Windows 8 or 10 turns on fast start up which is hibernation automatically.
Did you convert Windows 7 partitions from basic to dynamic?

Post these from Ubuntu live installer:
sudo parted -l
sudo fdisk -lu

---

### Post by josephconvert on 2018-11-29
Thank you. When I fist installed Ubuntu I did not hibernate Widnows 7. I simply left space on the hard drive and booted from Ubuntu Live CD and installed with no problems. I did not convert Windows 7 in any way. It is all the same as when I first installed Ubuntu. The only difference is that after removing the Ubuntu partians and leaving empty space again, the install from Ubuntu Live cannot detect Windows 7. 

I suspect something from the old install is still in the boot sector, maybe part of Grub, and this is confusing the detection. As I said before, if I boot from SuperGrub Live CD is finds Windows 7 straight away and lets me boot into it.

My question is, how can I restore the Windows 7 boot partition to what it was before ever dual booting? I suspect if that were done, the Ubuntu Live CD would detect Windows 7.

Will get back with resulst from 
sudo parted -l
sudo fdisk -lu

---

### Post by josephconvert on 2018-11-29
Here are the results of the two commands:

```
mint@mint:~$ sudo fdisk -lu
 Disk /dev/loop0: 1.7 GiB, 1859526656 bytes, 3631888 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0xe515b4d6
 
 
 Device     Boot      Start        End    Sectors   Size Id Type
 /dev/sda1  *          2048 1324061234 1324059187 631.4G  7 HPFS/NTFS/exFAT
 /dev/sda2       1324062718 1953523711  629460994 300.2G  5 Extended
 
 Partition 2 does not start on physical sector boundary.

 Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x0008d2ad
 
 
Device     Boot     Start       End   Sectors   Size Id Type
 /dev/sdb1           16126 976768064 976751939 465.8G  f W95 Ext'd (LBA)
 /dev/sdb5           16128 254117026 254100899 121.2G  7 HPFS/NTFS/exFAT
 /dev/sdb6       254132298 717591419 463459122   221G  7 HPFS/NTFS/exFAT
 /dev/sdb7  *    717591483 976768064 259176582 123.6G  7 HPFS/NTFS/exFAT
 
Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0xbf9bbf9b
 
 
Device     Boot Start       End   Sectors   Size Id Type
 /dev/sdc1  *     2048 976773119 976771072 465.8G  7 HPFS/NTFS/exFAT

Disk /dev/sdd: 29.2 GiB, 31376707072 bytes, 61282631 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x00000000
 
Device     Boot Start      End  Sectors  Size Id Type
 /dev/sdd1          32 61282630 61282599 29.2G  c W95 FAT32 (LBA)
 mint@mint:~$ 
``` 
 
 
 I was not sure if this command was a letter &#8216;l&#8217; or a number &#8216;1&#8217;. Here are the results form both.
 
 
 ```
mint@mint:~$ sudo parted -1
 parted: invalid option -- '1'
 Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]
 mint@mint:~$  
```
 
 
 
 
 ```
mint@mint:~$ sudo parted -l
 Error: Invalid partition table on /dev/sda -- wrong signature 0.
 Ignore/Cancel?
```

---

### Post by QIII on 2018-11-29
Are you using Mint or Ubuntu?

Also:  Please enclose all terminal commands and their results in code tags.  This preserves formatting and makes your posts easier to read.

To use code tags, either --

1. Click the # button above the text entry box, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2. Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by oldfred on 2018-11-29
It is el, not one, capital I.
Are you installing Mint? There is a separate sub-forum for Mint as it is not exactly Ubuntu. I can move thread if so.

Do not see anything there.
Can you partition in advance with gparted?
If Windows needs chkdsk that also can prevent Linux NTFS driver from seeing the NTFS partition.
Also gparted may show a red or yellow icon on NTFS if issues. Clicking on icon may tell more about what issue is.

---

### Post by josephconvert on 2018-11-29
Thank you for your help. I have run checkdisk and it found no errors.

I have the same issue with Ubuntu and with Mint. I used Mint live CD to followyou instructions because it loads faster than Ubuntu.

I might try formatting the empty space on the drive left when removing the Ubuntu partitions and see if that make a difference.

---

### Post by josephconvert on 2018-11-30
The SuperGrup Live CD gave me this information which may show what the problem is:

 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]

```

============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub in partition 6.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp ext2 part_msdos
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,324,061,234 1,324,059,187   7 NTFS / exFAT / HPFS
/dev/sda2       1,324,062,718 1,953,523,711   629,460,994   5 Extended
Invalid MBR Signature found.
Empty Partition.


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1              16,126   976,768,064   976,751,939   f W95 Extended (LBA)
/dev/sdb5              16,128   254,117,026   254,100,899   7 NTFS / exFAT / HPFS
/dev/sdb6         254,132,298   717,591,419   463,459,122   7 NTFS / exFAT / HPFS
/dev/sdb7    *    717,591,483   976,768,064   259,176,582   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   976,773,119   976,771,072   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8422825722824DDC                       ntfs       New Volume
/dev/sdb5        01CB880F3EE23450                       ntfs       DATA
/dev/sdb6        01CB880F92E131F0                       ntfs       DATA2
/dev/sdb7        01CB93ADA675E2C0                       ntfs       DATA3
/dev/sdc1        1A2815222814FF07                       ntfs       
/dev/sr0         2017-10-29-00-56-18-00                 iso9660    Boot-Repair-Disk 64bit
/dev/zram0       5ea6e8e2-af27-415f-bb5e-4e80712b7c3e   swap       
/dev/zram1       3e5ac8f9-af5f-4e76-8ae1-b4e345861f84   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Nov 29 10:51 ata-Optiarc_DVD_RW_AD-7260S -> ../../sr0
lrwxrwxrwx 1 root root  9 Nov 29 10:56 ata-ST1000DX001-1CM162_Z1DAF2BX -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST1000DX001-1CM162_Z1DAF2BX-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST1000DX001-1CM162_Z1DAF2BX-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Nov 29 10:56 ata-ST3500418AS_5VMJ5M4L -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST3500418AS_5VMJ5M4L-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST3500418AS_5VMJ5M4L-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST3500418AS_5VMJ5M4L-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST3500418AS_5VMJ5M4L-part7 -> ../../sdb7
lrwxrwxrwx 1 root root  9 Nov 29 10:56 ata-ST3500418AS_6VMPGWBV -> ../../sdc
lrwxrwxrwx 1 root root 10 Nov 29 10:56 ata-ST3500418AS_6VMPGWBV-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Nov 29 10:56 wwn-0x5000c5002ba68b35 -> ../../sdc
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c5002ba68b35-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Nov 29 10:56 wwn-0x5000c5002bc2eb16 -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c5002bc2eb16-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c5002bc2eb16-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c5002bc2eb16-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c5002bc2eb16-part7 -> ../../sdb7
lrwxrwxrwx 1 root root  9 Nov 29 10:56 wwn-0x5000c50066620525 -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c50066620525-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 29 10:56 wwn-0x5000c50066620525-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
--------------------------------------------------------------------------------


ADDITIONAL INFORMATION :
=================== log of boot-info 20181129_1056 ===================
boot-info version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4
Error: Invalid partition table on /dev/sda -- wrong signature 0.
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.
Partition 2 does not start on physical sector boundary.
boot-info is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda1:Windows 7:Windows:chain
/dev/sdc1:Microsoft Windows XP Professional:Windows1:chain

=================== blkid:
/dev/sda1: LABEL="New Volume" UUID="8422825722824DDC" TYPE="ntfs" PARTUUID="e515b4d6-01"
/dev/sdb5: LABEL="DATA" UUID="01CB880F3EE23450" TYPE="ntfs" PARTUUID="0008d2ad-05"
/dev/sdb6: LABEL="DATA2" UUID="01CB880F92E131F0" TYPE="ntfs" PARTUUID="0008d2ad-06"
/dev/sdb7: LABEL="DATA3" UUID="01CB93ADA675E2C0" TYPE="ntfs" PARTUUID="0008d2ad-07"
/dev/sdc1: UUID="1A2815222814FF07" TYPE="ntfs" PARTUUID="bf9bbf9b-01"
/dev/sr0: UUID="2017-10-29-00-56-18-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="6b8b4567" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/zram0: UUID="5ea6e8e2-af27-415f-bb5e-4e80712b7c3e" TYPE="swap"
/dev/zram1: UUID="3e5ac8f9-af5f-4e76-8ae1-b4e345861f84" TYPE="swap"


2 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Partition 2 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda1.
sdb5    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sdb5.
sdb6    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sdb6.
sdb7    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sdb7.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sdc1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:unknown:ATA ST1000DX001-1CM1:;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA ST3500418AS:;
1:8257kB:500GB:500GB:::lba;
5:8258kB:130GB:130GB:ntfs::;
6:130GB:367GB:237GB:ntfs::;
7:367GB:500GB:133GB:ntfs::boot;

BYT;
/dev/sdc:500GB:scsi:512:512:msdos:ATA ST3500418AS:;
1:1049kB:500GB:500GB:ntfs::boot;

BYT;
/dev/zram1:1035MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1035MB:1035MB:linux-swap(v1)::;

BYT;
/dev/sr0:742MB:scsi:2048:2048:unknown:Optiarc DVD RW AD-7260S:;

BYT;
/dev/zram0:1035MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1035MB:1035MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs 629.3M
sda   disk          931.5G
sda1  part ntfs     631.4G New Volume
sda2  part              1K
sdb   disk          465.8G
sdb1  part              1K
sdb5  part ntfs     121.2G DATA
sdb6  part ntfs       221G DATA2
sdb7  part ntfs     123.6G DATA3
sdc   disk          465.8G
sdc1  part ntfs     465.8G
sr0   rom  iso9660    708M Boot-Repair-Disk 64bit
zram0 disk            987M
zram1 disk            987M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sdb      1  0  0 running
sdb1     1  0  0
sdb5     1  0  0         /mnt/boot-sav/sdb5
sdb6     1  0  0         /mnt/boot-sav/sdb6
sdb7     1  0  0         /mnt/boot-sav/sdb7
sdc      1  0  0 running
sdc1     1  0  0         /mnt/boot-sav/sdc1
sr0      1  0  1 running /cdrom
zram0    0  0  0         [SWAP]
zram1    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1961292k,nr_inodes=490323,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=404292k,mode=755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12064)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=404288k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb5 on /mnt/boot-sav/sdb5 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb6 on /mnt/boot-sav/sdb6 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb7 on /mnt/boot-sav/sdb7 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvb dvd dvdrw ecryptfs fb0 fd full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdb5 sdb6 sdb7 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  32 8a eb 4e 00 00 00 00  |........2..N....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  dc 4d 82 22 57 82 22 84  |.........M."W.".|
00000050  7e 1d 20 66 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |~. f.3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  98 45 25 0f 00 00 00 00  |.........E%.....|
00000030  03 00 00 00 00 00 00 00  59 54 f2 00 00 00 00 00  |........YT......|
00000040  f6 00 00 00 01 00 00 00  50 34 e2 3e 0f 88 cb 01  |........P4.>....|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  31 d3 9f 1b 00 00 00 00  |........1.......|
00000030  03 00 00 00 00 00 00 00  33 fd b9 01 00 00 00 00  |........3.......|
00000040  f6 00 00 00 01 00 00 00  f0 31 e1 92 0f 88 cb 01  |.........1......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  85 b8 72 0f 00 00 00 00  |..........r.....|
00000030  03 00 00 00 00 00 00 00  88 2b f7 00 00 00 00 00  |.........+......|
00000040  f6 00 00 00 01 00 00 00  c0 e2 75 a6 ad 93 cb 01  |..........u.....|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 38 3a 00 00 00 00  |.........W8:....|
00000030  00 00 0c 00 00 00 00 00  5a 1d 0c 00 00 00 00 00  |........Z.......|
00000040  f6 00 00 00 01 00 00 00  07 ff 14 28 22 15 28 1a  |...........(".(.|
00000050  99 4c 11 ed fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.L...3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200
Partition 2 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     395M  6.3M  389M   2% /run
/dev/sr0       iso9660   708M  708M     0 100% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   2.0G   10M  2.0G   1% /
tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.0G  104K  2.0G   1% /tmp
tmpfs          tmpfs     395M  4.0K  395M   1% /run/user/999
/dev/sda1      fuseblk   632G  240G  392G  38% /mnt/boot-sav/sda1
/dev/sdb5      fuseblk   122G   89G   33G  74% /mnt/boot-sav/sdb5
/dev/sdb6      fuseblk   221G  176G   46G  80% /mnt/boot-sav/sdb6
/dev/sdb7      fuseblk   124G   88G   37G  71% /mnt/boot-sav/sdb7
/dev/sdc1      fuseblk   466G  415G   52G  89% /mnt/boot-sav/sdc1

=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe515b4d6

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1324061234 1324059187 631.4G  7 HPFS/NTFS/exFAT
/dev/sda2       1324062718 1953523711  629460994 300.2G  5 Extended



Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008d2ad

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1           16126 976768064 976751939 465.8G  f W95 Ext'd (LBA)
/dev/sdb5           16128 254117026 254100899 121.2G  7 HPFS/NTFS/exFAT
/dev/sdb6       254132298 717591419 463459122   221G  7 HPFS/NTFS/exFAT
/dev/sdb7  *    717591483 976768064 259176582 123.6G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbf9bbf9b

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1  *     2048 976773119 976771072 465.8G  7 HPFS/NTFS/exFAT


Disk /dev/zram0: 987 MiB, 1034985472 bytes, 252682 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 987 MiB, 1034985472 bytes, 252682 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2018-11-30
Please use code tags for long text or terminal output.
Easy to add with Forum's advanced editor and # icon.

You show no Linux partitions, and have a partition error on sda.

Major Windows updates in BIOS mode including Windows 7, 8 or 10 all have a "feature" (really bug). They delete from the partition table any Linux partitions. It is because they do not see them, so do not write them back into partition table. Partition is still there and usually can be restored with testdisk or parted rescue. But better if you have backup of partition table or output of details of partition sizes.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

All these are essentially the same.
      
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition) 
    
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
Screenshots of several of the recovery tools
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by josephconvert on 2018-12-01
Thank you for your help. Since I have a working Windows 7 I have decided to use Ubuntu in VirtualBox rather than reinstall it using dual boot. Dual Boot seems to cause a lot of problems when it gows wrong, so I feel it is better not to use it at all. The fixes you suggest I make are too complicated for me to undertake for the end I am seeking. But thank you for the trouble you have taken.

---

