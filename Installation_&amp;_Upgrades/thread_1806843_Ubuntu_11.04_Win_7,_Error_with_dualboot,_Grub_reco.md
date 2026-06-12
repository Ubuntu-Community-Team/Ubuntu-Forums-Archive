---
title: "Ubuntu 11.04 Win 7, Error with dualboot, Grub recovery"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by Honzacz on 2011-07-18
Hi,
I am newbee with Ubuntu and this is my first instalation of dualboot. I got Windows 7 and I would like to add Ubuntu on my old tablet PC (TC 4200).

I tried Windows installer, Windows worked, ubuntu not (grub error on booting). After that I tried instalation from USB, always it ends on same screen (Grub recovery, error: unkown disc)- I will add exact error message. After I tried to install Ubuntu from USB stick and add grub to sda, it crashed my Windows.. Repaired, reinstalled Ubuntu, same error again.

I got 5 disc sectors, Win 7, two data sectors, one ubuntu, one ubuntu swap.
Here is result text from boot info script
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........'.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1462120 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,723,839    30,723,777   7 NTFS / exFAT / HPFS
/dev/sda2          30,723,901   271,551,487   240,827,587   f W95 Extended (LBA)
/dev/sda5          30,723,903   133,116,479   102,392,577   7 NTFS / exFAT / HPFS
/dev/sda6         133,116,543   271,551,487   138,434,945   7 NTFS / exFAT / HPFS
/dev/sda3         271,552,512   308,674,559    37,122,048  83 Linux
/dev/sda4         308,674,560   312,580,095     3,905,536  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1008 MB, 1008730112 bytes
9 heads, 40 sectors/track, 5472 cylinders, total 1970176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,360     1,970,175     1,967,816   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        72A4F164A4F12B6D                       ntfs       
/dev/sda3        be912025-7ea3-4d31-857b-a533225c43cc   ext4       
/dev/sda4        ebb74fe8-77ec-432b-91bd-04c991ae8ece   swap       
/dev/sda5        448CF9B78CF9A418                       ntfs       
/dev/sda6        CA242C8A242C7B97                       ntfs       
/dev/sdb1        7027-5571                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/be912025-7ea3-4d31-857b-a533225c43cc ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/448CF9B78CF9A418  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/CA242C8A242C7B97  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root be912025-7ea3-4d31-857b-a533225c43cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root be912025-7ea3-4d31-857b-a533225c43cc
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
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root be912025-7ea3-4d31-857b-a533225c43cc
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=be912025-7ea3-4d31-857b-a533225c43cc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root be912025-7ea3-4d31-857b-a533225c43cc
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=be912025-7ea3-4d31-857b-a533225c43cc ro single 
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
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root be912025-7ea3-4d31-857b-a533225c43cc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root be912025-7ea3-4d31-857b-a533225c43cc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 72A4F164A4F12B6D
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=be912025-7ea3-4d31-857b-a533225c43cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=ebb74fe8-77ec-432b-91bd-04c991ae8ece none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.646144867 = 145.648939008  boot/grub/core.img                             1
 135.677753448 = 145.682878464  boot/grub/grub.cfg                             1
 131.064453125 = 140.729384960  boot/initrd.img-2.6.38-8-generic               2
 135.657554626 = 145.661190144  boot/vmlinuz-2.6.38-8-generic                  1
 131.064453125 = 140.729384960  initrd.img                                     2
 135.657554626 = 145.661190144  vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Hope somebody will know..

---

### Post by Honzacz on 2011-07-18
Error screen is:
Error: unkown filesystem
Grub rescue>

---

### Post by lmarmisa on 2011-07-18
I recommend to reinstall grub ( [https://help.ubuntu.com/community/Grub2#ChRoot )]("https://help.ubuntu.com/community/Grub2#ChRoot")

Boot into an Ubuntu Live CD / USB, open a terminal and type:

```

sudo mount /dev/sda3 /mnt 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
sudo chroot /mnt 
update-grub 
grub-install /dev/sda 
grub-install --recheck /dev/sda 
exit 
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done 
sudo umount /mnt/usr 
sudo umount /mnt

```Reboot the system normally and check if the problem is solved.

---

### Post by Honzacz on 2011-07-18
I exactly writed commands from above, didnt helped. Same error.
Here is copy of terminal:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda3/mnt
mount: can't find /dev/sda3/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i ; done
ubuntu@ubuntu:~$ sudo umount /mnt/usr
umount: /mnt/usr: not mounted
ubuntu@ubuntu:~$ sudo umount /mnt

```

---

### Post by lmarmisa on 2011-07-18
The first commnd was not correctly typed:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda3/mnt
mount: can't find /dev/sda3/mnt in /etc/fstab or /etc/mtab

```

You forgot to type a blank space.

Try to use copy & paste in order to avoid errors.

Reboot again and repeat the procedure. Follow my instructions. The link [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot) is only a reference.

---

### Post by Honzacz on 2011-07-18
Thanks,
in meantime i tried it once again with exactly copy-pasting what your wrote into terminal, same error again.

---

