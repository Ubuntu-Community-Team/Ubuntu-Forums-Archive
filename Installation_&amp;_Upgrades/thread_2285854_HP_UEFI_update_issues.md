---
title: "HP UEFI update issues"
date: 2015-07-08
forum: Installation &amp; Upgrades
---

### Post by daytonajohn2 on 2015-07-08
Today I installed some updates, and didn't look them over closely before installing. As I watched, I saw  grub updates being installed: "grub-efi-amd64", "grub-efi-amd64-bin", "grub-common", and "grub2-common". As I saw these being installed I thought to myself "Oh sh*t!!". 
I was right to think that. Next boot failed and showed a "MOK Management" page. The EFI boot was failing, because it couldn't validate the grub loader. I disabled "secure boot" and now I can boot into Ubuntu again. Anyone else see this?? More importantly: Anyone know how to fix this??
for the record:
Hardware: HP envy laptop
dual boot:
Windows 8.1
Ubuntu 15.04

---

### Post by ubfan1 on 2015-07-08
Check the bootloaders UEFI is trying to run with   sudo efibootmgr -v    and ensure your Ubuntu boot is trying to run shimx64.efi for secure boot, not grubx64.efi.   I have seen updates/installs-to-usb  alter that, leaving secure boot unbootable (but not in awhile).  You can change back to shim with efibootmgr too.

---

### Post by oldfred on 2015-07-08
Moved to your own thread since not really related to original post.

Since HP and HP often has issues with booting anything but the Windows entry, which work around did you use to get it to work? You may have to redo work around. Although older work arounds, even those done by Boot-Repair to use Windows efi file are not now recommended.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by daytonajohn2 on 2015-07-08
Here is the output from that command:
       [FONT=monospace]
```

BootCurrent: 0000 
Timeout: 0 seconds 
BootOrder: 0000,3000,0003,2001,2002,2004 
Boot0000* ubuntu        HD(2,145800,82000,b93bbe06-6e22-451d-b3af-27218721ad02)File(\EFI\ubuntu\shimx64.efi)RC 
Boot0001* ubuntu        HD(2,145800,82000,b93bbe06-6e22-451d-b3af-27218721ad02)File(\EFI\ubuntu\shimx64.efi)RC 
Boot0003* Windows Boot Manager  HD(2,145800,82000,b93bbe06-6e22-451d-b3af-27218721ad02)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.
{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.................... 
Boot2001* EFI USB Device        RC 
Boot2002* EFI DVD/CDROM RC 
Boot3000* Internal Hard Disk or Solid State Disk        RC

```
Looks like I am using shimx64.efi.

Using sbverify to check for signatures:

