---
title: "Installing on ext HDD"
date: 2024-03-17
forum: Installation &amp; Upgrades
---

### Post by larryb1607 on 2024-03-17
I have a 1 TB USB ext HDD.  I created a partition on it sdc 7 to install Ubuntu Cinnamon on.    I already have a ubuntu based disto installed om sdc5 & 6.  Grub appears to be installed as I get a choice of different kernels and Windows which is on my laptop.  I plan to move away from the old distro slowly as I migrate data into it.  When I try doing the install it asks me where to put the boot files.  I am not really sure where these are located.  I tried running some commands I found on the internet for showing the boot device, but none of the results actually had boot in the descriptions. generated.  I have Ubuntu Cinnamon on a USB stick and that boots fine.  Most of the rest of the USB HDD is for backups.

---

### Post by yancek on 2024-03-17
The image of your drive from gparted shows sdc7 as an ntfs filesystem on that partition.  That won't work for starters, you need a Linux filesystem.  If you intend to keep this new install and later drop the others on sdc5 and sdc6, you can install Grub to the MBR of that drive.  You should see device for bootloader installation in the main windows when installing Ubuntu and that should give you the option of /dev/sdc.  If you do that, you will need to set that drive to first boot priority in the BIOS. If you have other systems on other drives and boot from them, you will new to decide what to do since you haven't posted any details on that.  Your grub for the other Ubuntu's may be another drive and that is something only you would know since you did the installs.  You could run boot repair and just use the Create BootInfo Summary option to get that information.  Make sure you do not select to make any changes.

---

### Post by larryb1607 on 2024-03-18
Not sure how to do the boot repair as you suggest.  I believe that when I finally do install, I have the option to format the specified partition as I choose.  Thanks fr the reply

---

