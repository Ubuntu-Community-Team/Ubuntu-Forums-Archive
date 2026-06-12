---
title: "HP Gen 8 G1610T - Cannot install Ubuntu and boot. Really Frustrating"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by seanbw2 on 2016-06-08
Background
I have searched the boards and it appears I am in my own pickle.
My setup is as follows: HP Gen 8 G1610T Proliant server with five disks as follows /dev/sda, /dev/sdb, /dev/sdc, /dev/sdd and /dev/sdg. /dev/sdg is a 320GB hard disk whilst dev/sda to d are each 4TB HDD. There is an option in the Gen 8 server that allows the pc to boot from /dev/sdg and that is the option I wanted to exercise by installing ubuntu into /dev/sdg.
However at the last option to install the bootloader and finish the installation, I hit the brickwall with I cannot install the boot loader to the area specified. I am given three options and I can't get out of any unless I reboot. 
Option 1 is to choose another from the other hard disks and whichever I choose, the system won't accept. It just sticks there until I  reboot. 
Option 2 is to continue without a bootloader and even if I choose that it still stay stuck. 
Option 3 is to cancel the installation and even that sticks. 
So the real option is to ctrl+alt+del. Fast forward a day and a half and I am about to give up so here I am giving up ;)

My Plan
I have 4 x 4TB hard disks that I want to pool so I really don't want any system on them so preferably I will like to boot and keep all my system files to dev/sdg which is my fifth disk= 320GB hard disk.

Problem statement (as I see it)
Ubuntu installs to /dev/sdg but want to boot from /dev/sda (which is OK with me) but somehow it confuses itself and me because it initally installs to /dev/sdg but can't seem to boot from there but does not find all its files wherever it installed to. So for the past days I have been confronted with a grub rescue prompt which refuses to read from (hd1,gpt2) or whatever that is so I eventually removed all disks apart from these five and the sd card I am installing from.

How can I get past this considering the following:
[LIST=1]
[*]Booting from the SD card succeeds but I can't install into it so I need to install to /dev/sdg
[*]I can't seem to install and boot from /dev/sdg nor can I install and boot from /dev/sda (I have tried. I get a grub rescue prompt)
[*]I can run and update anything using the live cd but once I reboot - they disappear and I am back to the starting point.
[*]HP gen 8 G1610T prefers to boot from the SD card but I can't install to it and in any case I want to boot to /dev/sdg. The SD card is /dev/sdf.
[/LIST]

Solution Required (from You All)
How can I install the boot loader to /dev/sdg considering that I can't install from the live cd permanently? Currently I am in the live CD and I need your assistance.
I will post this and then paste the output of blkid from the server itself.

---

### Post by oldfred on 2016-06-08
Is this an UEFI system or BIOS.
If BIOS the install to sdg when partitioning sdg should work. But you then have to set BIOS to boot sdg.

But if UEFI, grub only installs to sda's ESP - efi system partition. The only way I have gotten it to install to sdb or a full install to a flash drive was to afterwards copy sda's ESP to sdb's ESP. And if internal drive, which I have not configured to directly boot, you would have to add a new entry to UEFI's NVRAM.

Can you temporarily disconnect the other 4 drives so you only have one as sda?
And is it sda, or is installer sda?

---

### Post by seanbw2 on 2016-06-08
I think it is a bios pc. Reason I say so is because I hae looked at the syslog and can find no massive mention of EFI.
I will google a test to check for EFIness. 
I can take the three other disks out but the problem as I saw it was a way to install thebootloader and make it sticky using the live cd as I am using now.
I have now taken the three hdd out but I still don't know how to make the sudo grub-update code sticky.

