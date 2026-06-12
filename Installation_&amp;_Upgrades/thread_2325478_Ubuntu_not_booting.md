---
title: "Ubuntu not booting"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by Omar_Jair on 2016-05-22
I recently installed the newest version of ubuntu but my computer keeps telling me there is no boot device, i tried to follow the boot partition creation method posted here [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition), sadly it hasn't helped a lot (not to say anything) the boot repair system tells me to do otherwise than the instructions and if i manage to do the boot-grub flag partition the system tells me i need another EFI partition, i dont make it and the purging kernel loading message keeps stuck (i've let it for 4 hours straight and nothing), is there any easier or more detailed steps? because it's getting frustrating.

---

### Post by grahammechanical on 2016-05-22
We need more information. Hardware specification? Other OS installed? BIOS or UEFI boot system? Did you select Erase disk & install Ubuntu? Or, the Something Else option?

If you have Windows 8 - 10 installed then you have a UEFI boot system. Have you read this wiki page?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If we have a UEFI boot system and we are using the Something else option than the installer will need at least 3 partitions. A efi_boot partition, a partition for Ubuntu & a swap partition. If Windows 8 -10 is installed then then installer can make use of the existing efi_boot partition that Windows is using.

Th emessage that there is no boot device does not necessarily mean that you need a boot partition. It means that the motherboard cannot find a boot loader. If we run Boot Repair and create a BootInfo summary report we get a URL to the location the summary report is stored. Post the URL in this thread. Then we can see for ourselves what Boot Repair has found.

Regards.

---

