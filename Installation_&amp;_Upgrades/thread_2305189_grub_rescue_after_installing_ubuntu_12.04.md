---
title: "grub rescue after installing ubuntu 12.04"
date: 2015-12-03
forum: Installation &amp; Upgrades
---

### Post by felix37 on 2015-12-03
I just installed ubuntu 12.04 lts to my PC besides windows 10

My pc has 2 ssds and one hdd. Windows is on one ssd the other one contains data. I had some space left on my hdd so i created a new partition for Linux using the ubuntu advanced partition manager during the installation.
So i freed up 50GB of space. On this free space i created a swap parition with 2GB and formated the rest with ext4 and set the mount point to "/". For the boot loader i choose (which was marked by default) the disk windows is installed to.
In general i followed this guide (but without the extra /home partition):  [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation).

As I tried to install linux and the installer crashed, telling me something was wrong with either the hdd or the install medium (was using an usb stick).
So i checked the USB, put ubuntu back on it and tried again. The partition setup was the same as before. This time it worked and ubuntu was installed the system rebooted and i got to ubuntu (wihtout a grub prompt).
After installing the nvidia-340 driver i tried to reboot the system.

Then i got this message:
error: no such device: "a large hex number"
grub rescue>

I rebooted again and started UEFI/BIOS and checked if anything was wrong with my HDDs. Nothing was so i closed it and surprisingly GRUB did load without any problems. Linux came up just fine as well. To verify I rebooted the system and the same grub error came up. It stayed after another reboot. If i start UEFI and close it again GRUB and linux start just fine.

I included a log file created with "sudo hwinfo". Here is the output of the Boot Info Script:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid bf71fd13-3610-40bc-a198-83bb3216a27c root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

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

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   487,473,151   486,754,304   7 NTFS / exFAT / HPFS
/dev/sda3         487,473,152   488,394,751       921,600  27 Hidden NTFS (Recovery Environment)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         264,192 1,861,080,111 1,860,815,920 Data partition (Windows/Linux)
/dev/sdb3   1,861,081,088 1,865,080,831     3,999,744 Swap partition (Linux)
/dev/sdb4   1,865,080,832 1,953,523,711    88,442,880 Data partition (Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sdc2             718,848   500,115,455   499,396,608   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        226EC7966EC760E1                       ntfs       System-reserviert
/dev/sda2        F868884E68880D96                       ntfs       
/dev/sda3        74341E8F341E5508                       ntfs       
/dev/sdb2        001257C61257BF7A                       ntfs       Volume
/dev/sdb3        e0cb22fd-29a7-4635-a70f-a4584f6e913d   swap       
/dev/sdb4        bf71fd13-3610-40bc-a198-83bb3216a27c   ext4       
/dev/sdc1        9ECC5939CC590CC1                       ntfs       System-reserviert
/dev/sdc2        567EF5F37EF5CBAD                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb4        /                        ext4       (rw,errors=remount-ro)


=========================== sdb4/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd1,gpt4)'
search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd1,gpt4)'
  search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.13.0-71-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt4)'
    search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
    linux    /boot/vmlinuz-3.13.0-71-generic root=UUID=bf71fd13-3610-40bc-a198-83bb3216a27c ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-71-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-71-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt4)'
    search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
    echo    'Loading Linux 3.13.0-71-generic ...'
    linux    /boot/vmlinuz-3.13.0-71-generic root=UUID=bf71fd13-3610-40bc-a198-83bb3216a27c ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-71-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt4)'
    search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=bf71fd13-3610-40bc-a198-83bb3216a27c ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt4)'
    search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
    echo    'Loading Linux 3.13.0-32-generic ...'
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=bf71fd13-3610-40bc-a198-83bb3216a27c ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-32-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt4)'
    search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt4)'
    search --no-floppy --fs-uuid --set=root bf71fd13-3610-40bc-a198-83bb3216a27c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 8 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 226EC7966EC760E1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 8 (loader) (on /dev/sdc1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 9ECC5939CC590CC1
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=bf71fd13-3610-40bc-a198-83bb3216a27c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=e0cb22fd-29a7-4635-a70f-a4584f6e913d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.13.0-32-generic              1
               =                boot/initrd.img-3.13.0-71-generic              1
               =                boot/vmlinuz-3.13.0-32-generic                 2
               =                boot/vmlinuz-3.13.0-71-generic                 1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```



How do i resolve this Problem? (Linux is a fresh install so i can reinstall it// if my UEFI and Linux just dont work out i can do without linux an will run it in a VM as i used to do)

---

### Post by yancek on 2015-12-03
I don't see any EFI partition and that will usually show in the bootinfoscript output.  You also show Grub installed to the MBR of the first drive and Ubuntu shows on the sdb4 partition.  My understanding is that if you use windows with GPT you need to use EFI with Ubuntu or one or both will not boot.

---

### Post by felix37 on 2015-12-03
I attached some pictures of the grub in rescue and in normal mode.

If grup is in rescue mode and i type "ls" it shows me that there is only one drive hd0.  hd0 can't be accessed as it if of an unknown filesystem 

If i open the console in the regular grub (using the uefi trick i described above to do so) ls shows all the partitions. (hd1,gpt4) <-> [sdb4] is the one containing ubuntu. Naturally it is also the device [COLOR=#000000][FONT=Ubuntu Mono]bf71fd13-3610-40bc-a198-83bb3216a27c

[/FONT][/COLOR]So if i simply boot the machine grub can't access any partition besides sdaX on which it is installed to. If i start the uefi gui and close it again grub _can_ access all the other partitions just fine.
So the problem seems to boil down to some uefi grub incompatibility.

> [COLOR=#000000]I don't see any EFI partition and that will usually show in the bootinfoscript output. You also show Grub installed to the MBR of the first drive and Ubuntu shows on the sdb4 partition. My understanding is that if you use windows with GPT you need to use EFI with Ubuntu or one or both will not boot.[/COLOR]

So how would i do this exactly?

EDIT:
One additional thing i found out is that, if i load the uefi setup and then just shut the pc down while I'm in it, the PC boots just fine the next time i turn it on. Secure boot is turned off.

And another question: If i would install grub to say sdb and keep sda as the first boot option, windows would boot as if linux isn't installed right? So to boot to linux i could just bring up the bootoption menu an choose sdb if i need to run linux. This is an option because this being my gaming pc i will boot to windows 90% of the time anyways.

---

### Post by yancek on 2015-12-03
I don't use UEFI/GPT so can't really tell you how to do it.  You don't have an EFI partition shown in the bootinfo output which you would need to have to boot windows and Ubuntu in EFI.  You can't use Legacy/CSM in the BIOS because you are using GPT partitioning and windows requires UEFI if you are using GPT.  The best way is to select to use UEFI during the install of both systems.  You could do a search here for posts by oldfred as he usually has a number of links in his posts which would be helpful.  Might get lucky and he'll see your post.

---

### Post by felix37 on 2015-12-04
The problem is fixed. All that was wrong, was that "Fast Boot" was enabled in uefi. My bad that i didn't check that earlier. Actually found that this might cause the problem in a post of oldFred. Thanks at yancek for your help!
So this thread can be closed.

---

