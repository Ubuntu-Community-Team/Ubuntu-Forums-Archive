---
title: "Upgraded from 14.10 to 15.04 but only loads 14.10"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2015-04-30
I had the new version, upgrade available message and went ahead with it.  After reboot, my PC seems to only load 14.10.  I have tried to configure GRUB but to no avail.

With ```
lsb_release -a

```
I get: ```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarchDistributor ID:    UbuntuDescription:    Ubuntu 14.10Release:    14.10Codename:    utopic
```

Boot Info script
```
                  Boot Info Script 0.61      [1 April 2012]

============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of     the same hard drive for core.img. core.img is at this location and looks     in partition 135 for . => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of     the same hard drive for core.img. core.img is at this location and looks     in partition 129 for .
sda1: __________________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows Vista/7: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:  Windows 7    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda2: __________________________________________________________________________
    File system:       Extended Partition    Boot sector type:  Unknown    Boot sector info: 
sda5: __________________________________________________________________________
    File system:       ext4    Boot sector type:  Grub2 (v1.99)    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5                        and looks at sector 422062784 of the same hard drive                        for core.img. core.img is at this location and looks                        in partition 135 for .    Operating System:  Debian GNU/Linux 8    Boot files:        /boot/grub/grub.cfg /etc/fstab
sda4: __________________________________________________________________________
    File system:       swap    Boot sector type:  -    Boot sector info: 
sdb1: __________________________________________________________________________
    File system:       ext4    Boot sector type:  -    Boot sector info:     Operating System:      Boot files:        
sdb3: __________________________________________________________________________
    File system:       ntfs    Boot sector type:  Windows Vista/7: NTFS    Boot sector info:  No errors found in the Boot Parameter Block.    Operating System:      Boot files:        
sdb4: __________________________________________________________________________
    File system:       Extended Partition    Boot sector type:  Unknown    Boot sector info: 
sdb5: __________________________________________________________________________
    File system:       ext4    Boot sector type:  -    Boot sector info:     Operating System:      Boot files:        
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectorsUnits: sectors of 1 * 512 = 512 bytesSector size (logical/physical): 512 bytes / 512 bytesI/O size (minimum/optimal): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1               2,048   350,824,447   350,822,400   7 NTFS / exFAT / HPFS/dev/sda2         350,826,494   455,583,743   104,757,250   5 Extended/dev/sda5    *    350,826,496   455,583,743   104,757,248  83 Linux/dev/sda4         455,583,744   488,396,799    32,813,056  82 Linux swap / Solaris

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500106780160 bytes, 976771055 sectorsUnits: sectors of 1 * 512 = 512 bytesSector size (logical/physical): 512 bytes / 512 bytesI/O size (minimum/optimal): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1                  63   566,050,815   566,050,753  83 Linux/dev/sdb3         566,050,816   771,809,279   205,758,464   7 NTFS / exFAT / HPFS/dev/sdb4         771,810,795   976,768,064   204,957,270   5 Extended/dev/sdb5         771,813,376   976,766,975   204,953,600  83 Linux

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/sda1        4AE5E83A4716097B                       ntfs       Windows/dev/sda4        c434799f-bdbe-4d21-ac56-9bef10ec2559   swap       /dev/sda5        92b22452-9630-4e73-a305-c86157428b5b   ext4       /dev/sdb1        9972d3c0-79f8-4baa-ae8f-ccbc63f630a8   ext4       Backup/dev/sdb3        2104697C2776893B                       ntfs       Documents/dev/sdb5        22c1ecdc-2fc5-4b0d-8e26-92d62a48c567   ext4       home
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)/dev/sdb1        /media/Backup            ext4       (rw,relatime,data=ordered)/dev/sdb3        /media/Documents         fuseblk    (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)/dev/sdb5        /home                    ext4       (rw,nosuid,nodev,relatime,data=ordered)

=========================== sda5/boot/grub/grub.cfg: ===========================
--------------------------------------------------------------------------------## DO NOT EDIT THIS FILE## It is automatically generated by grub-mkconfig using templates# from /etc/grub.d and settings from /etc/default/grub#
### BEGIN /etc/grub.d/00_header ###if [ -s $prefix/grubenv ]; then  set have_grubenv=true  load_envfiif [ "${next_entry}" ] ; then   set default="${next_entry}"   set next_entry=   save_env next_entry   set boot_once=trueelse   set default="0"fi
if [ x"${feature_menuentry_id}" = xy ]; then  menuentry_id_option="--id"else  menuentry_id_option=""fi
export menuentry_id_option
if [ "${prev_saved_entry}" ]; then  set saved_entry="${prev_saved_entry}"  save_env saved_entry  set prev_saved_entry=  save_env prev_saved_entry  set boot_once=truefi
function savedefault {  if [ -z "${boot_once}" ]; then    saved_entry="${chosen}"    save_env saved_entry  fi}function recordfail {  set recordfail=1  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi}function load_video {  if [ x$feature_all_video_module = xy ]; then    insmod all_video  else    insmod efi_gop    insmod efi_uga    insmod ieee1275_fb    insmod vbe    insmod vga    insmod video_bochs    insmod video_cirrus  fi}
insmod part_msdosinsmod ext2set root='hd0,msdos5'if [ x$feature_platform_search_hint = xy ]; then  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5belse  search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5bfiif loadfont /boot/grub/unicode.pf2 ; then  set gfxmode=1280x1024  load_video  insmod gfxterm  set locale_dir=$prefix/locale  set lang=en_GB  insmod gettextfiterminal_output gfxtermif [ "${recordfail}" = 1 ] ; then  set timeout=-1else  if [ x$feature_timeout_style = xy ] ; then    set timeout_style=menu    set timeout=5  # Fallback normal timeout code in case the timeout_style feature is  # unavailable.  else    set timeout=5  fifi### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###insmod part_msdosinsmod ntfsset root='hd1,msdos3'if [ x$feature_platform_search_hint = xy ]; then  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2104697C2776893Belse  search --no-floppy --fs-uuid --set=root 2104697C2776893Bfiinsmod jpegif background_image /Documents/Dropbox/Images for appearence/IMG_20110904_154245.jpg; then  set color_normal=light-green/white  set color_highlight=red/dark-grayelse  set menu_color_normal=white/black  set menu_color_highlight=black/light-grayfi### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###function gfxmode {    set gfxpayload="${1}"    if [ "${1}" = "keep" ]; then        set vt_handoff=vt.handoff=7    else        set vt_handoff=    fi}if [ "${recordfail}" != 1 ]; then  if [ -e ${prefix}/gfxblacklist.txt ]; then    if hwmatch ${prefix}/gfxblacklist.txt 3; then      if [ ${match} = 0 ]; then        set linux_gfx_mode=keep      else        set linux_gfx_mode=text      fi    else      set linux_gfx_mode=text    fi  else    set linux_gfx_mode=keep  fielse  set linux_gfx_mode=textfiexport linux_gfx_modemenuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-92b22452-9630-4e73-a305-c86157428b5b' {    recordfail    load_video    gfxmode $linux_gfx_mode    insmod gzio    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi    insmod part_msdos    insmod ext2    set root='hd0,msdos5'    if [ x$feature_platform_search_hint = xy ]; then      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b    else      search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b    fi    linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro  quiet splash $vt_handoff    initrd    /boot/initrd.img-3.19.0-15-generic}submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-92b22452-9630-4e73-a305-c86157428b5b' {    menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-92b22452-9630-4e73-a305-c86157428b5b' {        recordfail        load_video        gfxmode $linux_gfx_mode        insmod gzio        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi        insmod part_msdos        insmod ext2        set root='hd0,msdos5'        if [ x$feature_platform_search_hint = xy ]; then          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b        else          search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b        fi        echo    'Loading Linux 3.19.0-15-generic ...'        linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro  quiet splash $vt_handoff        echo    'Loading initial ramdisk ...'        initrd    /boot/initrd.img-3.19.0-15-generic    }    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-92b22452-9630-4e73-a305-c86157428b5b' {        recordfail        load_video        gfxmode $linux_gfx_mode        insmod gzio        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi        insmod part_msdos        insmod ext2        set root='hd0,msdos5'        if [ x$feature_platform_search_hint = xy ]; then          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b        else          search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b        fi        echo    'Loading Linux 3.19.0-15-generic ...'        linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro  quiet splash $vt_handoff init=/sbin/upstart        echo    'Loading initial ramdisk ...'        initrd    /boot/initrd.img-3.19.0-15-generic    }    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-92b22452-9630-4e73-a305-c86157428b5b' {        recordfail        load_video        insmod gzio        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi        insmod part_msdos        insmod ext2        set root='hd0,msdos5'        if [ x$feature_platform_search_hint = xy ]; then          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b        else          search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b        fi        echo    'Loading Linux 3.19.0-15-generic ...'        linux    /boot/vmlinuz-3.19.0-15-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro recovery nomodeset         echo    'Loading initial ramdisk ...'        initrd    /boot/initrd.img-3.19.0-15-generic    }    menuentry 'Ubuntu, with Linux 3.16.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-advanced-92b22452-9630-4e73-a305-c86157428b5b' {        recordfail        load_video        gfxmode $linux_gfx_mode        insmod gzio        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi        insmod part_msdos        insmod ext2        set root='hd0,msdos5'        if [ x$feature_platform_search_hint = xy ]; then          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b        else          search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b        fi        echo    'Loading Linux 3.16.0-34-generic ...'        linux    /boot/vmlinuz-3.16.0-34-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro  quiet splash $vt_handoff        echo    'Loading initial ramdisk ...'        initrd    /boot/initrd.img-3.16.0-34-generic    }    menuentry 'Ubuntu, with Linux 3.16.0-34-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-init-upstart-92b22452-9630-4e73-a305-c86157428b5b' {        recordfail        load_video        gfxmode $linux_gfx_mode        insmod gzio        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi        insmod part_msdos        insmod ext2        set root='hd0,msdos5'        if [ x$feature_platform_search_hint = xy ]; then          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b        else          search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b        fi        echo    'Loading Linux 3.16.0-34-generic ...'        linux    /boot/vmlinuz-3.16.0-34-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro  quiet splash $vt_handoff init=/sbin/upstart        echo    'Loading initial ramdisk ...'        initrd    /boot/initrd.img-3.16.0-34-generic    }    menuentry 'Ubuntu, with Linux 3.16.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-recovery-92b22452-9630-4e73-a305-c86157428b5b' {        recordfail        load_video        insmod gzio        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi        insmod part_msdos        insmod ext2        set root='hd0,msdos5'        if [ x$feature_platform_search_hint = xy ]; then          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  92b22452-9630-4e73-a305-c86157428b5b        else          search --no-floppy --fs-uuid --set=root 92b22452-9630-4e73-a305-c86157428b5b        fi        echo    'Loading Linux 3.16.0-34-generic ...'        linux    /boot/vmlinuz-3.16.0-34-generic root=UUID=92b22452-9630-4e73-a305-c86157428b5b ro recovery nomodeset         echo    'Loading initial ramdisk ...'        initrd    /boot/initrd.img-3.16.0-34-generic    }}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/30_os-prober ###menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-4AE5E83A4716097B' {    insmod part_msdos    insmod ntfs    set root='hd0,msdos1'    if [ x$feature_platform_search_hint = xy ]; then      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4AE5E83A4716097B    else      search --no-floppy --fs-uuid --set=root 4AE5E83A4716097B    fi    parttool ${root} hidden-    chainloader +1}set timeout_style=menuif [ "${timeout}" = 0 ]; then  set timeout=10fi### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/30_uefi-firmware ###### END /etc/grub.d/30_uefi-firmware ###
### BEGIN /etc/grub.d/40_custom #### This file provides an easy way to add custom menu entries.  Simply type the# menu entries you want to add after this comment.  Be careful not to change# the 'exec tail' line above.### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###if [ -f  ${config_directory}/custom.cfg ]; then  source ${config_directory}/custom.cfgelif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then  source $prefix/custom.cfg;fi### END /etc/grub.d/41_custom ###--------------------------------------------------------------------------------
=============================== sda5/etc/fstab: ================================
--------------------------------------------------------------------------------# /etc/fstab: static file system information.## Use 'blkid' to print the universally unique identifier for a# device; this may be used with UUID= as a more robust way to name devices# that works even if disks are added and removed. See fstab(5).## <file system> <mount point>   <type>  <options>       <dump>  <pass># / was on /dev/sda5 during installationUUID=92b22452-9630-4e73-a305-c86157428b5b /               ext4    errors=remount-ro 0       1# swap was on /dev/sda4 during installationUUID=c434799f-bdbe-4d21-ac56-9bef10ec2559 none            swap    sw              0       0
# /home was on /dev/sdb5 during installationUUID=22c1ecdc-2fc5-4b0d-8e26-92d62a48c567     /home               ext4    nodev,nosuid            1       2
# /media/Documents is on /dev/sdb3UUID=2104697C2776893B                             /media/Documents             ntfs    defaults,locale=en_GB.utf8      0       0
# /media/Backup was on /dev/sdb1 during installationUUID=9972d3c0-79f8-4baa-ae8f-ccbc63f630a8    /media/Backup        ext4    defaults        0    2
# /media/Documents is on /dev/sda1#UUID=4AE5E83A4716097B                             /media/Windows             ntfs    defaults,locale=en_GB.utf8      0       0
# 85 is the USB group#none     /proc/bus/usb     usbfs      devgid=85,devmode=666    0    0--------------------------------------------------------------------------------
=================== sda5: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)

======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sda2

Unknown BootLoader on sdb4


========= Devices which don't seem to have a corresponding hard drive: =========
sdc sdd sde sdf 
=============================== StdErr Messages: ===============================
hexdump: /dev/sda2: No such device or addresshexdump: /dev/sda2: No such device or addresscat: /tmp/BootInfo-5BoEaiht/Tmp_Log: No such file or directoryhexdump: /dev/sdb4: No such device or addresshexdump: /dev/sdb4: No such device or address
```

