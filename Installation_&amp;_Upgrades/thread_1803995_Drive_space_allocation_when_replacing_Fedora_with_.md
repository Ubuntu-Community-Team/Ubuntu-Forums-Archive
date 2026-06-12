---
title: "Drive space allocation when replacing Fedora with Ubuntu"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Potreaux on 2011-07-14
I am installing Ubuntu on a machine that currently has a dual-boot Windows 7 and Fedora set up. The IT department at my workplace set the machine up, but they don't really give any Linux support beyond installing Fedora.
 
I'd like to replace Fedora with Ubuntu.
 
At the first step of the installation, I am asked to allocate my drive space and am presented with the following list of devices:
 
/dev/sda1  Type: ntfs   Size: 209 MB        Used: 70 MB
/dev/sda2  Type: ntfs   Size: 451941 MB   Used: 69410 MB
/dev/sda3  Type: ext4  Size: 524 MB        Used: 112 MB
/dev/sda5  Type:         Size: 746423 MB   Used: unknown
 
It seems obvious to me that my main Windows partition is on /dev/sda2 and the Windows 7 loader is on /dev/sda1 since they are both NTFS file systems.
 
However, the Fedora setup seems strange to me. I am not sure what purpose the /dev/sda3 device serves and am a little suspicious about the lack of file system type and unkown used disk space on the /dev/sda5 device.
 
How should I allocate my drive space for Ubuntu to replace Fedora and which device should I select for the boot loader installation?

---

### Post by dino99 on 2011-07-14
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by annu2127 on 2011-07-14
Generally it's preferable to keep ur swap partition atleast double of ur RAM space && 5 GB at the max, u can keep more....but then u will be wasting the space....& one ext3/ext4 partition is required for which the mount point should be root (/). & as u already have 2 NTFS Partitions i suggest not to disturb them until u lack on space. :)

---

### Post by Potreaux on 2011-07-14
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)
 
Thanks. I suppose I should have stated that I know how to set up the partitions from tutorials that I have read.
 
Specifically, I want to get advice on what to do with the existing partitions, particularly /dev/sde3.  What is this? Should I delete it and create a new larger swap space?

---

### Post by Potreaux on 2011-07-14
> **annu2127 said:**
> Generally it's preferable to keep ur swap partition atleast double of ur RAM space && 5 GB at the max, u can keep more....but then u will be wasting the space....& one ext3/ext4 partition is required for which the mount point should be root (/). & as u already have 2 NTFS Partitions i suggest not to disturb them until u lack on space. :)
 
Thanks. My instinct was to delete the /dev/sda3 partition (the small 524 MB partition of file type ext4) and create a root partition, swap partition, and home partition. I have 24 GB RAM but am intending to set the swap at 5 GB. I have about 750 GB disk space left after the Windows partition so I can be somwhat liberal with disk space allocations for my partitions. Considering that, what would be good sizes for the root, swap, and home partitons? Particularly is there any reason to go above 12 GB for the root partition as dino99 suggested?

---

### Post by Quackers on 2011-07-14
I suspect it is a separate boot partition but we should check first.

Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Potreaux on 2011-07-14
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97 is installed in the MBR of /dev/sda and looks at sector 
    883141892 on boot drive #1 for the stage2 file.  A stage2 file is at this 
    location on /dev/sda.  Stage2 looks on partition #3 for /grub/grub.conf..

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 has 
                       862009720 sectors, but according to the info from 
                       fdisk, it has 882697967 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

vg_k6786-lv_root': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

vg_k6786-lv_home': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg_k6786-lv_swap': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1199.1 GB, 1199101181952 bytes
255 heads, 63 sectors/track, 145782 cylinders, total 2341994496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   883,109,615   882,697,968   7 NTFS / exFAT / HPFS
/dev/sda3         883,109,888   884,133,887     1,024,000  83 Linux
/dev/sda4         884,133,888 2,341,994,495 1,457,860,608   5 Extended
/dev/sda5         884,135,936 2,341,994,495 1,457,858,560  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/vg_k6786-lv_home 5840763a-a878-47b6-a05c-9cdaffe6be38   ext4       
/dev/mapper/vg_k6786-lv_root 33643afb-572e-4535-ba2c-d33631dc94cb   ext4       _Fedora-14-x86_6
/dev/mapper/vg_k6786-lv_swap 4765b9fa-8632-4629-947b-5170501b6076   swap       
/dev/sda1        BEF4AD6AF4AD259D                       ntfs       System
/dev/sda2        D0B2AE11B2ADFBDA                       ntfs       Windows
/dev/sda3        da0c1008-6cce-4fb8-b862-d65815e14520   ext4       
/dev/sda5        vwQ1OX-Z2KU-wLK9-rFgP-jIUL-scIi-1hzacY LVM2_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
vg_k6786-lv_home
vg_k6786-lv_root
vg_k6786-lv_swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg_k6786-lv_home /home                    ext4       (rw)
/dev/mapper/vg_k6786-lv_root /                        ext4       (rw)
/dev/sda3        /boot                    ext4       (rw)


