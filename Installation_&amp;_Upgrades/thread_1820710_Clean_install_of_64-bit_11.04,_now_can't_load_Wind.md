---
title: "Clean install of 64-bit 11.04, now can't load Windows Vista"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by jeffmartin on 2011-08-08
Hey there,

I have been running a dual boot of Vista and Ubuntu for several years now.  Every time I upgrade or reinstall Ubuntu, I run into the same "grub_rescue>" problem, so I am familiar (almost memorized) the solution to it.  This time, I changed my routine up a bit by re-structuring the partitions and the problem is slightly different.  I have my Vista partition, followed by /, /home, and swap.  The second drive is my data drive.

```
sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7122a59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10578    84967392+   7  HPFS/NTFS
/dev/sda2           10578       15442    39062528   83  Linux
/dev/sda3           15442       18481    24414208   83  Linux
/dev/sda4           18481       19458     7845888   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00008065

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
```Installation went perfectly and I immediately applied the now all-too-familiar grub_rescue> fix.  After restarting, I immediately booted into ubuntu and started downloading my standard set of applications.  I also installed grub-customizer and burg, thinking I'd try out a graphical bootloader this time.  Not sure if burg made any difference in this problem or not, but since it was different from my normal routine, thought I should mention it.

Burg installation and config went fine and I used Grub Customizer to change the boot entry names to something a little less arcane, as well as changing the order and default entry.  On restart, I had a beautiful bootloader with 2 options: Windows and Ubuntu - yay!  Unfortunately, that's the end of the good news.  Tried loading Windows and I now get a screen with nothing but a blinking cursor, but Ubuntu loads just fine.

Things I have tried:
Uninstalled burg
Uninstalled grub
Uninstalled grub-pc
Reinstalled grub-pc
Repaired MBR using Vista OEM CD
Uninstalled grub-pc again
Reinstalled grub-pc again
Cursed at screen again and again
...there's a couple of things I tried in here that I'm sure I forgot...
tried the grub_rescue> fix again (detailed below)
...came here looking for help!

Here's the fix I keep referring to as the grub_rescue> fix:
```
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
sudo apt-get install grub-pc
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo grub-install /dev/sda
sudo update-grub
```One thing I did notice from the boot info script was that I have 2 (or 3) versions of Grub installed apparently - one on /dev/sda, and 1 (or 2) on /dev/sdb.  I have tried using apt-get to purge grub and grub-pc, so I'm not sure why it keeps telling me I have it installed in both places with different versions, no less.  In addition, it displays the burg.cfg from /dev/sda2, even though I purged burg as well.  Any help would be appreciated!

Here's my boot info script results.txt (current state of my computer):
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 148758361 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   169,934,847   169,934,785   7 NTFS / exFAT / HPFS
/dev/sda2         169,934,848   248,059,903    78,125,056  83 Linux
/dev/sda3         248,059,904   296,888,319    48,828,416  83 Linux
/dev/sda4         296,888,320   312,580,095    15,691,776  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        060C4BFC0C4BE4F1                       ntfs       
/dev/sda2        db3d681a-56ec-491e-84a9-dc5b49e4a631   ext4       
/dev/sda3        5e0a136f-4517-4f65-b747-4db693560c89   ext4       
/dev/sda4        7272de9f-2304-4e57-a228-3684a788f6bb   swap       
/dev/sdb1        17C7E3216A5E36F3                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /home                    ext4       (rw,commit=0)


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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root db3d681a-56ec-491e-84a9-dc5b49e4a631
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root db3d681a-56ec-491e-84a9-dc5b49e4a631
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 060C4BFC0C4BE4F1
    chainloader +1
}
### END /etc/grub.d/10_os-prober ###

### BEGIN /etc/grub.d/20_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root db3d681a-56ec-491e-84a9-dc5b49e4a631
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=db3d681a-56ec-491e-84a9-dc5b49e4a631 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
### END /etc/grub.d/20_linux_proxy ###
--------------------------------------------------------------------------------

=========================== sda2/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
set gfxmode=1680x1050x24
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set db3d681a-56ec-491e-84a9-dc5b49e4a631
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=10
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_os-prober_proxy ###
menuentry "Windows" --class windows --class os {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 060c4bfc0c4be4f1
    chainloader +1
}
### END /etc/burg.d/10_os-prober_proxy ###

