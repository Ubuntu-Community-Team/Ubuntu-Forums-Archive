---
title: "how to return to ubuntu without install cd"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by rajeevisonline on 2010-12-11
I have installed ubuntu on a specific partition...installed[[COLOR=blue][FONT=Verdana][FONT=Verdana]windows[/FONT][/FONT][/COLOR] ]("http://www.linuxforums.org/forum/#")and mandriva on two other  partitions...now i would like to go back to ubuntu..is there any way i  can do this unfortunately i have no bootloader installed installed on  the ubuntu partition..is there any way to [[COLOR=blue][FONT=Verdana][FONT=Verdana]install[/FONT][/FONT][/COLOR][]("http://www.linuxforums.org/forum/#")  a bootloader on the mbr or elsewhere to retrieve the ubuntu  installation...preferably without live cd

---

### Post by sikander3786 on 2010-12-11
You would definitely need a Live CD or USB in order to re-install Grub.

Is any of those OS bootable i.e, either Windows or Mandriva?

If you are able to boot Mandriva or an Ubuntu Live CD or USB, please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or you can also try booting using a Super Grub disk and re-install Grub from inside your Ubuntu install.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by rajeevisonline on 2010-12-11
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 475572251 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Mandriva Linux release 2010.1 
                       (Official) for i586 Kernel 2.6.33.5-desktop-2mnb on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   291,676,139   291,676,077  83 Linux
/dev/sda2    *    292,013,505   327,211,919    35,198,415   7 HPFS/NTFS
/dev/sda3         327,211,920   472,712,624   145,500,705  83 Linux
/dev/sda4         473,660,460   488,392,064    14,731,605   5 Extended
/dev/sda5         473,660,523   484,215,164    10,554,642  83 Linux
/dev/sda6         484,215,228   488,392,064     4,176,837  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4ab65724-7104-48c2-80c3-c332ddd84c8e   ext4                                     
/dev/sda2        0E027A9A027A870D                       ntfs                                     
/dev/sda3        b3df30f2-d3a7-45db-97b9-ddf60c0d672a   ext4       BackUp                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        14f8ebbc-4745-4bcd-9742-f2d9f4858c3a   ext3                                     
/dev/sda6        dc32e9f4-636e-47ab-b848-8d29776692bd   ext2       Backup2                       
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,noatime,acl)
/dev/sda2        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=4ab65724-7104-48c2-80c3-c332ddd84c8e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=4ab65724-7104-48c2-80c3-c332ddd84c8e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4ab65724-7104-48c2-80c3-c332ddd84c8e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4ab65724-7104-48c2-80c3-c332ddd84c8e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4ab65724-7104-48c2-80c3-c332ddd84c8e
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4ab65724-7104-48c2-80c3-c332ddd84c8e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dd1234d5-51d4-4b29-84eb-472f44904145 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
  90.0GB: boot/grub/grub.cfg
  94.1GB: boot/initrd.img-2.6.32-24-generic
  36.6GB: boot/initrd.img-2.6.32-25-generic
  86.0GB: boot/vmlinuz-2.6.32-24-generic
 141.8GB: boot/vmlinuz-2.6.32-25-generic
  36.6GB: initrd.img
  94.1GB: initrd.img.old
 141.8GB: vmlinuz
  86.0GB: vmlinuz.old

=========================== sda5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=14f8ebbc-4745-4bcd-9742-f2d9f4858c3a splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title windows
root (hd0,1)
makeactive
chainloader +1

title alt_windows
root (hd0,1)
makeactive
chainloader +1

=============================== sda5/etc/fstab: ===============================

# Entry for /dev/sda5 :
UUID=14f8ebbc-4745-4bcd-9742-f2d9f4858c3a / ext3 acl,noatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sda2 :
UUID=0E027A9A027A870D /media/windows ntfs-3g defaults,umask=000 0 0
none /proc proc defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


 242.9GB: boot/grub/menu.lst
 243.1GB: boot/grub/stage2
 247.7GB: boot/initrd-2.6.33.5-desktop-2mnb.img
 247.7GB: boot/initrd-desktop.img
 247.7GB: boot/initrd.img
 247.3GB: boot/vmlinuz
 247.3GB: boot/vmlinuz-2.6.33.5-desktop-2mnb
 247.3GB: boot/vmlinuz-desktop
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

---

### Post by sikander3786 on 2010-12-11
I can see a few problems in that output and in order to fix them, you definitely need to boot an Ubuntu Live CD or USB. Can you grab one somewhere?

---

### Post by rajeevisonline on 2010-12-12
can somebody post a default syslinux.cfg file or a boot.cfg file for 10.04.1 as an attachment..so that i can edit it accoding to my bootscript.info

---

