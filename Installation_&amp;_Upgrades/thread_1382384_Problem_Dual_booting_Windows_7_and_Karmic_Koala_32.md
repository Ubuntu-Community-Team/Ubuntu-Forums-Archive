---
title: "Problem Dual booting Windows 7 and Karmic Koala 32bit"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by forent on 2010-01-15
My problem is i cant get into windows 7. Grub menu have showed himself now(thanks to Herman and drs305). 
ive read this thread "[http://ubuntuforums.org/showthread.php?t=1379434&page=3](http://ubuntuforums.org/showthread.php?t=1379434&page=3)"
using ```
sudo ./00_start_here.sh 
```

i have search everywhere, but my windows wont back to grub menu. i can only get into ubuntu karmic. FYI im using GRUB2(1.97beta 4) and this is my boot info
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /menu.lst /bootmgr /Windows/System32/winload.exe 
                       /grldr /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /grldr /GRLDR

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a9e0a9d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,521,934    83,521,872   7 HPFS/NTFS
/dev/sda2          83,521,935   312,560,639   229,038,705   f W95 Ext d (LBA)
/dev/sda5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sda6         204,796,683   312,560,639   107,763,957   7 HPFS/NTFS
/dev/sda7          83,522,061   101,498,669    17,976,609  83 Linux
/dev/sda8         101,498,733   102,398,309       899,577  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500 MB, 500563968 bytes
255 heads, 63 sectors/track, 60 cylinders, total 977664 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cebb

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       977,663       977,601   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="60F06026F060049E" TYPE="ntfs" 
sda5: UUID="6A603F3E603F1075" LABEL="Master" TYPE="ntfs" 
sda6: UUID="58D8C402D8C3DC7E" LABEL="Document" TYPE="ntfs" 
sda7: LABEL="Linux" UUID="dd97f370-31e6-46a3-b2f6-30f0256466b0" TYPE="ext4" 
sda8: UUID="864220e6-6aa4-4fbd-a2a3-7240d290449e" TYPE="swap" 
sdc1: LABEL="RIFKIWIJAYA" UUID="88FC-B128" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rifkiwijaya/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rifkiwijaya)
/dev/sdc1 on /media/RIFKIWIJAYA type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1 on /media/Mobile Partner   type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda5 on /media/Master type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/menu.lst: ================================

timeout 60 
default 0 
 
title Boot from Hard Drive 
rootnoverify (hd0,0) 
chainloader (hd0,0)+1 
 
title -------------------- 
root 
 
title Start Hiren's BootCD 
find --set-root /HBCD/boot.gz 
map --mem /HBCD/boot.gz (fd0) 
map --hook 
chainloader (fd0)+1 
rootnoverify (fd0) 
map --floppies=1 
boot 
 
title Mini Windows Xp 
find --set-root /HBCD/XPLOADER.BIN 
chainloader /HBCD/XPLOADER.BIN 

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: menu.lst

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set dd97f370-31e6-46a3-b2f6-30f0256466b0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set dd97f370-31e6-46a3-b2f6-30f0256466b0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd97f370-31e6-46a3-b2f6-30f0256466b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set dd97f370-31e6-46a3-b2f6-30f0256466b0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=dd97f370-31e6-46a3-b2f6-30f0256466b0 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=dd97f370-31e6-46a3-b2f6-30f0256466b0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=864220e6-6aa4-4fbd-a2a3-7240d290449e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  42.7GB: boot/grub/core.img
  42.7GB: boot/grub/grub.cfg
  42.7GB: boot/initrd.img-2.6.31-14-generic
  42.7GB: boot/vmlinuz-2.6.31-14-generic
  42.7GB: initrd.img
  42.7GB: vmlinuz

================================ sdc1/menu.lst: ================================

timeout 60 
default 0 
 
title Boot from Hard Drive 
rootnoverify (hd0,0) 
chainloader (hd0,0)+1 
 
title -------------------- 
root 
 
title Start Hiren's BootCD 
find --set-root /HBCD/boot.gz 
map --mem /HBCD/boot.gz (fd0) 
map --hook 
chainloader (fd0)+1 
rootnoverify (fd0) 
map --floppies=1 
boot 
 
title Mini Windows Xp 
find --set-root /HBCD/XPLOADER.BIN 
chainloader /HBCD/XPLOADER.BIN 

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```


thanks a bunch before..

---

### Post by meierfra. on 2010-01-19
> sda1:
Boot files/dirs:   /menu.lst /bootmgr /Windows/System32/winload.exe 
                       /grldr [COLOR="Red"]/boot/grub/core.img[/COLOR]

You seem to have a "/boot" folder on your Windows partition. Since Windows 7 has a "/Boot" folder, this can sometime prevent booting. Also the file /Boot/bcd seems to be missing.


Do this in a terminal in Ubuntu

```
sudo mount /dev/sda1 /mnt
cd /mnt
ls [Bb][Oo][Oo][Tt]/[Bb][Cc][Dd]
sudo mv boot boot.backup
```
Did the "ls"  command produce any output?

Reboot and see whether you can boot into Windows 7.

If you are not able to boot into Window 7, describe exactly what happens when you try to boot Window 7.

---

### Post by mikeody on 2010-01-19
A 'boot' and a 'Boot' !
Looks very much like my problem of a few days ago !!

---

### Post by efflandt on 2010-01-20
Just curious where you got /etc/grub.d/11_Windows from, and what you changed in /etc/grub.d/30_os-prober to not find Windows?  The default /etc/grub.d/30_os-prober usually has this section:

```
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
    Windows\ Vista*|Windows\ 7*)
    ;;
    *)
      cat << EOF
    drivemap -s (hd0) \${root}
EOF
    ;;
      esac

      cat <<EOF
    chainloader +1
}
EOF
```And you seem to be missing the part that plugs "drivemap -s (hd0) ${root}" into grub.cfg (maybe only an issue if initially booting from a different drive).  So I wonder if anything else is missing (my grub.cfg menuentry for WinXP ends up with more lines, but some are related GRUB_DEFAULT=saved in /etc/default/grub).

---