### BEGIN /etc/burg.d/30_linux_proxy ###
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set db3d681a-56ec-491e-84a9-dc5b49e4a631
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=db3d681a-56ec-491e-84a9-dc5b49e4a631 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
### END /etc/burg.d/30_linux_proxy ###

### BEGIN /etc/burg.d/40_custom_proxy ###
### END /etc/burg.d/40_custom_proxy ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda3       /home           ext4    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 103.386852264 = 111.010787328  boot/burg/burg.cfg                             1
 103.251365662 = 110.865309696  boot/burg/core.img                             1
 103.250541687 = 110.864424960  boot/grub/core.img                             1
 103.400394440 = 111.025328128  boot/grub/grub.cfg                             1
  82.412422180 = 88.489664512   boot/initrd.img-2.6.38-10-generic              2
 102.359375000 = 109.907542016  boot/initrd.img-2.6.38-8-generic               2
  81.687812805 = 87.711621120   boot/vmlinuz-2.6.38-10-generic                 1
 103.351707458 = 110.973050880  boot/vmlinuz-2.6.38-8-generic                  1
  82.412422180 = 88.489664512   initrd.img                                     2
 102.359375000 = 109.907542016  initrd.img.old                                 2
  81.687812805 = 87.711621120   vmlinuz                                        1
 103.351707458 = 110.973050880  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by mikewhatever on 2011-08-08
Try running **sudo update-grub** from the Ubuntu installation. That should pick up Vista and generate an entry in grub.cfg - there is none now.

/dev/sda, dev/sdb, etc are the MBRs of the respective hdds. They have nothing to do with the package manager, and purging grub would not overwrite them. It's ok to just leave them be.

---

### Post by jeffmartin on 2011-08-08
Thanks for the reply.  Windows Vista is actually a menu entry as stated in my previous post.  When I select that entry, however, it gives me a black screen with an underscore blinking cursor.  It should be noted that when I select Ubuntu from the grub list, the same screen happens for a few seconds before I get the login screen.  My best guess is that Grub is not chainloading to the Windows bootloader, but I don't know enough about the process to know how to fix it.

I have run 'sudo update-grub' previously as stated in my post, but I did it again, just in case.  Here's the updated boot info script results.  I didn't notice any difference in the resulting list, and no change in the behavior of the Windows Vista menu item.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 148758361 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   169,934,847   169,934,785   7 NTFS / exFAT / HPFS
/dev/sda2         169,934,848   248,059,903    78,125,056  83 Linux
/dev/sda3         248,059,904   296,888,319    48,828,416  83 Linux
/dev/sda4         296,888,320   312,580,095    15,691,776  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        060C4BFC0C4BE4F1                       ntfs       
/dev/sda2        db3d681a-56ec-491e-84a9-dc5b49e4a631   ext4       
/dev/sda3        5e0a136f-4517-4f65-b747-4db693560c89   ext4       
/dev/sda4        7272de9f-2304-4e57-a228-3684a788f6bb   swap       
/dev/sdb1        17C7E3216A5E36F3                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/060C4BFC0C4BE4F1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /home                    ext4       (rw,commit=0)
/dev/sdb1        /media/17C7E3216A5E36F3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root db3d681a-56ec-491e-84a9-dc5b49e4a631
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root db3d681a-56ec-491e-84a9-dc5b49e4a631
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 060C4BFC0C4BE4F1
    chainloader +1
}
### END /etc/grub.d/10_os-prober ###

### BEGIN /etc/grub.d/20_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root db3d681a-56ec-491e-84a9-dc5b49e4a631
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=db3d681a-56ec-491e-84a9-dc5b49e4a631 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
### END /etc/grub.d/20_linux_proxy ###
--------------------------------------------------------------------------------

=========================== sda2/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
set gfxmode=1680x1050x24
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set db3d681a-56ec-491e-84a9-dc5b49e4a631
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=10
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_os-prober_proxy ###
menuentry "Windows" --class windows --class os {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 060c4bfc0c4be4f1
    chainloader +1
}
### END /etc/burg.d/10_os-prober_proxy ###

### BEGIN /etc/burg.d/30_linux_proxy ###
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set db3d681a-56ec-491e-84a9-dc5b49e4a631
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=db3d681a-56ec-491e-84a9-dc5b49e4a631 ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
### END /etc/burg.d/30_linux_proxy ###