### Post by yancek on 2024-03-18
Go to the boot repair page at the link below from one of your functioning installs and use the 2nd option explained on that page as it is more up to date.  You should see an option to select Create Bootinfo summary when boot repair starts.  Do that and when it finishes it will give you the option to upload to pastebin and give you a link to post here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by larryb1607 on 2024-03-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/focal/InRelease](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/focal/InRelease)  503  Service Unavailable [IP: 185.125.190.80 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
 larrypc &#57520; ~ &#57520; sudo apt install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
 larrypc &#57520; ~ &#57520; 100 &#57520; 

it appears it did not work

---

### Post by yancek on 2024-03-20
Don't know what the problem would be.  Did you try multiple times just in case the server is down?

---

### Post by larryb1607 on 2024-03-23
boot-repair-4ppa2075                                              [20240323_1555]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sdc1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdc7 starts 
                       at sector 128. But according to the info from fdisk, 
                       sdc7 starts at sector 172585088.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


================================ 3 OS detected =================================

OS#1:   The OS now in use - Ubuntu 20.04.6 LTS on sdc5
OS#2:   Windows 7 (boot) on sda2
OS#3:   Windows 7 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 3rd Gen Core processor Graphics Controller from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.4.0-174-generic root=UUID=7143b8d5-260d-42cc-b24b-c1f963d1a305 ro quiet splash vt.handoff=7
df -Th / : /dev/sdc5      ext4   28G   11G   16G  41% /

===================================== UEFI =====================================

BIOS/UEFI firmware: A13 from Dell Inc.
This installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sdc    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2046 sectors * 512 bytes
sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    63 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sdc5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ng,    update-grub,    not-far
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda7    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc7    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sdc5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda7    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc7    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sdc5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdc
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda7    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdc2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc7    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdb1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sdb: 29.84 GiB, 32017047552 bytes, 62533296 sectors
Disk identifier: 0x6ffdaf18
     Boot Start      End  Sectors Size Id Type
sdb1        2048 16775167 16773120   8G 84 OS/2 hidden or Intel hibernation
Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x0001fb10
     Boot     Start       End   Sectors   Size Id Type
sda1              63     80324     80262  39.2M de Dell Utility
sda2           81920  58101759  58019840  27.7G  7 HPFS/NTFS/exFAT
sda3  *     58101760 359698431 301596672 143.8G  7 HPFS/NTFS/exFAT
sda4       359700417 976764927 617064511 294.2G  f W95 Ext'd (LBA)
sda5       359700480 486510591 126810112  60.5G  7 HPFS/NTFS/exFAT
sda6       486512640 527470591  40957952  19.5G  b W95 FAT32
sda7       527472640 976764927 449292288 214.2G  7 HPFS/NTFS/exFAT
Disk sdc: 931.49 GiB, 1000170586112 bytes, 1953458176 sectors
Disk identifier: 0x6416a379
     Boot     Start        End    Sectors   Size Id Type
sdc1            2046  293416959  293414914 139.9G  f W95 Ext'd (LBA)
sdc2       293417088 1953458111 1660041024 791.6G  7 HPFS/NTFS/exFAT
sdc5            2048   60000255   59998208  28.6G 83 Linux
sdc6        60002304  172584959  112582656  53.7G 83 Linux
sdc7       172585088  293416959  120831872  57.6G  7 HPFS/NTFS/exFAT
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:msdos:ATA ST500LT012-9WS14:;
1:32.3kB:41.1MB:41.1MB:fat16::diag;
2:41.9MB:29.7GB:29.7GB:ntfs::;
3:29.7GB:184GB:154GB:ntfs::boot;
4:184GB:500GB:316GB:::lba;
5:184GB:249GB:64.9GB:ntfs::;
6:249GB:270GB:21.0GB:fat32::;
7:270GB:500GB:230GB:ntfs::;
sdb:32.0GB:scsi:512:512:msdos:ATA SAMSUNG SSD PM83:;
1:1049kB:8589MB:8588MB:::irst;
sdc:1000GB:scsi:512:512:msdos:WD Elements 10A8:;
1:1048kB:150GB:150GB:::lba;
5:1049kB:30.7GB:30.7GB:ext4::;
6:30.7GB:88.4GB:57.6GB:ext4::;
7:88.4GB:150GB:61.9GB:ntfs::;
2:150GB:1000GB:850GB:ntfs::;

Free space >10MiB: ______________________________________________________________

sdb: 8191MiB:30534MiB:22343MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE          UUID                                 PARTUUID                             LABEL      PARTLABEL
sda    isw_raid_member                                                                                      
&#9500;&#9472;sda1 vfat            5450-4444                            0001fb10-01                                     
&#9500;&#9472;sda2 ntfs            4E30C3EF30C3DC59                     0001fb10-02                          RECOVERY   
&#9500;&#9472;sda3 ntfs            3448C71648C6D630                     0001fb10-03                          OS         
&#9500;&#9472;sda4                                                      0001fb10-04                                     
&#9500;&#9472;sda5 ntfs            01D6AA41EF5AF4C0                     0001fb10-05                          L          
&#9500;&#9472;sda6 vfat            865C-8A44                            0001fb10-06                          NEW VOLUME 
&#9492;&#9472;sda7 ntfs            8C689D01689CEAEA                     0001fb10-07                          New Volume 
sdb    isw_raid_member                                                                                      
&#9492;&#9472;sdb1                                                      6ffdaf18-01                                     
sdc                                                                                                         
&#9500;&#9472;sdc1                                                      6416a379-01                                     
&#9500;&#9472;sdc2 ntfs            92A816A5A81687BD                     6416a379-02                          G          
&#9500;&#9472;sdc5 ext4            7143b8d5-260d-42cc-b24b-c1f963d1a305 6416a379-05                                     
&#9500;&#9472;sdc6 ext4            5e840212-391d-4052-ad88-244b25d2be9f 6416a379-06                                     
&#9492;&#9472;sdc7 ntfs            92A816A5A81687BD                     6416a379-07                          H          

Mount points (filtered): _______________________________________________________

             Avail Use% Mounted on
/dev/sda1      39M   0% /mnt/boot-sav/sda1
/dev/sda2    12.6G  55% /mnt/boot-sav/sda2
/dev/sda3    84.3G  41% /mnt/boot-sav/sda3
/dev/sda5      50G  17% /mnt/boot-sav/sda5
/dev/sda6    19.5G   0% /mnt/boot-sav/sda6
/dev/sda7     100G  53% /mnt/boot-sav/sda7
/dev/sdc2   700.8G  11% /mnt/boot-sav/sdc2
/dev/sdc5    15.7G  39% /
/dev/sdc6    31.3G  35% /home
/dev/sdc7    57.5G   0% /mnt/boot-sav/sdc7

Mount options (filtered): ______________________________________________________

/dev/sda1   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda3   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda6   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda7   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc2   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc5   ext4            rw,relatime,errors=remount-ro
/dev/sdc6   ext4            rw,relatime
/dev/sdc7   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096

====================== sdc5/boot/grub/grub.cfg (filtered) ======================

Linux Lite GNU/Linux   7143b8d5-260d-42cc-b24b-c1f963d1a305
Windows 7 (on sda2)   4E30C3EF30C3DC59
Windows 7 (on sda3)   3448C71648C6D630
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sdc5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdg5 during installation
UUID=7143b8d5-260d-42cc-b24b-c1f963d1a305 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdg6 during installation
UUID=5e840212-391d-4052-ad88-244b25d2be9f /home           ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0

======================= sdc5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='Linux Lite'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/boot/grub_linux_lite.png"

==================== sdc5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  16.208488464 = 17.403731968   boot/grub/grub.cfg                             1
   8.262863159 = 8.872181760    boot/grub/i386-pc/core.img                     1
  12.732471466 = 13.671387136   boot/vmlinuz                                   2
   7.349658966 = 7.891636224    boot/vmlinuz-5.4.0-173-generic                 1
  12.732471466 = 13.671387136   boot/vmlinuz-5.4.0-174-generic                 2
   7.349658966 = 7.891636224    boot/vmlinuz.old                               1
  15.024040222 = 16.131940352   boot/initrd.img                                5
   5.780654907 = 6.206930944    boot/initrd.img-5.4.0-173-generic              8
  15.024040222 = 16.131940352   boot/initrd.img-5.4.0-174-generic              5
   5.780654907 = 6.206930944    boot/initrd.img.old                            8

===================== sdc5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Jan 11  2022 10_linux
-rwxr-xr-x 1 root root 42359 Aug 17  2020 10_linux_zfs
-rwxr-xr-x 1 root root 13101 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 12059 Dec 14  2019 30_os-prober
-rwxr-xr-x 1 root root  1424 Feb 26  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 14  2019 40_custom
-rwxr-xr-x 1 root root   216 Dec 14  2019 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to reset grubenv) and reinstall the grub2 of
sdc5 into the MBR of sdc.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on sdc (WD Elements 10A8) disk!