You lost me here: And is it sda, or is installer sda? 
The installer is actually an sd card at /de/sdf.
```

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda2  ext4             (not mounted)  2fdc85b0-4f3a-454d-93fa-85c02fe26185
/dev/sdb1  ext4    GenG1610T002 (not mounted) fc5f2e1a-32a0-4b72-971f-28828ef1cd42
/dev/sdc1  ext4    GenG1610T003 (not mounted) c41de965-ebea-4229-a2b0-e514be69bf67
/dev/sdd1  ext4    GenG1610T004 (not mounted) 4ffe7ed7-6381-421c-bc93-1bec6448ee37
/dev/sde1  vfat    GENG1610TSD /cdrom      17FF-395B
/dev/ram0                   (not mounted)  
/dev/ram1                   (not mounted)  
/dev/ram2                   (not mounted)  
/dev/ram3                   (not mounted)  
/dev/ram4                   (not mounted)  
/dev/ram5                   (not mounted)  
/dev/ram6                   (not mounted)  
/dev/ram7                   (not mounted)  
/dev/ram8                   (not mounted)  
/dev/ram9                   (not mounted)  
/dev/ram10                  (not mounted)  
/dev/ram11                  (not mounted)  
/dev/ram12                  (not mounted)  
/dev/ram13                  (not mounted)  
/dev/ram14                  (not mounted)  
/dev/ram15                  (not mounted)  
/dev/loop0                  /rofs          
/dev/sda1                   (not mounted)  
/dev/sda3                   [SWAP]         
/dev/sdf1                   /media/ubuntu/VID 
/dev/sdg1                   (not mounted)  
/dev/sdg5                   [SWAP]         
ubuntu@ubuntu:~$ 

```
The /de/ramX I have no clue what they are. Memory is 16GB so it may be ram

