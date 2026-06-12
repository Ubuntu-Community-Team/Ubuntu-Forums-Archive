---
title: "Clean install of Ubuntu 10.10"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by njwatson32 on 2011-09-03
So I installed Ubuntu 11.04 (alongside the preloaded Windows 7 after getting a new ThinkPad T420) and was having some *major* issues with it, namely that it logged me out randomly every now and then and programs (especially Firefox) would crash consistently.

I figured something had gone wrong during installation so I decided I'd try reinstalling. So I popped in the installation DVD and installed a new version in the same partition as the previous one. When I boot up, I now get the grub rescue prompt. Following some instructions online, I was able to direct it to the usual boot menu and from there boot Ubuntu (or Windows 7). If it matters, I ran:
```

set prefix=(hd0,msdos6)/boot/grub
set root=(hd0,msdos6)
insmod normal
normal

```

However, I'm having trouble fixing grub so that I don't have to do this every time. Furthermore, it appears that I am still having the same problems as the first time around, so I'm thinking of just uninstalling 11.04 and using 10.10, which I haven't had any problems with before. I'm scared to try anything though while I'm having grub issues for fear that when I uninstall 11.04 I won't be able to boot into anything.

To clarify, my end goal is to get 10.10 on alongside Windows 7, preferably without having to reinstall Windows 7 (I do have an installation disk though, so I could if I *really* had to).

My hard drive is laid out like this:
SYSTEM_DRV - 1.17 GB
Windows7_OS - 82.91 GB
Ubuntu 11.04 - 31.27 GB
Swap - 3.89 GB

I'm not sure what additional details you need to know to help me, but let me know and I can tell you.

Can I please have some help!? I'm fairly inexperienced with this kind of stuff (hard drive partitions, details of booting, etc.), but I am a CS major (but more theoretical) so I'm not completely lost.

Thanks!

---

### Post by Hakunka-Matata on 2011-09-03
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
That's how to reinstall grub, several different ways.

There's really no need to worry about not being able to boot up Ubuntu if the MBR or Grub2 gets messed up. You can always boot with the install CD, the liveCD/USB if you have it handy.  Do you:?
If you do I'd suggest you reinstall grub using the link above.  Section 12.1.2.  Then go on to three and four until it starts working right.

Please download and run **boot_info_script**, link in my signature.  Post contents of the RESULTS.txt file that boot_info_script.sh produces/generates for you.

sudo grub-install --boot-directory=/mnt/boot /dev/sdX for 11.04

---

### Post by njwatson32 on 2011-09-03
> **Hakunka-Matata said:**
> []("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")Please download and run **boot_info_script**, link in my signature.  Post contents of the RESULTS.txt file that boot_info_script.sh produces/generates for you.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2           2,459,648   176,338,943   173,879,296   7 NTFS / exFAT / HPFS
/dev/sda3         176,340,990   250,068,991    73,728,002   5 Extended
/dev/sda5         241,915,904   250,068,991     8,153,088  82 Linux swap / Solaris
/dev/sda6         176,340,992   241,915,903    65,574,912  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        AE6EEFE96EEFA7F3                       ntfs       SYSTEM_DRV
/dev/sda2        AEAEF311AEF2D137                       ntfs       Windows7_OS
/dev/sda5        1c7ae79b-8782-4137-a1e8-932d5b76add6   swap       
/dev/sda6        0efe9530-d75f-4c3d-816b-f16515788a13   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
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

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root AE6EEFE96EEFA7F3
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AEAEF311AEF2D137
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.233730316 = 107.625148416  boot/grub/core.img                             1
 100.256061554 = 107.649126400  boot/grub/grub.cfg                             1
  85.094242096 = 91.369246720   boot/initrd.img-2.6.38-11-generic              2
  84.493694305 = 90.724413440   boot/initrd.img-2.6.38-8-generic               2
  84.808902740 = 91.062865920   boot/vmlinuz-2.6.38-11-generic                 1
 100.249961853 = 107.642576896  boot/vmlinuz-2.6.38-8-generic                  1
  85.094242096 = 91.369246720   initrd.img                                     2
  84.493694305 = 90.724413440   initrd.img.old                                 2
  84.808902740 = 91.062865920   vmlinuz                                        1
 100.249961853 = 107.642576896  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Hakunka-Matata on 2011-09-03
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. [B][COLOR=Red]core.img is at this location and looks 
    for (,msdos5)/boot/grub [/COLOR][/B]on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

[COLOR=Red]sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  [/COLOR]

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2           2,459,648   176,338,943   173,879,296   7 NTFS / exFAT / HPFS
/dev/sda3         176,340,990   250,068,991    73,728,002   5 Extended
/dev/sda5         241,915,904   250,068,991     8,153,088  82 Linux swap / Solaris
/dev/sda6         176,340,992   241,915,903    65,574,912  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        AE6EEFE96EEFA7F3                       ntfs       SYSTEM_DRV
/dev/sda2        AEAEF311AEF2D137                       ntfs       Windows7_OS
/dev/sda5        1c7ae79b-8782-4137-a1e8-932d5b76add6   swap       
/dev/sda6        0efe9530-d75f-4c3d-816b-f16515788a13   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
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

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0efe9530-d75f-4c3d-816b-f16515788a13 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 0efe9530-d75f-4c3d-816b-f16515788a13
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root AE6EEFE96EEFA7F3
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AEAEF311AEF2D137
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.233730316 = 107.625148416  boot/grub/core.img                             1
 100.256061554 = 107.649126400  boot/grub/grub.cfg                             1
  85.094242096 = 91.369246720   boot/initrd.img-2.6.38-11-generic              2
  84.493694305 = 90.724413440   boot/initrd.img-2.6.38-8-generic               2
  84.808902740 = 91.062865920   boot/vmlinuz-2.6.38-11-generic                 1
 100.249961853 = 107.642576896  boot/vmlinuz-2.6.38-8-generic                  1
  85.094242096 = 91.369246720   initrd.img                                     2
  84.493694305 = 90.724413440   initrd.img.old                                 2
  84.808902740 = 91.062865920   vmlinuz                                        1
 100.249961853 = 107.642576896  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

Do you see what's wrong?  It's being told to look in (msdos5)=sda5 for boot files, and sda5 is the swap partition!, can't happen.  That has to be fixed, it should be msdos6 = sda6 which is where the boot files and system are located.  But the reinstall will fix (it better) that.  Wanted you to see it first.

---

### Post by Hakunka-Matata on 2011-09-03
Redacted first message, formatting is fixed.

---

### Post by njwatson32 on 2011-09-03
OK thanks, grub is fixed now. So if I want to downgrade to 10.10, can I just put in the 10.10 DVD and have it overwrite to the same partition as 11.04 without messing anything up?

PS: I know other people have had the same problems as I have with 11.04 logging out randomly, but there didn't seem to be a solution. Do you know anything about this?

---

### Post by Hakunka-Matata on 2011-09-03
Yes, you can.  You can also use gparted and delete the current OS partition.

---