---

### Post by yancek on 2024-03-24
If you want to install the new Ubuntu release to sdc7, make sure you format that partition with a Linux filesystem (ext4 is default).  This will overwrite anything currently on that partition so if there is data on that ntfs partition now, back it up to another location.  Grub according to boot repair is installed in the MBR of sdc and points to the other Grub files on sdc5.  When you install Ubuntu to sdc7, select the option device for bootloader installation as sdc.  Grub should (or may) run update-grub at the end of the install and add entries for the other OS(s).  If that doesn't happen, you need to boot the new install, make sure os-prober is enabled and run update-grub.

I would suggest that before you begin the install you run the command:  sudo fdisk -l to list the drives and partitions as the install USB may show itself as sda.  You can see which drive is sdc by the size, 1TB which is the only 1TB drive you have.  It may not show as sdc.

---

### Post by larryb1607 on 2024-04-10
Created 2 partition out of sdc7.  Installed Ubuntu Cinnamon mount point / on sdc8 and /home on sdc7.  I was at a loss as to how or where to put the boot files so I used the command ubiquity-b to skip the boot install.  Should I rerun the boot repair app or is there an easier way to fix GRUB so it also sees the Ubuntu Cinnamon install?  Yje Linux Lite is still shown in the boot menu and boots fine.

thanks

---