### BEGIN /etc/burg.d/40_custom_proxy ###
### END /etc/burg.d/40_custom_proxy ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda3       /home           ext4    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 103.386852264 = 111.010787328  boot/burg/burg.cfg                             1
 103.251365662 = 110.865309696  boot/burg/core.img                             1
 103.250541687 = 110.864424960  boot/grub/core.img                             1
 103.425624847 = 111.052419072  boot/grub/grub.cfg                             1
  82.412422180 = 88.489664512   boot/initrd.img-2.6.38-10-generic              2
 102.359375000 = 109.907542016  boot/initrd.img-2.6.38-8-generic               2
  81.687812805 = 87.711621120   boot/vmlinuz-2.6.38-10-generic                 1
 103.351707458 = 110.973050880  boot/vmlinuz-2.6.38-8-generic                  1
  82.412422180 = 88.489664512   initrd.img                                     2
 102.359375000 = 109.907542016  initrd.img.old                                 2
  81.687812805 = 87.711621120   vmlinuz                                        1
 103.351707458 = 110.973050880  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by jeffmartin on 2011-08-08
For visual clarification, a couple of screenshots, first of the grub menu items, and then the screen that results from selecting either Windows Vista or Ubuntu.  The difference between the two is that Ubuntu displays a login screen after a few seconds, while Vista doesn't display anything.  I even let it sit at that screen while I ran to the grocery store, and it hadn't changed.

---

### Post by mikewhatever on 2011-08-08
I am sorry, there was a Vista entry in /boot/grub/grub.cfg. It's above the Ubuntu entries, and I am used to see it below. Let's wait for some experts to look at it.

---

### Post by jeffmartin on 2011-08-08
No worries, I appreciate the stab at it!  My wife and I share this computer, and she's definitely not computer-savvy, so I put Windows first (and default) so she could just turn on the computer and not have to worry about anything else.

Back to the problem at hand, I was looking a bit more closely at the menu entry details, hoping to find something wrong, but I don't know enough about the format.  Does this look right?

```
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 060C4BFC0C4BE4F1
    chainloader +1
}
```

Only other thing I can think of is that the Windows bootloader somehow got damaged when I changed the Windows partition size and as a result, it's not loading like it should.  Anyone else have any theories?

---

### Post by mikewhatever on 2011-08-08
It seems to look ok, but the problem is a bit complicated because of burg and easyBCD additions. I don't know enough about these.

---

### Post by oldfred on 2011-08-08
If you resized Vista it will want to run chkdsk which also resets some parameters in the windows partition boot sector as that has to know the correct size of the partition.

If you have a windows repair CD I would run chkdsk and possibly fixboot.

chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector

You may be able to get to a windows recovery mode with f8 just after clicking in grub's windows entry. Some reported it took many tries as the timing is very quick.

---

### Post by jeffmartin on 2011-08-08
> **oldfred said:**
> If you resized Vista it will want to run chkdsk which also resets some parameters in the windows partition boot sector as that has to know the correct size of the partition.

If you have a windows repair CD I would run chkdsk and possibly fixboot.

chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector

You may be able to get to a windows recovery mode with f8 just after clicking in grub's windows entry. Some reported it took many tries as the timing is very quick.

Thanks for the reply.  I did run the bootrec.exe /fixboot and bootrec.exe /fixmbr, didn't seem to make a difference.  I also ran the disk repair program which said that it couldn't continue because of an error.  Unfortunately I didn't write it down at the time, but I will try it again when I get home tonight, along with the chkdsk.

---

### Post by jeffmartin on 2011-08-09
UPDATE:
Ok, here's what I did tonight to try to fix the problem...

Booted with Windows disk and ran the following commands:

```
chkdsk C: /r /f #ran it three times, no errors on final run
bootrec.exe /fixboot
bootrec.exe /fixmbr
```Restarted computer, crossed fingers, hoped for Windows bootloader...got NO bootloader, just a blinking cursor where grub would normally load.

Booted with Natty LiveCD and ran the following commands:

```
sudo apt-get purge grub-pc
sudo apt-get install grub-pc
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo grub-install /dev/sda
sudo update-grub
```Restarted computer, crossed fingers, hoped for Grub...and got it.  But, selecting Windows from the list gives me the same blinking cursor that I had when I first posted.  Heh, looks like I'm back where I started.

---

### Post by YannBuntu on 2011-08-09
Hello,

