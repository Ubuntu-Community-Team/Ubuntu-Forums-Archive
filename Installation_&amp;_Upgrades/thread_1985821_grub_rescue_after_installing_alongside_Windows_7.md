---
title: "grub rescue after installing alongside Windows 7"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by Yooper on 2012-05-23
I could use some assistance.  I was running a dual boot with 11.04 and Windows 7.  During the update process to 12.04 I lost power.  I was still able to boot Windows.   I made a live CD and installed 12.04.  When I went to boot up for the first time I received an error was in GRUB RESCUE mode.

I am very new at this, perhaps in over my head.  So any help you can provide is appreciated.  I have tried to follow some of these how to's but seem to be missing something.  Currently all I can do is boot the 12.04 Live CD.  I tried the boot repair CD, but that seemed to stall after an hour on "searching system".


In advance...  thank you.

---

### Post by oldfred on 2012-05-23
I moved you to a new thread as it can get confusing with multiple users with similar issues but different configurations.

If you cannot get Boot-Repair to run in your Ubuntu liveCD, try this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Yooper on 2012-05-23
```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 9a8ace3c-e0f1-4d95-b370-78e795db95ec root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 5d19df5b-486b-43d3-96e0-5eecb7f9804c root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 251.1 GB, 251058462208 bytes
255 heads, 63 sectors/track, 30522 cylinders, total 490348559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   490,346,495   490,344,448   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63 1,474,824,653 1,474,824,591   7 NTFS / exFAT / HPFS
/dev/sdd2       1,474,826,238 1,953,521,663   478,695,426   5 Extended
/dev/sdd5       1,936,750,592 1,953,521,663    16,771,072  82 Linux swap / Solaris
/dev/sdd6       1,474,826,240 1,936,750,591   461,924,352  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1AB265E1B265C23D                       ntfs       
/dev/sdb1        B244D59C44D5639F                       ntfs       Storage 1 Movies
/dev/sdc1        E20467CA04679FF1                       ntfs       Storage 3
/dev/sdd1        4E40F7F340F7DF9F                       ntfs       Storage 2 Family Pics and Movies
/dev/sdd5        ad0a5780-546d-48a9-8666-f6cc4320989e   swap       
/dev/sdd6        84a35258-a64a-4dc2-b6ea-b8776eace592   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1AB265E1B265C23D  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdd6/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos6)'
search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos6)'
  search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=84a35258-a64a-4dc2-b6ea-b8776eace592 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=84a35258-a64a-4dc2-b6ea-b8776eace592 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=84a35258-a64a-4dc2-b6ea-b8776eace592 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=84a35258-a64a-4dc2-b6ea-b8776eace592 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos6)'
    search --no-floppy --fs-uuid --set=root 84a35258-a64a-4dc2-b6ea-b8776eace592
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 1AB265E1B265C23D
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

=============================== sdd6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=84a35258-a64a-4dc2-b6ea-b8776eace592 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=ad0a5780-546d-48a9-8666-f6cc4320989e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 785.399337769 = 843.316117504  boot/grub/core.img                             1
 785.401355743 = 843.318284288  boot/grub/grub.cfg                             1
 704.176548004 = 756.103811072  boot/initrd.img-3.2.0-23-generic-pae           2
 704.283203125 = 756.218331136  boot/initrd.img-3.2.0-24-generic-pae           2
 847.385005951 = 909.872721920  boot/vmlinuz-3.2.0-23-generic-pae              1
 704.033969879 = 755.950718976  boot/vmlinuz-3.2.0-24-generic-pae              1
 704.176548004 = 756.103811072  initrd.img                                     2
 847.385005951 = 909.872721920  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

---

### Post by drs305 on 2012-05-23
It looks like things are intact in the sdd MBR and on the sdd6 partition. Have you tried changing the BIOS boot order to boot your sdd drive first?

There could be a problem with GRUB/BIOS seeing the boot files, but try the above first.

---

### Post by YannBuntu on 2012-05-23
Hello
I see no problem in the BootInfo. Please make sure your BIOS is setup to boot on sdd.
Failed upgrades generally result in broken system files. Sometimes it can be solved just by [reinstalling GRUB]("https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD"), if not i would just reinstall [this way]("https://help.ubuntu.com/community/UbuntuReinstallation").

(The stall on "scanning system" was probably an update problem. You may want to retry Boot-Repair-Disk skipping the update (answer "No" to the "Do you want to update from PPA?" question).

---

### Post by Yooper on 2012-05-25
THANK YOU.

Sorry for the delay in posting.  I made the change in the bios and I am up and running.


THANKS AGAIN.

---