============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_k6786-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sde
default=0
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.13-92.fc14.x86_64)
    root (hd0,2)
    kernel /vmlinuz-2.6.35.13-92.fc14.x86_64 ro root=/dev/mapper/vg_k6786-lv_root rd_LVM_LV=vg_k6786/lv_root rd_LVM_LV=vg_k6786/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet nouveau.modeset=0 rdblacklist=nouveau
    initrd /initramfs-2.6.35.13-92.fc14.x86_64.img
title Fedora (2.6.35.11-83.fc14.x86_64)
    root (hd0,2)
    kernel /vmlinuz-2.6.35.11-83.fc14.x86_64 ro root=/dev/mapper/vg_k6786-lv_root rd_LVM_LV=vg_k6786/lv_root rd_LVM_LV=vg_k6786/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=no rhgb quiet
    initrd /initramfs-2.6.35.11-83.fc14.x86_64.img
title Fedora (2.6.35.6-45.fc14.x86_64)
    root (hd0,2)
    kernel /vmlinuz-2.6.35.6-45.fc14.x86_64 ro root=/dev/mapper/vg_k6786-lv_root rd_LVM_LV=vg_k6786/lv_root rd_LVM_LV=vg_k6786/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=no rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.x86_64.img
title Windows
    rootnoverify (hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 421.111818314 = 452.165371904  grub/grub.conf                                 2
 421.111818314 = 452.165371904  grub/menu.lst                                  2
 421.114984512 = 452.168771584  grub/stage2                                    1
 421.168413162 = 452.226140160  initramfs-2.6.35.11-83.fc14.x86_64.img         1
 421.152725220 = 452.209295360  initramfs-2.6.35.11-83.fc14.x86_64-nouveau.img  1
 421.201613426 = 452.261788672  initramfs-2.6.35.13-92.fc14.x86_64.img         1
 421.187941551 = 452.247108608  initramfs-2.6.35.13-92.fc14.x86_64-nouveau.img  1
 421.129547119 = 452.184408064  initramfs-2.6.35.6-45.fc14.x86_64.img          2
 421.121621132 = 452.175897600  initrd-plymouth.img                            1
 421.138292313 = 452.193798144  vmlinuz-2.6.35.11-83.fc14.x86_64               1
 421.175708771 = 452.233973760  vmlinuz-2.6.35.13-92.fc14.x86_64               1
 421.111628532 = 452.165168128  vmlinuz-2.6.35.6-45.fc14.x86_64                1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on vg_k6786-lv_root'


Unknown BootLoader on vg_k6786-lv_home'


Unknown BootLoader on vg_k6786-lv_swap'



========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_k6786-lv_root': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/vg_k6786-lv_root': No such file or directory
hexdump: /dev/mapper/vg_k6786-lv_root': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_k6786-lv_home': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/vg_k6786-lv_home': No such file or directory
hexdump: /dev/mapper/vg_k6786-lv_home': Bad file descriptor
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_k6786-lv_swap': No such file or directory
hexdump: stdin: Bad file descriptor.
hexdump: /dev/mapper/vg_k6786-lv_swap': No such file or directory
hexdump: /dev/mapper/vg_k6786-lv_swap': Bad file descriptor
mdadm: No arrays found in config file or automatically

```Thanks Quackers! From what I gather it looks like your suspicion was correct.

What is the best way to go about formatting/repartitioning my hard drive and replacing Fedora with Ubuntu?

---

### Post by Quackers on 2011-07-14
Yes, sda3 is a separate boot partition. This is not normally needed, however, it appears you are using LVM (Logical Volume Manager) which could need a separate boot partition. I just don't know enough about LVM or even how to disable/remove it, so am not prepared to lead you astray :-)
Maybe you could contact your IT guy and ask whether LVM is needed and what you should do about it if it isn't.
Alternatively you could google and see what turns up.
Sorry I can't be more help than that.

---

### Post by Potreaux on 2011-07-14
Well, thanks for trying. At least I learned a few things about my boot setup. It is vacation season so I doubt I'll hear from IT until September :(  But now I'm glad I didn't go messing with my boot setup before I knew what was happening.

---