### Post by Omar_Jair on 2016-05-22
No other OS installed, i don't know what do you mean by software, i erased and installed ubuntu, i also have my boot repair logs, here are they
>                                    [Paste2]("http://paste2.org/")                                                                                       
[LIST]
[*][Create Paste]("http://paste2.org/") 
[*][Followup Paste]("http://paste2.org/bI5p5U2U/followup") 
[*][QR]("http://paste2.org/bI5p5U2U/qr") 
[/LIST]
                                                                                                                 


 ```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]
  
 
    ============================= Boot Info Summary: ===============================
  
     => No boot loader is installed in the MBR of /dev/sda.
  
    sda1: __________________________________________________________________________
  
        File system:       vfat
         Boot sector type:  FAT32
         Boot sector info:  No errors found in the Boot Parameter Block.
         Operating System:  
         Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                            /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                            /EFI/ubuntu/shimx64.efi 
                            /EFI/Microsoft/Boot/bootmgfw.efi 
                            /EFI/Microsoft/Boot/bootx64.efi
  
    sda2: __________________________________________________________________________
  
        File system:       ext4
         Boot sector type:  -
         Boot sector info: 
         Operating System:  Ubuntu 16.04 LTS
         Boot files:        /boot/grub/grub.cfg /etc/fstab
  
    sda3: __________________________________________________________________________
  
        File system:       swap
         Boot sector type:  -
         Boot sector info: 
  
    ============================ Drive/Partition Info: =============================
  
    Drive: sda _____________________________________________________________________
     Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: gpt
  
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  
    /dev/sda1                   1   976,773,167   976,773,167  ee GPT
  
 
    GUID Partition Table detected.
  
    Partition  Attrs   Start Sector    End Sector  # of Sectors System
     /dev/sda1                 2,048     1,050,623     1,048,576 EFI System partition
     /dev/sda2             1,050,624   968,615,935   967,565,312 Data partition (Linux)
     /dev/sda3           968,615,936   976,771,071     8,155,136 Swap partition (Linux)
  
    Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
  
    "blkid" output: ________________________________________________________________
  
    Device           UUID                                   TYPE       LABEL
  
    /dev/loop0                                              squashfs   
     /dev/sda1        25E3-456F                              vfat       
     /dev/sda2        50ee09d6-0d07-4fe3-a340-a82b019a712d   ext4       
     /dev/sda3        f873a567-0b25-4185-ad67-a91f5d974ccc   swap       
     /dev/sr0         2016-04-20-22-29-52-00                 iso9660    Ubuntu 16.04 LTS amd64
  
    ========================= "ls -l /dev/disk/by-id" output: ======================
  
    total 0
     lrwxrwxrwx 1 root root  9 May 23 03:01 ata-HGST_HTS545050A7E380_150125TM8514TFHMHT2P -> ../../sda
     lrwxrwxrwx 1 root root 10 May 23 03:01 ata-HGST_HTS545050A7E380_150125TM8514TFHMHT2P-part1 -> ../../sda1
     lrwxrwxrwx 1 root root 10 May 23 03:01 ata-HGST_HTS545050A7E380_150125TM8514TFHMHT2P-part2 -> ../../sda2
     lrwxrwxrwx 1 root root 10 May 23 03:01 ata-HGST_HTS545050A7E380_150125TM8514TFHMHT2P-part3 -> ../../sda3
     lrwxrwxrwx 1 root root  9 May 23 02:55 ata-TSSTcorp_CDDVDW_SU-208GB_S16T6YDG100S3S -> ../../sr0
     lrwxrwxrwx 1 root root  9 May 23 03:01 wwn-0x5000cca7a1d6f5c7 -> ../../sda
     lrwxrwxrwx 1 root root 10 May 23 03:01 wwn-0x5000cca7a1d6f5c7-part1 -> ../../sda1
     lrwxrwxrwx 1 root root 10 May 23 03:01 wwn-0x5000cca7a1d6f5c7-part2 -> ../../sda2
     lrwxrwxrwx 1 root root 10 May 23 03:01 wwn-0x5000cca7a1d6f5c7-part3 -> ../../sda3
  
    ================================ Mount points: =================================
  
    Device           Mount_Point              Type       Options
  
    /dev/loop0       /rofs                    squashfs   (ro,noatime)
     /dev/sda2        /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
     /dev/sr0         /cdrom                   iso9660    (ro,noatime)
  
 
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
        set default="0"
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
  
    if [ x$feature_default_font_path = xy ] ; then
        font=unicode
     else
     insmod part_gpt
     insmod ext2
     set root='hd0,gpt2'
     if [ x$feature_platform_search_hint = xy ]; then
       search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
     else
       search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
     fi
         font="/usr/share/grub/unicode.pf2"
     fi
  
    if loadfont $font ; then
       set gfxmode=auto
       load_video
       insmod gfxterm
       set locale_dir=$prefix/locale
       set lang=en_US
       insmod gettext
     fi
     terminal_output gfxterm
     if [ "${recordfail}" = 1 ] ; then
       set timeout=10
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
     if background_color 44,0,30,0; then
       clear
     fi
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
     menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
         recordfail
         load_video
         gfxmode $linux_gfx_mode
         insmod gzio
         if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
         insmod part_gpt
         insmod ext2
         set root='hd0,gpt2'
         if [ x$feature_platform_search_hint = xy ]; then
           search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
         else
           search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
         fi
         linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro  quiet splash $vt_handoff
         initrd    /boot/initrd.img-4.4.0-22-generic
     }
     submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
         menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-advanced-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
             else
               search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
             fi
             echo    'Loading Linux 4.4.0-22-generic ...'
             linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro  quiet splash $vt_handoff
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-22-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-init-upstart-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
             else
               search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
             fi
             echo    'Loading Linux 4.4.0-22-generic ...'
             linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro  quiet splash $vt_handoff init=/sbin/upstart
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-22-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-recovery-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
             recordfail
             load_video
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
             else
               search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
             fi
             echo    'Loading Linux 4.4.0-22-generic ...'
             linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro recovery nomodeset 
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-22-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
             else
               search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
             fi
             echo    'Loading Linux 4.4.0-21-generic ...'
             linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro  quiet splash $vt_handoff
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-21-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
             recordfail
             load_video
             gfxmode $linux_gfx_mode
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
             else
               search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
             fi
             echo    'Loading Linux 4.4.0-21-generic ...'
             linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro  quiet splash $vt_handoff init=/sbin/upstart
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-21-generic
         }
         menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-50ee09d6-0d07-4fe3-a340-a82b019a712d' {
             recordfail
             load_video
             insmod gzio
             if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
             insmod part_gpt
             insmod ext2
             set root='hd0,gpt2'
             if [ x$feature_platform_search_hint = xy ]; then
               search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  50ee09d6-0d07-4fe3-a340-a82b019a712d
             else
               search --no-floppy --fs-uuid --set=root 50ee09d6-0d07-4fe3-a340-a82b019a712d
             fi
             echo    'Loading Linux 4.4.0-21-generic ...'
             linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d ro recovery nomodeset 
             echo    'Loading initial ramdisk ...'
             initrd    /boot/initrd.img-4.4.0-21-generic
         }
     }
  
    ### END /etc/grub.d/10_linux ###
  
    ### BEGIN /etc/grub.d/20_linux_xen ###
  
    ### END /etc/grub.d/20_linux_xen ###
  
    ### BEGIN /etc/grub.d/25_custom ###
  
    menuentry "EFI/ubuntu/fwupx64.efi" {
     search --fs-uuid --no-floppy --set=root 25E3-456F
     chainloader (${root})/EFI/ubuntu/fwupx64.efi
     }
  
    menuentry "EFI/ubuntu/MokManager.efi" {
     search --fs-uuid --no-floppy --set=root 25E3-456F
     chainloader (${root})/EFI/ubuntu/MokManager.efi
     }
     ### END /etc/grub.d/25_custom ###
  
    ### BEGIN /etc/grub.d/30_os-prober ###
     ### END /etc/grub.d/30_os-prober ###
  
    ### BEGIN /etc/grub.d/30_uefi-firmware ###
     menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
         fwsetup
     }
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
     # / was on /dev/sda2 during installation
     UUID=50ee09d6-0d07-4fe3-a340-a82b019a712d /               ext4    errors=remount-ro 0       1
     # /boot/efi was on /dev/sda1 during installation
     #UUID=25E3-456F  /boot/efi       vfat    umask=0077      0       1
     # swap was on /dev/sda3 during installation
     UUID=f873a567-0b25-4185-ad67-a91f5d974ccc none            swap    sw              0       0
     UUID=25E3-456F    /boot/efi    vfat    defaults    0    1
     --------------------------------------------------------------------------------
  
    =================== sda2: Location of files loaded by Grub: ====================
  
               GiB - GB             File                                 Fragment(s)
  
       0.500984192 = 0.537927680    boot/grub/grub.cfg                             1
        1.577819824 = 1.694171136    boot/vmlinuz-4.4.0-21-generic                  1
        2.155776978 = 2.314747904    boot/vmlinuz-4.4.0-22-generic                  1
        1.577819824 = 1.694171136    vmlinuz                                        1
        2.433994293 = 2.613481472    boot/initrd.img-4.4.0-21-generic               1
        2.829097748 = 3.037720576    boot/initrd.img-4.4.0-22-generic               3
        2.433994293 = 2.613481472    initrd.img                                     1
        2.433994293 = 2.613481472    initrd.img.old                                 1
  
    =============================== StdErr Messages: ===============================
  
    File descriptor 9 (/proc/20098/mounts) leaked on lvs invocation. Parent PID 28543: bash
     File descriptor 63 (pipe:[121285]) leaked on lvs invocation. Parent PID 28543: bash
  
    ADDITIONAL INFORMATION :
     =================== log of boot-repair 2016-05-23__03h00 ===================
     boot-repair version : 4ppa37
     boot-sav version : 4ppa37
     glade2script version : 3.2.3~ppa1
     boot-sav-extra version : 4ppa37
     Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
     Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
     boot-repair is executed in live-session (Ubuntu 16.04 LTS, xenial, Ubuntu, x86_64)
     CPU op-mode(s):        32-bit, 64-bit
     BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
     ls: cannot access '/home/usr/.config': No such file or directory
  
    =================== os-prober:
     /dev/sda2:Ubuntu 16.04 LTS (16.04):Ubuntu:linux
  
    =================== blkid:
     /dev/sda1: UUID="25E3-456F" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f8c1e537-67ca-4ce5-bfa5-c5ffc3ca5f9c"
     /dev/sda2: UUID="50ee09d6-0d07-4fe3-a340-a82b019a712d" TYPE="ext4" PARTUUID="ade7a20d-08d1-46b6-b707-408ac4a0e816"
     /dev/sr0: UUID="2016-04-20-22-29-52-00" LABEL="Ubuntu 16.04 LTS amd64" TYPE="iso9660" PTUUID="0e0e8e70" PTTYPE="dos"
     /dev/loop0: TYPE="squashfs"
     /dev/sda3: UUID="f873a567-0b25-4185-ad67-a91f5d974ccc" TYPE="swap" PARTUUID="912b5500-2434-446d-82c5-2024398a016c"
  
 
    1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
  
    Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
     Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootx64.efi
     Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
  
    =================== /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/etc/grub.d/ :
     drwxr-xr-x  2 root root    4096 May 23 02:59 grub.d
     drwxr-xr-x  2 root root    4096 May 23 02:56 grub.d.bak
     total 76
     -rwxr-xr-x 1 root root  9791 Apr 15 22:00 00_header
     -rwxr-xr-x 1 root root  6258 Mar 15 18:08 05_debian_theme
     -rwxr-xr-x 1 root root 12261 Apr 15 22:00 10_linux
     -rwxr-xr-x 1 root root 11082 Apr 15 22:00 20_linux_xen
     -rwxr-xr-x 1 root root   305 May 23 02:59 25_custom
     -rwxr-xr-x 1 root root 11692 Apr 15 22:00 30_os-prober
     -rwxr-xr-x 1 root root  1418 Apr 15 22:00 30_uefi-firmware
     -rwxr-xr-x 1 root root   214 Apr 15 22:00 40_custom
     -rwxr-xr-x 1 root root   216 Apr 15 22:00 41_custom
     -rw-r--r-- 1 root root   483 Apr 15 22:00 README
  
 
 
 
    =================== /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/etc/default/grub :
  
    # If you change this file, run 'update-grub' afterwards to update
     # /boot/grub/grub.cfg.
     # For full documentation of the options in this file, see:
     #   info -f grub -n 'Simple configuration'
  
    GRUB_DEFAULT=0
     #GRUB_HIDDEN_TIMEOUT=0
     GRUB_HIDDEN_TIMEOUT_QUIET=true
     GRUB_TIMEOUT=10
     GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
     GRUB_CMDLINE_LINUX=""
  
    # Uncomment to enable BadRAM filtering, modify to suit your needs
     # This works with Linux (no patch required) and with any kernel that obtains
     # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
     #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
  
    # Uncomment to disable graphical terminal (grub-pc only)
     #GRUB_TERMINAL=console
  
    # The resolution used on graphical terminal
     # note that you can use only modes which your graphic card supports via VBE
     # you can see them in real GRUB with the command `vbeinfo'
     #GRUB_GFXMODE=640x480
  
    # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
     #GRUB_DISABLE_LINUX_UUID=true
  
    # Uncomment to disable generation of recovery mode menu entries
     #GRUB_DISABLE_RECOVERY="true"
  
    # Uncomment to get a beep at grub start
     #GRUB_INIT_TUNE="480 440 1"
  
 
 
    /boot/efi detected in the fstab of sda2: UUID=25E3-456F     (sda1)
  
    =================== efibootmgr -v
     gui-g2slaunch.sh: line 140: 22583 Segmentation fault      (core dumped) LANGUAGE=C LC_ALL=C sudo efibootmgr -v
  
    =================== UEFI/Legacy mode:
     BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
     SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])
  
 
    =================== PARTITIONS & DISKS:
     sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
     sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d.
  
    sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
  
 
    =================== parted -l:
  
    Model: ATA HGST HTS545050A7 (scsi)
     Disk /dev/sda: 500GB
     Sector size (logical/physical): 512B/4096B
     Partition Table: gpt
     Disk Flags:
  
    Number  Start   End    Size    File system     Name                  Flags
     1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
     2      538MB   496GB  495GB   ext4
     3      496GB   500GB  4175MB  linux-swap(v1)
  
 
    Model: TSSTcorp CDDVDW SU-208GB (scsi)
     Disk /dev/sr0: 1486MB
     Sector size (logical/physical): 2048B/2048B
     Partition Table: mac
     Disk Flags:
  
    Number  Start   End     Size    File system  Name   Flags
     1      2048B   6143B   4096B                Apple
     2      1479MB  1481MB  2425kB               EFI
  
    =================== parted -lm:
  
    BYT;
     /dev/sda:500GB:scsi:512:4096:gpt:ATA HGST HTS545050A7:;
     1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
     2:538MB:496GB:495GB:ext4::;
     3:496GB:500GB:4175MB:linux-swap(v1)::;
  
    BYT;
     /dev/sr0:1486MB:scsi:2048:2048:mac:TSSTcorp CDDVDW SU-208GB:;
     1:2048B:6143B:4096B::Apple:;
     2:1479MB:1481MB:2425kB::EFI:;
  
    =================== lsblk:
     KNAME TYPE FSTYPE     SIZE LABEL
     sda   disk          465.8G
     sda1  part vfat       512M
     sda2  part ext4     461.4G
     sda3  part swap       3.9G
     sr0   rom  iso9660    1.4G Ubuntu 16.04 LTS amd64
     loop0 loop squashfs   1.3G
  
    KNAME ROTA RO RM STATE   MOUNTPOINT
     sda      1  0  0 running
     sda1     1  0  0         /mnt/boot-sav/sda1
     sda2     1  0  0         /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d
     sda3     1  0  0         [SWAP]
     sr0      1  0  1 running /cdrom
     loop0    1  1  0         /rofs
  
 
    =================== mount:
     sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
     proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
     udev on /dev type devtmpfs (rw,nosuid,relatime,size=1951024k,nr_inodes=487756,mode=755)
     devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
     tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=393136k,mode=755)
     /dev/sr0 on /cdrom type iso9660 (ro,noatime)
     /dev/loop0 on /rofs type squashfs (ro,noatime)
     /cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
     securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
     tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
     tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
     tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
     cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/)
     pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
     efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
     cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/)
     cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices,nsroot=/)
     cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,nsroot=/)
     cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/)
     cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/)
     cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory,nsroot=/)
     cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/)
     cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/)
     cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/)
     cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/)
     systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
     hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
     mqueue on /dev/mqueue type mqueue (rw,relatime)
     debugfs on /sys/kernel/debug type debugfs (rw,relatime)
     tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
     fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
     tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
     tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=393136k,mode=700,uid=999,gid=999)
     gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
     /dev/sda2 on /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
     /dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
  
 
    =================== ls:
     /sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
     /sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
     /dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout toshiba_acpi uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero
     ls /dev/mapper:  control
  
    =================== hexdump -n512 -C /dev/sda1
     00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
     00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
     00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
     00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
     00000040  80 01 29 6f 45 e3 25 4e  4f 20 4e 41 4d 45 20 20  |..)oE.%NO NAME  |
     00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
     00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
     00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
     00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
     00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
     000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
     000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
     000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
     000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
     000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
     *
     000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
     00000200
  
    =================== df -Th:
  
    Filesystem     Type      Size  Used Avail Use% Mounted on
     udev           devtmpfs  1.9G     0  1.9G   0% /dev
     tmpfs          tmpfs     384M  6.3M  378M   2% /run
     /dev/sr0       iso9660   1.4G  1.4G     0 100% /cdrom
     /dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
     /cow           overlay   1.9G  102M  1.8G   6% /
     tmpfs          tmpfs     1.9G  576K  1.9G   1% /dev/shm
     tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
     tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
     tmpfs          tmpfs     1.9G  320K  1.9G   1% /tmp
     tmpfs          tmpfs     384M   72K  384M   1% /run/user/999
     /dev/sda2      ext4      455G  4.1G  427G   1% /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d
     /dev/sda1      vfat      511M  3.1M  508M   1% /mnt/boot-sav/sda1
  
    =================== fdisk -l:
     Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
  
 
    Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
  
 
    Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
     Units: sectors of 1 * 512 = 512 bytes
     Sector size (logical/physical): 512 bytes / 4096 bytes
     I/O size (minimum/optimal): 4096 bytes / 4096 bytes
     Disklabel type: gpt
     Disk identifier: B7877691-1664-4386-969D-08EE87010E68
  
    Device         Start       End   Sectors   Size Type
     /dev/sda1       2048   1050623   1048576   512M EFI System
     /dev/sda2    1050624 968615935 967565312 461.4G Linux filesystem
     /dev/sda3  968615936 976771071   8155136   3.9G Linux swap
  
 
 
    =================== Recommended repair
     The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
     Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi
  
 
    rm /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi.grb
     rm /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootx64.efi.grb
     rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi.grb
     Mount sda1 on /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi
     ls sda1/efi: /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Boot
  
    *******lspci -nnk | grep -iA3 vga
     00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0e)
     DeviceName:  Onboard IGD
     Subsystem: Toshiba America Info Systems Atom Processor Z36xxx/Z37xxx Series Graphics & Display [1179:f910]
     Kernel driver in use: i915
     *******
  
    grub-install --version
     grub-install (GRUB) 2.02~beta2-36ubuntu3,grub-install (GRUB) 2.
  
    chroot /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d efibootmgr -v
     BootCurrent: 000A
     Timeout: 0 seconds
     BootOrder: 0002,0009,0000,0001,0006,0007,000A
     Boot0000* kali    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
     Boot0001* debian    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
     Boot0002* ubuntu    HD(1,GPT,f8c1e537-67ca-4ce5-bfa5-c5ffc3ca5f9c,0x800,0x100000)/File(EFIubuntugrubx64.efi)
     Boot0006* UEFI: IP6 Realtek PCIe FE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(f0761c8dfbc5,0)/IPv6([::]:<->[::]:,0,0)..BO
     Boot0007* UEFI: IP4 Realtek PCIe FE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(f0761c8dfbc5,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)..BO
     Boot0009* UEFI: Built-in EFI Shell     VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
     Boot000A* UEFI: TSSTcorp CDDVDW SU-208GB    PciRoot(0x0)/Pci(0x13,0x0)/Sata(1,65535,0)/CDROM(1,0xb0451,0x1280)..BO
  
    chroot /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d uname -r
     Kernel: 4.4.0-21-generic
  
    Reinstall the grub-efi-amd64-signed of sda2
     Installing for x86_64-efi platform.
     Installation finished. No error reported.
     grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
     mv 25_custom
     ls sda1/efi: /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Boot
     df /dev/sda1
     cp /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/ubuntu/shimx64.efi /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (& .grb)
     df /dev/sda1
     cp /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/ubuntu/shimx64.efi /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
     df /dev/sda1
     cp /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/ubuntu/shimx64.efi /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/Boot/bootx64.efi (& .grb)
     ls sda1/efi: /Microsoft/Boot/bootx64.efi.grb /Microsoft/Boot/bootx64.efi /Microsoft/Boot/bootmgfw.efi.grb /Microsoft/Boot/bootmgfw.efi /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Boot /Boot/bootx64.efi.grb /Boot/bootx64.efi
     Add /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi efi entries in /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/etc/grub.d/25_custom
     Adding custom /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/ubuntu/fwupx64.efi
     Adding custom /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d/boot/efi/EFI/ubuntu/MokManager.efi
  
    chroot /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d efibootmgr -v
     BootCurrent: 000A
     Timeout: 0 seconds
     BootOrder: 0002,0009,0000,0001,0006,0007,000A
     Boot0000* kali    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
     Boot0001* debian    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
     Boot0002* ubuntu    HD(1,GPT,f8c1e537-67ca-4ce5-bfa5-c5ffc3ca5f9c,0x800,0x100000)/File(EFIubuntugrubx64.efi)
     Boot0006* UEFI: IP6 Realtek PCIe FE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(f0761c8dfbc5,0)/IPv6([::]:<->[::]:,0,0)..BO
     Boot0007* UEFI: IP4 Realtek PCIe FE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(f0761c8dfbc5,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)..BO
     Boot0009* UEFI: Built-in EFI Shell     VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
     Boot000A* UEFI: TSSTcorp CDDVDW SU-208GB    PciRoot(0x0)/Pci(0x13,0x0)/Sata(1,65535,0)/CDROM(1,0xb0451,0x1280)..BO
  
    chroot /media/ubuntu/50ee09d6-0d07-4fe3-a340-a82b019a712d update-grub
     Generating grub configuration file ...
     Found linux image: /boot/vmlinuz-4.4.0-22-generic
     Found initrd image: /boot/initrd.img-4.4.0-22-generic
     Found linux image: /boot/vmlinuz-4.4.0-21-generic
     Found initrd image: /boot/initrd.img-4.4.0-21-generic
     Adding boot menu entry for EFI firmware configuration
     Unhide GRUB boot menu in sda2/boot/grub/grub.cfg
  
    Boot successfully repaired.
  
    You can now reboot your computer.
  
    paste.ubuntu.com ko (), using paste.debian
     paste.debian.net ko (), using paste2
  
                               
                       © 2006 - 2016 Paste2.org.