boot-repair info is here: [http://paste2.org/MNJcf35p](http://paste2.org/MNJcf35p) which I reproduce below:
Apologies for the long paste but I genuinely cannot find anywhere to cut off confidently
```

[Paste2]("http://paste2.org/")                                                                                       
[Create Paste]("http://paste2.org/")
[Followup Paste]("http://paste2.org/MNJcf35p/followup")
[QR]("http://paste2.org/MNJcf35p/qr")
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]
  
 
    ============================= Boot Info Summary: ===============================
  
     => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
         of the same hard drive for core.img. core.img is at this location and 
         looks for (,gpt2)/boot/grub. It also embeds following components:
         
         modules
         ---------------------------------------------------------------------------
         fshelp ext2 part_gpt biosdisk
         ---------------------------------------------------------------------------
      => No boot loader is installed in the MBR of /dev/sdb.
      => No boot loader is installed in the MBR of /dev/sdc.
      => No boot loader is installed in the MBR of /dev/sdd.
      => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sde.
      => No boot loader is installed in the MBR of /dev/sdf.
      => Grub2 (v2.00) is installed in the MBR of /dev/sdg and looks at sector 1 of 
         the same hard drive for core.img. core.img is at this location and looks 
         for (,msdos1)/boot/grub. It also embeds following components:
         
         modules
         ---------------------------------------------------------------------------
         fshelp ext2 part_msdos biosdisk
         ---------------------------------------------------------------------------
  
    sda1: __________________________________________________________________________
  
        File system:       
         Boot sector type:  Grub2's core.img
         Boot sector info: 
         Mounting failed:   mount: unknown filesystem type ''
  
    sda2: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  Ubuntu 16.04 LTS
         Boot files:        /boot/grub/grub.cfg /etc/fstab 
                            /boot/grub/i386-pc/core.img
  
    sda3: __________________________________________________________________________
  
        File system:       swap
         Boot sector type:  -
         Boot sector info: 
  
    sdb1: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  
         Boot files:        
  
    sdc1: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  
         Boot files:        
  
    sdd1: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  
         Boot files:        
  
    sde1: __________________________________________________________________________
  
        File system:       vfat
         Boot sector type:  SYSLINUX 6.03
         Boot sector info:  Syslinux looks at sector 30840 of /dev/sde1 for its 
                            second stage. The integrity check of Syslinux failed. 
                            No errors found in the Boot Parameter Block.
         Operating System:  
         Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                            /EFI/BOOT/grubx64.efi /ldlinux.sys
  
    sdf1: __________________________________________________________________________
  
        File system:       vfat
         Boot sector type:  FAT32
         Boot sector info:  According to the info in the boot sector, sdf1 starts 
                            at sector 0. But according to the info from fdisk, 
                            sdf1 starts at sector 63. According to the info in the 
                            boot sector, sdf1 has 524224 sectors.. But according 
                            to the info from the partition table, it has 514016 
                            sectors.
         Operating System:  
         Boot files:        
  
    sdg1: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  Ubuntu 16.04 LTS
         Boot files:        /etc/fstab /boot/grub/i386-pc/core.img
  
    sdg2: __________________________________________________________________________
  
        File system:       Extended Partition
         Boot sector type:  Unknown
         Boot sector info: 
  
    sdg5: __________________________________________________________________________
  
        File system:       swap
         Boot sector type:  -
         Boot sector info: 
  
    ============================ Drive/Partition Info: =============================
  
    Drive: sda _____________________________________________________________________
     Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: gpt
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT
  
 
    GUID Partition Table detected.
  
    Partition  Attrs   Start Sector    End Sector  # of Sectors System
     /dev/sda1                 2,048         4,095         2,048 Data partition (Linux)
     /dev/sda2                 4,096 7,780,554,751 7,780,550,656 Data partition (Linux)
     /dev/sda3         7,780,554,752 7,814,035,455    33,480,704 Swap partition (Linux)
  
    Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
  
    Drive: sdb _____________________________________________________________________
     Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: gpt
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT
  
 
    GUID Partition Table detected.
  
    Partition  Attrs   Start Sector    End Sector  # of Sectors System
     /dev/sdb1                 2,048 7,814,035,455 7,814,033,408 Data partition (Linux)
  
    Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
  
    Drive: sdc _____________________________________________________________________
     Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: gpt
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT
  
 
    GUID Partition Table detected.
  
    Partition  Attrs   Start Sector    End Sector  # of Sectors System
     /dev/sdc1                 2,048 7,814,037,134 7,814,035,087 Data partition (Linux)
  
    Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
  
    Drive: sdd _____________________________________________________________________
     Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: gpt
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT
  
 
    GUID Partition Table detected.
  
    Partition  Attrs   Start Sector    End Sector  # of Sectors System
     /dev/sdd1                 2,048 7,814,037,134 7,814,035,087 Data partition (Linux)
  
    Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
  
    Drive: sde _____________________________________________________________________
     Disk /dev/sde: 60.1 GiB, 64490569728 bytes, 125958144 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disklabel type: dos
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sde1    *          2,048   125,958,143   125,956,096   c W95 FAT32 (LBA)
  
 
    Drive: sdf _____________________________________________________________________
     Disk /dev/sdf: 256 MiB, 268435456 bytes, 524288 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disklabel type: dos
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sdf1                  63       514,079       514,017   c W95 FAT32 (LBA)
  
 
    Drive: sdg _____________________________________________________________________
     Disk /dev/sdg: 298.1 GiB, 320072933376 bytes, 625142448 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disklabel type: dos
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sdg1               2,048   591,659,007   591,656,960  83 Linux
     /dev/sdg2         591,661,054   625,141,759    33,480,706   5 Extended
     /dev/sdg5         591,661,056   625,141,759    33,480,704  82 Linux swap / Solaris
  
 
    "blkid" output: ________________________________________________________________
  
    Device           UUID                                   TYPE       LABEL
  
    /dev/loop0                                              squashfs   
     /dev/sda1                                                          
     /dev/sda2        2fdc85b0-4f3a-454d-93fa-85c02fe26185   ext4       
     /dev/sda3        82a5e0e3-9828-44f7-94e2-5376bf0fadf1   swap       
     /dev/sdb1        fc5f2e1a-32a0-4b72-971f-28828ef1cd42   ext4       GenG1610T002
     /dev/sdc1        c41de965-ebea-4229-a2b0-e514be69bf67   ext4       GenG1610T003
     /dev/sdd1        4ffe7ed7-6381-421c-bc93-1bec6448ee37   ext4       GenG1610T004
     /dev/sde1        17FF-395B                              vfat       GENG1610TSD
     /dev/sdf1        55BA-8E92                              vfat       VID
     /dev/sdg1        ff062a65-1aaf-4172-a35a-13a6a85e87c4   ext4       
     /dev/sdg5        d33d22aa-945d-4ed1-a710-ed6c7f379708   swap       
  
    ========================= "ls -l /dev/disk/by-id" output: ======================
  
    total 0
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 ata-Hitachi_HCC543232A7A380_E203421L16RUYP -> ../../sdg
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HCC543232A7A380_E203421L16RUYP-part1 -> ../../sdg1
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HCC543232A7A380_E203421L16RUYP-part2 -> ../../sdg2
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HCC543232A7A380_E203421L16RUYP-part5 -> ../../sdg5
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 ata-Hitachi_HDS5C4040ALE630_PL1321LAGB3H5H -> ../../sda
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HDS5C4040ALE630_PL1321LAGB3H5H-part1 -> ../../sda1
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HDS5C4040ALE630_PL1321LAGB3H5H-part2 -> ../../sda2
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HDS5C4040ALE630_PL1321LAGB3H5H-part3 -> ../../sda3
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 ata-Hitachi_HDS5C4040ALE630_PL2331LAGAP1AJ -> ../../sdb
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-Hitachi_HDS5C4040ALE630_PL2331LAGAP1AJ-part1 -> ../../sdb1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 ata-ST4000DM000-1F2168_Z3015TFR -> ../../sdd
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-ST4000DM000-1F2168_Z3015TFR-part1 -> ../../sdd1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 ata-ST4000DM000-1F2168_Z3015TR7 -> ../../sdc
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 ata-ST4000DM000-1F2168_Z3015TR7-part1 -> ../../sdc1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 usb-HP_iLO_Internal_SD-CARD_000002660A01-0:0 -> ../../sde
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 usb-HP_iLO_Internal_SD-CARD_000002660A01-0:0-part1 -> ../../sde1
     lrwxrwxrwx 1 root root  9 Jun  8 20:13 usb-HP_iLO_LUN_01_Media_0_000002660A01-0:1 -> ../../sdf
     lrwxrwxrwx 1 root root 10 Jun  8 20:13 usb-HP_iLO_LUN_01_Media_0_000002660A01-0:1-part1 -> ../../sdf1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 wwn-0x5000c5006575dccd -> ../../sdd
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000c5006575dccd-part1 -> ../../sdd1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 wwn-0x5000c500657623cb -> ../../sdc
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000c500657623cb-part1 -> ../../sdc1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 wwn-0x5000cca22ec4dab4 -> ../../sdb
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca22ec4dab4-part1 -> ../../sdb1
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 wwn-0x5000cca22ec50d2e -> ../../sda
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca22ec50d2e-part1 -> ../../sda1
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca22ec50d2e-part2 -> ../../sda2
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca22ec50d2e-part3 -> ../../sda3
     lrwxrwxrwx 1 root root  9 Jun  8 20:49 wwn-0x5000cca706d12775 -> ../../sdg
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca706d12775-part1 -> ../../sdg1
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca706d12775-part2 -> ../../sdg2
     lrwxrwxrwx 1 root root 10 Jun  8 20:49 wwn-0x5000cca706d12775-part5 -> ../../sdg5
  
    ================================ Mount points: =================================
  
    Device           Mount_Point              Type       Options
  
    /dev/loop0       /rofs                    squashfs   (ro,noatime)
     /dev/sde1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
     /dev/sdf1        /media/ubuntu/VID        vfat        (ro,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
  
 
    =========================== sda2/boot/grub/grub.cfg: ===========================
  
    --------------------------------------------------------------------------------
     #
     # DO NOT EDIT THIS FILE
     #
     # It is automatically generated by grub-mkconfig using templates
     # from /etc/grub.d and settings from /etc/default/grub
     #
  
    ### BEGIN /etc/grub.d/00_header ###
     if [ -s $prefix/grubenv ]; then
       set have_grubenv=true
       load_env
     fi
     if [ "${next_entry}" ] ; then
        set default="${next_entry}"
        set next_entry=
        save_env next_entry
        set boot_once=true
     else
        set default="Advanced options for Ubuntu>Ubuntu, with Linux 4.4.0-21-generic"
     fi
  
    if [ x"${feature_menuentry_id}" = xy ]; then
       menuentry_id_option="--id"
     else
       menuentry_id_option=""
     fi
  
    export menuentry_id_option
  
    if [ "${prev_saved_entry}" ]; then
       set saved_entry="${prev_saved_entry}"
       save_env saved_entry
       set prev_saved_entry=
       save_env prev_saved_entry
       set boot_once=true
     fi
  
    function savedefault {
       if [ -z "${boot_once}" ]; then
         saved_entry="${chosen}"
         save_env saved_entry
       fi
     }
     function recordfail {
       set recordfail=1
       if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
     }
     function load_video {
       if [ x$feature_all_video_module = xy ]; then
         insmod all_video
       else
         insmod efi_gop
         insmod efi_uga
         insmod ieee1275_fb
         insmod vbe
         insmod vga
         insmod video_bochs
         insmod video_cirrus
       fi
     }
  
    insmod part_gpt
     insmod ext2
     set root='hd0,gpt2'
     if [ x$feature_platform_search_hint = xy ]; then
       search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
     else
       search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
     fi
     if loadfont /boot/grub/unicode.pf2 ; then
       set gfxmode=auto
       load_video
       insmod gfxterm
       set locale_dir=$prefix/locale
       set lang=en_GB
       insmod gettext
     fi
     terminal_output gfxterm
     if [ "${recordfail}" = 1 ] ; then
       set timeout=30
     else
       if [ x$feature_timeout_style = xy ] ; then
         set timeout_style=menu
         set timeout=10
       # Fallback normal timeout code in case the timeout_style feature is
       # unavailable.
       else
         set timeout=10
       fi
     fi
     ### END /etc/grub.d/00_header ###
  
    ### BEGIN /etc/grub.d/05_debian_theme ###
     set menu_color_normal=white/black
     set menu_color_highlight=black/light-gray
     ### END /etc/grub.d/05_debian_theme ###
  
    ### BEGIN /etc/grub.d/10_linux ###
     function gfxmode {
         set gfxpayload="${1}"
         if [ "${1}" = "keep" ]; then
             set vt_handoff=vt.handoff=7
         else
             set vt_handoff=
         fi
     }
     if [ "${recordfail}" != 1 ]; then
       if [ -e ${prefix}/gfxblacklist.txt ]; then
         if hwmatch ${prefix}/gfxblacklist.txt 3; then
           if [ ${match} = 0 ]; then
             set linux_gfx_mode=keep
           else
             set linux_gfx_mode=text
           fi
         else
           set linux_gfx_mode=text
         fi
       else
         set linux_gfx_mode=keep
       fi
     else
       set linux_gfx_mode=text
     fi
     export linux_gfx_mode
     menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu  --class os $menuentry_id_option  'gnulinux-simple-2fdc85b0-4f3a-454d-93fa-85c02fe26185' {
         recordfail
         load_video
         gfxmode $linux_gfx_mode
         insmod gzio
         if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
         insmod part_gpt
         insmod ext2
         set root='hd0,gpt2'
         if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
         else
           search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
         fi
         linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro  quiet splash $vt_handoff
         initrd    /boot/initrd.img-4.4.0-22-generic
     }
     submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2fdc85b0-4f3a-454d-93fa-85c02fe26185' {
         menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-4.4.0-22-generic-advanced-2fdc85b0-4f3a-454d-93fa-85c02fe26185'  {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
             else
               search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
             fi
             echo    'Loading Linux 4.4.0-22-generic ...'
             linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro  quiet splash $vt_handoff
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-22-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-22-generic (upstart)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-4.4.0-22-generic-init-upstart-2fdc85b0-4f3a-454d-93fa-85c02fe26185'  {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
             else
               search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
             fi
             echo    'Loading Linux 4.4.0-22-generic ...'
             linux    /boot/vmlinuz-4.4.0-22-generic  root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro  quiet splash  $vt_handoff init=/sbin/upstart
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-22-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-4.4.0-22-generic-recovery-2fdc85b0-4f3a-454d-93fa-85c02fe26185'  {
             recordfail
             load_video
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
             else
               search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
             fi
             echo    'Loading Linux 4.4.0-22-generic ...'
             linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro recovery nomodeset 
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-22-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-4.4.0-21-generic-advanced-2fdc85b0-4f3a-454d-93fa-85c02fe26185'  {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
             else
               search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
             fi
             echo    'Loading Linux 4.4.0-21-generic ...'
             linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro  quiet splash $vt_handoff
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-21-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-4.4.0-21-generic-init-upstart-2fdc85b0-4f3a-454d-93fa-85c02fe26185'  {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
             else
               search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
             fi
             echo    'Loading Linux 4.4.0-21-generic ...'
             linux    /boot/vmlinuz-4.4.0-21-generic  root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro  quiet splash  $vt_handoff init=/sbin/upstart
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-21-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-4.4.0-21-generic-recovery-2fdc85b0-4f3a-454d-93fa-85c02fe26185'  {
             recordfail
             load_video
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root  --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
             else
               search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
             fi
             echo    'Loading Linux 4.4.0-21-generic ...'
             linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 ro recovery nomodeset 
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-21-generic
         }
     }
  
    ### END /etc/grub.d/10_linux ###
  
    ### BEGIN /etc/grub.d/20_linux_xen ###
  
    ### END /etc/grub.d/20_linux_xen ###
  
    ### BEGIN /etc/grub.d/20_memtest86+ ###
     menuentry 'Memory test (memtest86+)' {
         insmod part_gpt
         insmod ext2
         set root='hd0,gpt2'
         if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
         else
           search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
         fi
         knetbsd    /boot/memtest86+.elf
     }
     menuentry 'Memory test (memtest86+, serial console 115200)' {
         insmod part_gpt
         insmod ext2
         set root='hd0,gpt2'
         if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2  --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2   2fdc85b0-4f3a-454d-93fa-85c02fe26185
         else
           search --no-floppy --fs-uuid --set=root 2fdc85b0-4f3a-454d-93fa-85c02fe26185
         fi
         linux16    /boot/memtest86+.bin console=ttyS0,115200n8
     }
     ### END /etc/grub.d/20_memtest86+ ###
  
    ### BEGIN /etc/grub.d/30_os-prober ###
     ### END /etc/grub.d/30_os-prober ###
  
    ### BEGIN /etc/grub.d/30_uefi-firmware ###
     ### END /etc/grub.d/30_uefi-firmware ###
  
    ### BEGIN /etc/grub.d/40_custom ###
     # This file provides an easy way to add custom menu entries.  Simply type the
     # menu entries you want to add after this comment.  Be careful not to change
     # the 'exec tail' line above.
     ### END /etc/grub.d/40_custom ###
  
    ### BEGIN /etc/grub.d/41_custom ###
     if [ -f  ${config_directory}/custom.cfg ]; then
       source ${config_directory}/custom.cfg
     elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
       source $prefix/custom.cfg;
     fi
     ### END /etc/grub.d/41_custom ###
     --------------------------------------------------------------------------------
  
    =============================== sda2/etc/fstab: ================================
  
    --------------------------------------------------------------------------------
     # /etc/fstab: static file system information.
     #
     # Use 'blkid' to print the universally unique identifier for a
     # device; this may be used with UUID= as a more robust way to name devices
     # that works even if disks are added and removed. See fstab(5).
     #
     # <file system> <mount point>   <type>  <options>       <dump>  <pass>
     # / was on /dev/sde2 during installation
     UUID=2fdc85b0-4f3a-454d-93fa-85c02fe26185 /               ext4    errors=remount-ro 0       1
     # swap was on /dev/sde3 during installation
     UUID=82a5e0e3-9828-44f7-94e2-5376bf0fadf1 none            swap    sw              0       0
     --------------------------------------------------------------------------------
  
    =================== sda2: Location of files loaded by Grub: ====================
  
               GiB - GB             File                                 Fragment(s)
  
    2776.735961914 = 2981.497536512 boot/grub/grub.cfg                             1
     2776.729312897 = 2981.490397184 boot/grub/i386-pc/core

```

---

### Post by QIII on 2016-06-08
@seanbw2:

Please use code tags rather than quote tags for long output:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by seanbw2 on 2016-06-08
```

===================================================================================
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sda2 into the MBRs of all disks (except USB without OS).
The boot flag would be placed on sda1.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems


=================== Blockers in case of suggested repair
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (4001GB) disk!
=================================================================================

The suggested repair indicated by boot-repair will not work for the simple reason that I have tried it both using gui and cli and the same things happen. The installation to sdg defaults to a i386 mode which suggests msdos which creates a disconnection between sda and sdg.
Even if I give up and install to sda and boot from sda, I still get drooped into a grub rescue prompt.

```

Q: can I copy the grub structure from sda to sdg? Will that work?

@[**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170") :  cool. I have edited the very long post. It looks better and less frightening ;)
Thanks

---

### Post by oldfred on 2016-06-08
With link we really do not need it posted.

You cannot copy MBR from gpt drive to a MBR drive. 
MBR has core.img hidden in the sectors after the MBR. 
Gpt has core.img in the bios_grub partition.

I probably would have also used gpt on sdg, even though not required. But that also then would require the bios_grub partition.

You now show a full install on sda as well as sdg.
The grub in sdg is looking for files on sda. But I would think it still should boot.

Do you have UEFI/BIOS set to boot in BIOS boot mode? Not IDE nor RAID?

Do not run the auto fix with Boot-Repair.
You can run advanced mode, choose install in sdg, and install grub to only sdg. And the full uninstall/reinstall grub option.

Does sda1 install boot?

---

### Post by seanbw2 on 2016-06-08
The installer is on /dev/sdf and i am trying to install to /dev/sdg.
phew

> **oldfred said:**
> With link we really do not need it posted.

You cannot copy MBR from gpt drive to a MBR drive. 
MBR has core.img hidden in the sectors after the MBR. 
Gpt has core.img in the bios_grub partition.

I probably would have also used gpt on sdg, even though not required. But that also then would require the bios_grub partition.

I don't understand how sdg is not gpt. I used GParted on all disks.

> **oldfred said:**
>  You now show a full install on sda as well as sdg.

Yes I tried to install to sda first, it won't boot but went to grub rescue. Tried boot-repair and installed to all drives. Booted and still sent into grub rescue prompt so I gave up and installed to sdg in the hope that I can make HP boot from sdg by using the BIOS option in the BIOS menu allowing thre system to boot from the second esata controller. 
I have not been able to get the system boot after that. It still went into grub rescue.

> **oldfred said:**
>  The grub in sdg is looking for files on sda. But I would think it still should boot. 

I think the mismatch is the issue - no? From sda - it is looking for gpt entries in sdg and from sdg looking for msdos in sda?

 > **oldfred said:**
>   Do you have UEFI/BIOS set to boot in BIOS boot mode? Not IDE nor RAID? 

No I have AHCI boot. I have three options in this pc - AHCI, Legacy and HP Raid. Raid is a non contender because my plan is to use Snapraid, mergerfs and pool.

 > **oldfred said:**
>  Do not run the auto fix with Boot-Repair.

No fear. I shan't. I have run it prior. It did not work. Not its fault. At that point I had 14 drives it was working through.

> **oldfred said:**
>    You can run advanced mode, choose install in sdg, and install grub to only sdg. And the full uninstall/reinstall grub option.  

You are suggesting install grub to sdg. Uninstall grub from sda?  

> **oldfred said:**
>   Does sda1 install boot?  

Yes I have tried before deciding on sdg. It still went to grub rescue mode.

Just thinking aloud. I can boot into live sd card OK. Should I reinstall to sdg after using GParted to delete, format and partition using GPT?
Is that a step forward? 
i.e.
using Live CD - Run GParted and delete existing partition on sda and sdg
Still using GParted - format both drives - using same values GPT and ext4
Using the Install from Live CD option - install to sdg.
Leave sda empty but if my experience is same - Live CD will still put pointers on sda because HP forces it to.

Is this worth a try?

I went ahead and tried it.
Got the same I can't install bootloader to sdgX.
Ran bbot-repair and reinstalled to sdg.
BootInfo pastebin link is : [http://paste2.org/v85PXhCy](http://paste2.org/v85PXhCy)
It is asking me to reboot but I don't think so yet.

---

### Post by oldfred on 2016-06-08
Your sdg is still MBR.
To get gpt you have to select in gparted before anything else, select gpt under device, advanced & select gpt over msdos(MBR) default partitioning....     

If you partition in advance, then you have to have the bios_grub 1 or 2MB unformatted partition for grub to correctly install.
And only with Something Else do you get option on where to install grub, and that should always be a drive like sdg, never a partition like sdg1.

AHCI is correct. And a few BIOS require a boot flag on a partition. Grub does not use boot flag, only Windows & syslinux. But a few BIOS seem to only know about Windows and must see the boot flag. But BIOS boot flag is not the same as UEFI/gpt boot flag.

With gpt the boot flag should only be on an ESP - efi system partition.

Since I knew I was eventually going to convert to a newer UEFI system, I started putting both the ESP and bios_grub on new drives well before my first UEFI system. 
If it wants boot flag, then add a small 100MB ESP, FAT32 formatted with gpt. It probably should be first partition on drive as that is UEFI recommendation.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Just noticed this:
Matrox Electronics Systems Ltd. MGA G200EH [102b:0533]

Are you sure it is not booting, but you have video issues? With only one install grub menu is not shown unless you hold shift key, and it goes right on to booting system. 

Some suggestions here on Matrox driver fixes:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)

---

### Post by seanbw2 on 2016-06-09
Boot Info incase I have really messed up my system: [http://paste2.org/mme7ZPBt](http://paste2.org/mme7ZPBt)

---

### Post by oldfred on 2016-06-09
Now you have two ESP - efi system partitions on sdg. Most UEFI, do not like two ESPs.
Only one ESP or FAT32 partition with the boot flag per device. And that is for UEFI boot. Neither of yours are shown as FAT32?
And/or one bios_grub partition for BIOS boot.

```

 /dev/sdg1    10,240   562,636,799   562,626,560 EFI System partition
/dev/sdg2      2,048      10,239            8,192 EFI System partition 


```

See post #8 above on how I normally partition.
       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by seanbw2 on 2016-06-09
Thanks Oldfred. What I am doing is:
Reboot - Done
Delete partitions sda and sdg
Using Gparted - make sdg a gpt drive. I tried to use GParted to repartition sdg into grub_bios,  main and swap partitions but I ran into a problem. using GParted to create a grub_bios partition created a 1MB partition in front of the grub_bios partition i.e. sdg2 (grub_bios) 5MB resulted in sdg2 and sdg6 where both are grub_bios but sdg2 is 1 MB less than before I started and that 1 MB is used to create sdg6 (say) so I will try and use the ubuntu partition manager this time.
Which means - I will use GParted to make sdg a GPT drive but use Ubuntu partition manager to create the other partitions.
install Ubuntu Live session on sdg and put the bootloader on /dev/sdg not sdg1
(sdg has now become sdh because of drive I am using to backup)
Apologies but I think I am confused.

> Since I knew I was eventually going to convert to a newer UEFI system, I  started putting both the ESP and bios_grub on new drives well before my  first UEFI system. 
If it wants boot flag, then add a small 100MB ESP, FAT32 formatted with  gpt. It probably should be first partition on drive as that is UEFI  recommendation.

Does this not result in 4 partitions?
sdg1 = 300mb for bios_grub  (GParted will not allow the same partition to carry both flags i.e. bios_grub and boot
sdg2=30GB for swap
sdg1 =ext4 mounted as / main ubuntu installation partition
where does esp go? if I hive 100mb off sdg2 as esp - this makes 4 partitions.

---

### Post by seanbw2 on 2016-06-09
[ATTACH=CONFIG]269491[/ATTACH]
This is what I am ending up with.
1MB free space from creating bios_grub from initial 300mb unformatted partition, then 300MB bios_grub partition, 301GB / ubuntu/home partition and finally 15GB swap partition.
Where does the esp go?
I am holding off the installation until I am definite as I think i am on the cusp of a final solution (well then the battle of making HP boot to sdg starts but that is a familiar battle)
So waiting for guidance/assistance at this point. Many thanks to everybody that have chipped in to help. It is a refreshing change from prior atempts.

---

### Post by oldfred on 2016-06-09
Is the installer calling the gparted bios_grub partition biosgrub. That would just be the same partition. Grub on gpt partitioned drives needs a unformatted partition of 1 or 2MB.

You can have a 100-300MB partition formatted FAT32 with boot flag (ESP). That would only be used for UEFI boot, but good to have on drive if later you convert that drive to UEFI boot. It is recommended by UEFI to be first on drive and that can be difficult to add once drive has lots of data. If not using it now, make it only 100MB.

For BIOS boot you must have a 1 or 2MB unformatted partition with the bios_grub flag.

Then how you boot installer is how either is used. If you boot installer in UEFI mode the ESP is used. If you boot installer in BIOS mode, then the bios_grub partition is used.

This is all the same as I posted in post #8. I always create  ESP, bios_grub, / (root) & swap with gparted and using gpt. And never had any issues.

Partitions should end up like mine:
```
 Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2       1,026,048     1,030,143         4,096 BIOS Boot partition
/dev/sda3       1,030,144    52,229,362    51,199,219 Data partition (Linux)
/dev/sda4     246,163,456   250,068,991     3,905,536 Swap partition (Linux) 


```

---

### Post by seanbw2 on 2016-06-09
Thank you. It seemed clear enough. I just wanted to be sure.
lack of confidence I guess.
So I will now extend the existing free space, format it FAT32 with boot flag but it will not be used for now.
The other partitions are OK looking at your setup.
Ok. deep breath and ...

---

### Post by seanbw2 on 2016-06-09
Wow . Installation finished wit no error messages. 
First thing is to test that I can boot into sdg using the bios set by HP.
Oldfred - I am grateful. Many thanks.
Let me try and boot into sdg from startup.

---

### Post by seanbw2 on 2016-06-09
after a few niggles with HP, I am now logging into sdg straight from boot.
Thanks Oldfred.Much obliged.
Now to get my fstab setup properly with my 14 hard disks and counting.
I shall mark this thread solved.
Cheers

sean

---

### Post by oldfred on 2016-06-09
Glad you got it working.

If you have issues with fstab or mounting post a new thread. I only know standard partitions not RAID nor any special server type configurations.

---

