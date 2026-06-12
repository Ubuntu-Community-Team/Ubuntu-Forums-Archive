---
title: "Overwrote windows 7 with ubuntu 11.10, but wrong boot loader?"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by Zephilinox on 2012-03-06
So I decided to completely delete windows 7 by overwriting the partition with a LiveCD install, however after its completed I can't boot into ubuntu, instead the windows boot manager complains that somethings is broken and I should use my repair disc, how can I get rid of the windows boot loader?

---

### Post by darkod on 2012-03-06
It looks like the grub2 bootloader didn't install. To see more details, run the boot info script from the link in my signature and post the results as explained there.

---

### Post by Mark Phelps on 2012-03-07
The results of the script that darkod mentioned will confirm this ... but I suspect, that if you have a PC that came preinstalled with Win7, then the Windows bootloader files are on a separate partition -- which was NOT overwritten by your Ubuntu install.

If the script result confirms this, you will need to boot from an Ubuntu desktop CD, choose Try Ubuntu, remove the now unneeded Windows partition, and reinstall GRUB.

---

### Post by Zephilinox on 2012-03-07
I read a post about how the boot loader might be on another HDD, and it was, which is quite inconvinient but at least I can get on I suppose, thanks for the help anyway.

I do have sound issues but I'll ask for help about that in another thread.

If you know of a way to move the boot loader back to where it is meant to be (320gb hard drive) and delete the windows bootloader I would really appreciate it, here is my results.txt

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   616,753,151   616,751,104  83 Linux
/dev/sda2         616,755,198   625,141,759     8,386,562   5 Extended
/dev/sda5         616,755,200   625,141,759     8,386,560  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  64 3,907,029,119 3,907,029,056   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 607e537a-33fc-4c81-8c3b-afc580d37d2e   swap       
/dev/sda1        7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068   ext4       
/dev/sdb1        147085FF7085E836                       ntfs       Storage
/dev/sdc1        A28867EE8867C001                       ntfs       External Storage

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/External Storage  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 147085FF7085E836
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7eed5dc9-cdb7-4b21-8cc5-14d59a3bd068 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=fa9ab271-cc66-4d36-93e9-27100023a5e2 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.168563843 = 111.850143744  boot/grub/core.img                             1
 154.126529694 = 165.492101120  boot/grub/grub.cfg                             1
   1.770523071 = 1.901084672    boot/initrd.img-3.0.0-12-generic               2
   2.048988342 = 2.200084480    boot/initrd.img-3.0.0-16-generic               2
  32.133979797 = 34.503598080   boot/vmlinuz-3.0.0-12-generic                  1
   2.708469391 = 2.908196864    boot/vmlinuz-3.0.0-16-generic                  1
   2.048988342 = 2.200084480    initrd.img                                     2
   1.770523071 = 1.901084672    initrd.img.old                                 2
   2.708469391 = 2.908196864    vmlinuz                                        1
  32.133979797 = 34.503598080   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 7f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by 3177 on 2012-03-07
I would recommend throwing your live cd in. Open up Gparted, then manually re format your drive(as well as any others windows poisoned with its bootloader). Ive had to do this on my wifes acer aspire when windows crapped the bed.
Good luck.

---

### Post by darkod on 2012-03-07
Grub2 is on /dev/sda same as your ubuntu, that's the 320GB disk. If you boot from this disk all should be fine. No changes need to be done.

Actually the windows bootloader is on /dev/sdb, the 1TB disk, so you might have been booting windows all the time from the second disk, despite thinking that you are doing it from the first disk.

If you boot from the 320GB right now, does it boot OK?

---

### Post by Zephilinox on 2012-03-07
3177, I had already tried that but formatting sda had no effect, however if darkrod is right then that would make sense, since I've been booting windows from sdb even though it was on sda all this time, I'll check soon.

Yep, I was, it seems even though sda is my SATA1 HDD my boot order decided to use my other HDD instead, had to switch it around.

I've also fixed my sound problems, by editing /etc/modprobe.d/alsa-base.conf and changing snd-usb-audio to index 1, it now loads as default :D

thanks again.

---