```
             [[IMG]http://static.paste2.org/templates/paste2/img/follow_us-a.png[/IMG]]("https://twitter.com/paste2org")
             


---

### Post by oldfred on 2016-05-22
Please use code tags for longer code or text.
With Boot-Repairs' Summary report better to just provide link.

Separate /boot partition was for some very old BIOS that could not boot from beyond 137GB on hard drive. Some users replaced smaller drives with larger drives that BIOS did not fully support. Have yet to see that issue with any UEFI system. Some servers or LVM may need a separate /boot, but not most desktops.

What brand/model system. Some violate UEFI spec that says not to use Description as part of UEFI boot. And of course only valid description is "Windows Boot Manager". 
Since only Ubuntu we can add a "Windows" description that really boots shimx64.efi.

sudo efibootmgr -v
         If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Confirm you have new entry:
sudo efibootmgr -v

      
 Codes from 
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

---

### Post by Omar_Jair on 2016-05-23
WoW, managed to solve the problem .___. i see that im not very clever when it comes to partitions, just had to put a boot flag on the ubuntu partition

---

### Post by oldfred on 2016-05-23
With UEFI & gpt, boot flag is only on the ESP - efi system partition. Or your sda1.
I would not expect system to boot at all if boot flag on the Linux ext4 partition.

---

### Post by Omar_Jair on 2016-05-25
Sadly for me i think it is a problem everytime i have to reinstall ubuntu, i can't seem to understand partitions too well, do you have any easy steps? im tired of messing around with partitions till i manage to boot.

---

### Post by oldfred on 2016-05-25
Major difference now on whether UEFI or BIOS install.
BIOS is the 35 year old original PC boot that uses MBR(msdos) partitioning.
UEFI is the newer boot system replacing BIOS that uses gpt(GUID) partitioning.
How you boot install media is then how it installs and drive partitioning needs to match or drive is totally reformatted.

Windows will only boot in UEFI mode from gpt, or only with BIOS from MBR.
You generally want Ubuntu in same boot mode as Windows, so you can dual boot from grub menu.

       gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record

[/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 

With UEFI, it also has CSM.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

So with most UEFI based systems, you have three boot modes, UEFI with Secure boot, UEFI, and CSM.
If you have Secure boot on, standard UEFI or CSM will give the error on no valid boot. But you may get similar message if you install in CSM mode, but try to boot in UEFI mode or vice-versa. 
How you boot install media is how it installs, but that may not be the current default setting in UEFI, so you have to make sure UEFI and your install method match.

    [URL="http://en.wikipedia.org/wiki/Master_boot_record"]
      [/URL]
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/353683/uefi-partitioning-for-dummies](http://askubuntu.com/questions/353683/uefi-partitioning-for-dummies)

Even more info in link below in my signature:
 

    [URL="http://en.wikipedia.org/wiki/Master_boot_record"]
[/URL]

---