GRUB says it is booting 3.19.0.14 which I thought was 15.04......

Any ideas, please.

---

### Post by TheFadedBrit on 2015-04-30
Have you Tried to upgrade using the disk before ive found this is more stable as i think the built in one is slower and alot more buggy?

---

### Post by Jonners59 on 2015-04-30
Not this time.  The problem is keeping my installation and configs as is and not starting from scratch.  Bit late now.  How can I fix things????

---

### Post by Jonners59 on 2015-04-30
Any help please...???????

---

### Post by QIII on 2015-04-30
Please be patient.  The forum is populated by volunteer users who give their time as they have it to give.  They live in all time zones around the globe.  It is not reasonable to expect that just the right person with just the right answer will even be aware of your thread immediately after you have posted it.

If you don't have an answer in another 12 hours, feel free to bump the thread to expose it to users in other time zones.

---

### Post by grahammechanical on 2015-04-30
The command lsb_release -a prints to the screen the file /etc/lsb-release which should read in Gedit

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"

And this is what lsb_release - a should show
> 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

It is this file that is used for the entry in the Grub boot menu. What does the actual lsb-release file read? What does the boot menu say? What does the login screen say? I have no idea why the command lsb_release -a is giving that output.

Perhaps you have lsb modules installed.

[http://askubuntu.com/questions/230766/how-lsb-module-affects-system-and-can-be-made-available-to-the-system](http://askubuntu.com/questions/230766/how-lsb-module-affects-system-and-can-be-made-available-to-the-system)

What does this say?

```
cat /etc/os-release
```

it should say

> NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

Regards.

---

### Post by Jonners59 on 2015-05-01
[COLOR=#000000]grahammechanical
Thanks for getting back.  I have tried the cmd that you suggested and added the outputs FYI.  I have also added two other notes/observations.  Hope this sheds some light on this.

[/COLOR]This is what I have...

```
lsb_release - a

```
```
Output =Usage: lsb_release [options]


lsb_release: error: No arguments are permitted

```


Actual file /etc/lsb-release, reads (opened with gedit) =
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"

```

```
cat /etc/os-release

```
Output =
```
PRETTY_NAME="Debian GNU/Linux 8 (jessie)"
NAME="Debian GNU/Linux"
VERSION_ID="8"
VERSION="8 (jessie)"
ID=debian
HOME_URL="http://www.debian.org/"
SUPPORT_URL="http://www.debian.org/support/"
BUG_REPORT_URL="https://bugs.debian.org/"

```

Reading from Grub Customizer which has the same text as the Grub menu at launch it reads:
Ubuntu, with Linux 3.19.0-15-generic
Ubuntu, with Linux 3.19.0-15-generic (upstart)
Ubuntu, with Linux 3.19.0-15-generic (recovery)

I do not know if it is related but two other issues exist since the upgrade:
1. Everything is owned by ROOT, which is a pain and I can not change ownership.
2. When I do updates or add sw I get
```
dpkg: error processing package urfkill (--configure): subprocess installed post-installation script returned error exit status 102
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-system-settings:
 ubuntu-system-settings depends on urfkill; however:
  Package urfkill is not configured yet.


dpkg: error processing package ubuntu-system-settings (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of unity8:
 unity8 depends on qtdeclarative5-ubuntu-telephony0.1; however:
  Package qtdeclarative5-ubuntu-telephony0.1:amd64 is not configured yet.
 unity8 depends on ubuntu-system-settings; however:
  Package ubuntu-system-settings is not configured yet.


dpkg: error processing package unity8 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of indicator-network:
 indicator-network depends on ofono; however:
  Package ofono is not configured yet.
 indicator-network depends on unity8 (>= 8.00+14.10.20140806); however:
  Package unity8 is not configured yet.
 indicator-network depends on urfkill; however:
  Package urfkill is not configured yet.


dpkg: error processing package indicator-network (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-system-settings-online-accounts:
 ubuntu-system-settings-online-accounts depends on ubuntu-system-settings; however:
  Package ubuntu-system-settings is not configured yet.


dpkg: error processing package ubuntu-system-settings-online-accounts (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of account-plugin-ubuntuone:
 account-plugin-ubuntuone depends on ubuntu-system-settings-online-accounts; however:
  Package ubuntu-system-settings-online-accounts is not configured yet.


dpkg: error processing package account-plugin-ubuntuone (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of unity-scope-click:
 unity-scope-click depends on account-plugin-ubuntuone; however:
  Package account-plugin-ubuntuone is not configured yet.


dpkg: error processing package unity-scope-click (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up plexmediaserver-ros6 (0.9.7.22.510-8faeab3) ...
chown: invalid user: ‘admin:admin’
dpkg: error processing package plexmediaserver-ros6 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of plexmediaserver-ros6-binaries:
 plexmediaserver-ros6-binaries depends on plexmediaserver-ros6 (>= 0.9.7.22.510-8faeab3); however:
  Package plexmediaserver-ros6 is not configured yet.


dpkg: error processing package plexmediaserver-ros6-binaries (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 ofono
 telepathy-ofono
 telephony-service
 qtdeclarative5-ubuntu-telephony0.1:amd64
 urfkill
 ubuntu-system-settings
 unity8
 indicator-network
 ubuntu-system-settings-online-accounts
 account-plugin-ubuntuone
 unity-scope-click
 plexmediaserver-ros6
 plexmediaserver-ros6-binaries
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TheFadedBrit on 2015-05-01
if it is only registering as you having 14.10 then get the disk install and try upgrading from there it will most likely fix your problem.

---

### Post by bapoumba on 2015-05-01
You are most likely using ppas that give you the dependency problems.
Please backup anything you'd cry for if you'd loose.

If not too late, you can revert the packages back to their trusty versions using ppa-purge (please see my sig) if you already have it installed. If not, you may not be able to install it. Best would be to disable all your ppas, cross your fingers and upgrade to utopic. The package manager may be too unhappy for that.

in the mean time, please post the output to : 
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by Jonners59 on 2015-05-07
OK. I sorted it by downloading the iso and burning to a disk, and installing that way.  I chose "other" in the options and selected my /home, which is separate without formatting.

It installed Unity, and from there I installed xfce4.  I now have a machine working, though it did take a lot of jigging and re-installing apps, such as crossover to get me back to where I was.  ONLY issue now is that the xfce does not load correctly, but I have raised a new thread for that, so I shall close this as solved using a burnt DVD.

---