If I understand correctly, since yesterday you could not get access to Windows anytime, even after repairing with the Windows repair CD ?

even without GRUB (directly BIOS -> Windows) ?

---

### Post by jeffmartin on 2011-08-09
> **YannBuntu said:**
> Hello,

If I understand correctly, since yesterday you could not get access to Windows anytime, even after repairing with the Windows repair CD ?

even without GRUB (directly BIOS -> Windows) ?

That's correct, no access to Windows, even after the repair CD.  I am not familiar with how to go directly from BIOS to Windows - can you explain what I need to try?

---

### Post by oldfred on 2011-08-09
When you ran fixMBR you replaced grub with the windows boot loader in the MBR, so you booted with windows directly to the Vista install with the boot flag.

Then when you reinstalled grub it booted grub and then grub chainloaded to the Vista partition (does not need boot flag, but jumps to windows just like the windows boot loader does). 

So if windows did not work directly then it will not work from grub.

You have gone thru most of the fixes, but this is the full list.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

Noticed your Vista is now starting at sector 63 which is what XP or older versions of Ubuntu/gparted used. New versions of gparted would not move it, but older versions did and then you had to run fixBoot to correct the new entry. Did you install Vista over an XP install or did it get moved?

---

### Post by jeffmartin on 2011-08-10
> **oldfred said:**
> When you ran fixMBR you replaced grub with the windows boot loader in the MBR, so you booted with windows directly to the Vista install with the boot flag.

Then when you reinstalled grub it booted grub and then grub chainloaded to the Vista partition (does not need boot flag, but jumps to windows just like the windows boot loader does). 

So if windows did not work directly then it will not work from grub.

You have gone thru most of the fixes, but this is the full list.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

Noticed your Vista is now starting at sector 63 which is what XP or older versions of Ubuntu/gparted used. New versions of gparted would not move it, but older versions did and then you had to run fixBoot to correct the new entry. Did you install Vista over an XP install or did it get moved?

My Vista partition is pretty old - I think it may even be the original that I installed when I built the computer.  Every upgrade or reinstall of Ubuntu has kinda been worked around that partition because I would rather mess up my Ubuntu install since it's easier to fix, heh.  I think I did the original partition scheme with the version of gparted that came with either Gutsy or Hardy, not sure which.

Anyways, I will run those commands and report back - there's a couple in there I didn't try.

---

### Post by jeffmartin on 2011-08-10
> **hansherdel said:**
> Its seems like the problem was solved. I have here a tool that converts YouTube songs and music into MP3. [YouTube to MP3 Converter]("http://www.flockee.com/static/youtube-to-mp3/?category=youtube-to-mp3-converter")

I'm sorry, I fail to see how this relates to the problem, nor has the problem been solved.  Perhaps you could enlighten me?

UPDATE:
@oldfred
I booted from the Vista CD and ran the repair commands you listed in that order.  While it didn't help, it was informative.  Apparently, I have 0 Windows installations - not really sure how that happened.  I guess my next step is to run a Restore.  Are there any issues I should know about before doing that?  The main problem I foresee is having to restore grub afterwards, which is not really a problem.

---

### Post by oldfred on 2011-08-10
For whatever reason it is not seeing your Windows install. That often happens with some sort of file/configuration issue, but the repairs usually fix it. I might try them one more time, as some seem to depend on others and each needs to be run before the other to totally fix it.

Boot script seemed to show all the boot files, NTFS partition, at least part of NTFS partition boot sector was correct, so not too much can be wrong. But we have seen where for whatever reason fixes may not work. Often users just give up and re-install so we never really know what is wrong.

---

### Post by jeffmartin on 2011-08-10
> **oldfred said:**
> For whatever reason it is not seeing your Windows install. That often happens with some sort of file/configuration issue, but the repairs usually fix it. I might try them one more time, as some seem to depend on others and each needs to be run before the other to totally fix it.

Boot script seemed to show all the boot files, NTFS partition, at least part of NTFS partition boot sector was correct, so not too much can be wrong. But we have seen where for whatever reason fixes may not work. Often users just give up and re-install so we never really know what is wrong.

Well, I'm not on a timetable so I can test whatever you want to suggest.  Should I run through those Windows command line options again?

---

### Post by oldfred on 2011-08-10
It cannot hurt at this point to rerun the commands. and/or try autorepair (and it takes 3 times) which as I understand it is even less likely to work. But no guarantees.

---

