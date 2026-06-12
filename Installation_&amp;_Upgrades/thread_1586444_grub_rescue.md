---
title: "grub rescue"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by aaira on 2010-10-02
I am newbie to have dual boot ubuntu
I have tried every combination but cann't seem to have dual boot working
I always end up with grub rescue prompt.
Below please find the output form fdisk and boot_info_script055.sh
Please help me to  configure dual-boot system (WINDOWS XP and Ubuntu 10.04)
--------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e622e61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18121   145553898    7  HPFS/NTFS
/dev/sda2           18121       30061    95908864   83  Linux
/dev/sda4           30061       30402     2734080   82  Linux swap / Solaris

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2d724129

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3878     3908992+   b  W95 FAT32
---------------------------------------------------------------------------
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /BOOTLNX.BIN is trying to chain 
                       load sector #356870144 on boot drive #1 BootPart in 
                       the file /ubunlba.bin is trying to chain load sector 
                       #356870144 on boot drive #1 BootPart in the file 
                       /ubuntu.bin is trying to chain load sector #356870144 
                       on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   291,107,858   291,107,796   7 HPFS/NTFS
/dev/sda2         291,108,864   482,926,591   191,817,728  83 Linux
/dev/sda4         482,926,592   488,394,751     5,468,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76E8430FE842CCD5                       ntfs                                     
/dev/sda2        47e271bb-61ef-433a-ac31-d35e92d45b17   ext4                                     
/dev/sda4        20b23bdf-755f-40bf-9699-6db15cae5b89   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        10D2-249A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
C:\ubuntu.bin="Ubuntu" 
c:\ubunlba.bin=" UbunLBA" 
c:\BOOTLNX.BIN=" BOOT_LNX" 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 47e271bb-61ef-433a-ac31-d35e92d45b17
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 47e271bb-61ef-433a-ac31-d35e92d45b17
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 47e271bb-61ef-433a-ac31-d35e92d45b17
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=47e271bb-61ef-433a-ac31-d35e92d45b17 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 47e271bb-61ef-433a-ac31-d35e92d45b17
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=47e271bb-61ef-433a-ac31-d35e92d45b17 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 47e271bb-61ef-433a-ac31-d35e92d45b17
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 47e271bb-61ef-433a-ac31-d35e92d45b17
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 76e8430fe842ccd5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=47e271bb-61ef-433a-ac31-d35e92d45b17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=20b23bdf-755f-40bf-9699-6db15cae5b89 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 168.5GB: boot/grub/core.img
 170.6GB: boot/grub/grub.cfg
 149.5GB: boot/initrd.img-2.6.32-24-generic
 168.5GB: boot/vmlinuz-2.6.32-24-generic
 149.5GB: initrd.img
 168.5GB: vmlinuz

```

---

### Post by garvinrick4 on 2010-10-02
Put in Live Cd (install Cd) choose try Ubuntu and go to a terminal and:
```
sudo mkdir /media/root
```
```
sudo mount /dev/sda2 /media/root
```
```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```
```
sudo umount /media/root
``` (not a typo)
```
sudo halt
```
Take Cd out.
Boot machine and choose ubuntu and when boots open a terminal and:
```
sudo update-grub
```

---

### Post by aaira on 2010-10-02
I followed all the steps to the letter but no rescue
At bootup after BIOS screens I get following message.


[FONT=Courier New]unknown filesystem.
grub rescue>[/FONT]

Any clue what else can be wrong?

---

### Post by garvinrick4 on 2010-10-02
Does Windows boot?

---

### Post by aaira on 2010-10-02
No Windows does not boot. I just get  grub rescue> prompt
(unless there are some special commands to boot windows from grub rescue> prompt?
Any clues?

Do you think I may have some hardware issues I am using Dell Inspiron 8500

---

### Post by garvinrick4 on 2010-10-02
Lets get Windows booting first and then get Ubuntu booting.
Put in Live Cd and in Terminal:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Now take out CD and boot into windows

---

### Post by garvinrick4 on 2010-10-02
Dell has their own drivers but do not think is the problem.
They take Windows apart and give you seperate disk of their drivers instead of
using public domain drivers so if you stray to far from them they can smack you
on the knuckles. But this should be a working system. Lets keep at it.

---

### Post by garvinrick4 on 2010-10-02
Given that Windows boots now.
Now lilo should have over written anything in mbr. So now lets put grub2 in mbr with
post 2 again to overwrite lilo so as to boot both Windows and Ubuntu.

---

### Post by xieon on 2010-10-02
> **garvinrick4 said:**
> Lets get Windows booting first and then get Ubuntu booting.
Put in Live Cd and in Terminal:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Now take out CD and boot into windows

I was having this same problem, and this worked perfect. Restored my mbr, then I was able to reinstall Ubuntu because the version I had was corrupted.

---