[/FONT]
       [FONT=monospace][COLOR=#000000] sbverify --no-verify shimx64.efi  [/COLOR]
warning: data remaining[1158632 vs 1276984]: gaps between PE/COFF sections? 
Signature verification OK

[/FONT]
   
           [FONT=monospace][COLOR=#000000] sbverify --no-verify grubx64.efi  [/COLOR]
No signature table present 
Unable to read signature data from grubx64.efi 
Signature verification failed

grubx64.efi was changed by the recent update. Could the lack of a signature cause my problem?
[/FONT]

---

### Post by daytonajohn2 on 2015-07-08
Here is the output from bootinfoscript:

                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/HP/bootmgr.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,333,247     1,331,200 Windows Recovery Environment (Windows)
/dev/sda2       1,333,248     1,865,727       532,480 EFI System partition
/dev/sda3       1,865,728     2,127,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,127,872   565,645,311   563,517,440 Data partition (Windows/Linux)
/dev/sda5   1,896,845,312 1,953,513,471    56,668,160 Data partition (Windows/Linux)
/dev/sda6     565,645,312   858,613,759   292,968,448 Data partition (Linux)
/dev/sda7     858,613,760   921,114,623    62,500,864 Swap partition (Linux)
/dev/sda8     921,114,624 1,896,845,311   975,730,688 Data partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        02A6DFBFA6DFB181                       ntfs       WINRE
/dev/sda2        42CA-463E                              vfat       
/dev/sda3                                                          
/dev/sda4        92B035BEB035A99D                       ntfs       Windows
/dev/sda5        421ECE6A1ECE5717                       ntfs       RECOVERY
/dev/sda6        2e566a75-3772-4e8e-9b95-22035eee5646   ext4       
/dev/sda7        bad30743-92a4-4bab-b6f1-158e656b289d   swap       
/dev/sda8        8d0583a9-7f54-4407-a857-b4ae27e56f8c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda4        /mnt/windows             fuseblk    (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda8        /home                    ext4       (rw,relatime,data=ordered)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
else
  search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
#set_background_image "images/tile.png";

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2e566a75-3772-4e8e-9b95-22035eee5646' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
    else
      search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
    fi
    linux    /boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
    initrd    /boot/initrd.img-3.19.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
    menuentry 'Ubuntu, with Linux 3.19.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-22-generic ...'
        linux    /boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-init-upstart-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-22-generic ...'
        linux    /boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro   init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-22-generic-recovery-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-22-generic ...'
        linux    /boot/vmlinuz-3.19.0-22-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-21-generic ...'
        linux    /boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-init-upstart-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-21-generic ...'
        linux    /boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro   init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-21-generic-recovery-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-21-generic ...'
        linux    /boot/vmlinuz-3.19.0-21-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-20-generic ...'
        linux    /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-20-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-init-upstart-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-20-generic ...'
        linux    /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro   init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-20-generic-recovery-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-20-generic ...'
        linux    /boot/vmlinuz-3.19.0-20-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-18-generic ...'
        linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-18-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-init-upstart-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-18-generic ...'
        linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro   init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-18-generic-recovery-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-18-generic ...'
        linux    /boot/vmlinuz-3.19.0-18-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /boot/vmlinuz-3.19.0-15-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-init-upstart-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /boot/vmlinuz-3.19.0-15-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro   init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.19.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-15-generic-recovery-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.19.0-15-generic ...'
        linux    /boot/vmlinuz-3.19.0-15-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-15-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-advanced-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.16.0-34-generic ...'
        linux    /boot/vmlinuz-3.16.0-34-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-34-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-init-upstart-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.16.0-34-generic ...'
        linux    /boot/vmlinuz-3.16.0-34-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro   init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-34-generic-recovery-2e566a75-3772-4e8e-9b95-22035eee5646' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  2e566a75-3772-4e8e-9b95-22035eee5646
        else
          search --no-floppy --fs-uuid --set=root 2e566a75-3772-4e8e-9b95-22035eee5646
        fi
        echo    'Loading Linux 3.16.0-34-generic ...'
        linux    /boot/vmlinuz-3.16.0-34-generic.efi.signed root=UUID=2e566a75-3772-4e8e-9b95-22035eee5646 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-34-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-42CA-463E' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  42CA-463E
    else
      search --no-floppy --fs-uuid --set=root 42CA-463E
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=2e566a75-3772-4e8e-9b95-22035eee5646 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=42CA-463E  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda8 during installation
UUID=8d0583a9-7f54-4407-a857-b4ae27e56f8c /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=bad30743-92a4-4bab-b6f1-158e656b289d none            swap    sw              0       0
//192.168.1.3/public              /mnt/mybook      cifs      _netdev,guest,nofail,rw,noperm      0      0
/dev/sda4                  /mnt/windows      ntfs      defaults,bg      0      0
UUID=42CA-463E    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 14 00  |........?....X..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 3e 46 ca 42 4e  4f 20 4e 41 4d 45 20 20  |..)>F.BNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-vswlmd0d/Tmp_Log: No such file or directory
```

---

### Post by ubfan1 on 2015-07-08
grubx64.efi should not fail the signature verify.  Take a look at the one in /usr/lib/grub/x86_64-efi-signed/grubx64.efi.signed  and if it's OK, just copy it (without the .signed ) to /boot/efi/EFI/ubuntu/grubx64.efi  (the one that failed the sig test I presume).

---

### Post by oldfred on 2015-07-08
Please use code tags for longer terminal output.
And often easier to just post link to Summary Report that Boot-Repair gives.

Were you booting from boot3000 which now is second in boot order?
And grub update added duplicate ubuntu entry that now is first in boot order.

Was the hard drive entry boot3000 or /EFI/Boot/bootx64.efi a copy of grubx64.efi or shimx64.efi? If so you may need to copy new version of shim or grub into /EFI/Boot and rename to bootx64.efi.

---

### Post by daytonajohn2 on 2015-07-10
There is no /usr/lib/grub/x86_64-efi-signed/ directory on my machine. There is a[FONT=monospace][COLOR=#000000] /usr/lib/grub/x86_64-efi/ directory, but it contains mostly *.mod files and no grub*.[/COLOR]
[/FONT]

---

### Post by oldfred on 2015-07-10
If you do not have signed, then you are booting with secure boot off.
You need shim (grub - signed version) and signed kernels to boot with Secure boot on.

If secure boot was turned on in UEFI, that could also be an issue.

---

### Post by daytonajohn2 on 2015-07-11
I was booting successfully using secure boot before the update I mentioned. I did some more research and found that this is a bug and has been reported: [https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1469995](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1469995) 
I just noticed that the update in question also did a removal of[FONT=monospace][COLOR=#000000] the package: grub-efi-amd64-signed. [/COLOR]
[/FONT]

---

### Post by daytonajohn2 on 2015-07-11
So, convinced that the problem was an unsigned grubx64.efi, I copied an old version of it from a backup to /boot/efi/EFI/ubuntu (overwriting the new version). Sbverify indicates that the old version was signed. Switched back to secure boot, and all is working again.
So with that fix, and the knowledge that this is a known bug, I want to mark this thread as "solved", but I can't find any way to do that.

---

### Post by daytonajohn2 on 2015-07-11
OK, found it. Marked as solved.

---

