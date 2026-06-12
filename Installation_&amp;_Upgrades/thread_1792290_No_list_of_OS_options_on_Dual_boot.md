---
title: "No list of OS options on Dual boot"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by wolfv6 on 2011-06-28
I just installed a dual boot win7-Ubuntu 11.04. When I reboot, there is no list of OS options displayed, it just boots to windows.  Below are the details of how I got to this point.
 
I Used GParted to delete all partitions off a hardard drive. Then installed win7 from CD. Win7 works fine. Then I formated an ext4 partion and installed Ubuntu 11.04 from the iso CD. But on reboot I don't see a list of OS options. When I boot from the Ubuntu 11.04 CD, I can view the usual Unix directories in the hard drive Ubuntu root (bin, etc, lib, usr, var) and the /boot/grub directory. So Ubuntu looks like it got installed. What else can I trouble shoot to get the list of OS options displayed?
 
I appriciate you helping me out.

---

### Post by Quackers on 2011-06-28
Where did you install grub to? Did you change it from the default setting?

---

### Post by mastablasta on 2011-06-28
use the bootinfosript found here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
and post the results here using code tags (the # icon) so it's easier to read. 
 
this script will tell us what is happening during your boot. and might just tell us what is going wrong.

---

### Post by wolfv6 on 2011-06-28
Thanks for the quick response.

I don't know where I installed grub to, it must of been to default.

Below are the boot_info_script.sh RESULTS.txt.

I will be back in 10 hours.  Thanks for looking into this.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

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
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda4 
                       and looks at sector 130805312 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos4)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    67,336,191    67,129,344   7 NTFS / exFAT / HPFS
/dev/sda3          67,336,192   117,667,839    50,331,648   7 NTFS / exFAT / HPFS
/dev/sda4         117,667,840   160,833,535    43,165,696  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F8B8659EB8655BDE                       ntfs       System Reserved
/dev/sda2        281226BC12268F3E                       ntfs       
/dev/sda3        A2AA2FE6AA2FB5A7                       ntfs       
/dev/sda4        5fc060f7-abe6-4b03-94af-3ac05808c6fc   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/281226BC12268F3E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/A2AA2FE6AA2FB5A7  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/5fc060f7-abe6-4b03-94af-3ac05808c6fc ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 5fc060f7-abe6-4b03-94af-3ac05808c6fc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 5fc060f7-abe6-4b03-94af-3ac05808c6fc
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5fc060f7-abe6-4b03-94af-3ac05808c6fc
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5fc060f7-abe6-4b03-94af-3ac05808c6fc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5fc060f7-abe6-4b03-94af-3ac05808c6fc
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5fc060f7-abe6-4b03-94af-3ac05808c6fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5fc060f7-abe6-4b03-94af-3ac05808c6fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 5fc060f7-abe6-4b03-94af-3ac05808c6fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F8B8659EB8655BDE
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

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=5fc060f7-abe6-4b03-94af-3ac05808c6fc /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  62.372859955 = 66.972348416   boot/grub/core.img                             1
  58.507911682 = 62.822391808   boot/grub/grub.cfg                             1
  58.152454376 = 62.440722432   boot/initrd.img-2.6.38-8-generic               2
  62.371589661 = 66.970984448   boot/vmlinuz-2.6.38-8-generic                  1
  58.152454376 = 62.440722432   initrd.img                                     2
  62.371589661 = 66.970984448   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Quackers on 2011-06-28
Grub has been installed to sda4. It needs to be in sda, otherwise it won't boot.
The following instructions should install grub to the mbr of sda, but beware that it will over-write your Windows bootloader. This shouldn't be a problem as grub can boot Windows, but unless you have a Windows repair disc or a Windows installation disc (NOT recovery discs) you will have difficulty re-creating it should you need to do so.
I would advise that you make a repair disc at least before you start (from Windows Control Panel > Backup & Restore Centre > left panel click on "make a recovery cd". Note that this is not a set of recovery dvd's - just a repair cd).

When done, boot from the Ubuntu live cd and select "try Ubuntu".
When the desktop loads open a terminal and copy/paste these lines, one at a time pressing enter after each one.
```
sudo mount /dev/sda4 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
``` This should report no errors. If it doesn't reboot and Ubuntu should boot directly.
Open a terminal and run ```
sudo update-grub
``` and you should see the Windows Loader picked up as grub.cfg is run.
If so, reboot and you should see a grub menu with the choice of which OS to boot.

---

### Post by wolfv6 on 2011-06-28
Thanks Quackers.  That worked.  My list of OS options is displayed at bootup.

---

### Post by Quackers on 2011-06-28
Excellent :-)
Have fun!

---

