---
title: "grub2 Fedora/Ubuntu 40_custom problem"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by andrewthomas on 2010-02-25
I installed Fedora on my second drive and am having problems pointing Ubuntu's grub2 to fedora's grub and vice versa.  I can boot either by changing the boot order in BIOS but would like to figure out how to boot to Ubuntu's drive and be able to select fedora from there.  

I have tried some of the advice in [http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777) and

[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

but I can't seem to get it right

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 
    150403411 on boot drive #1 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #2 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sdb3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   145,950,524   145,950,462   7 HPFS/NTFS
/dev/sda2         145,950,525   488,392,064   342,441,540   5 Extended
/dev/sda5         145,950,588   474,415,514   328,464,927  83 Linux
/dev/sda6         474,415,578   488,392,064    13,976,487  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   150,384,464   150,384,402   7 HPFS/NTFS
/dev/sdb2    *    150,384,465   150,794,064       409,600  83 Linux
/dev/sdb3         150,794,065   625,137,344   474,343,280  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        52A0C5F8A0C5E299                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        022b33a9-6c12-44bc-b573-114ffe8ae906   ext4                                     
/dev/sda6        358dff3b-4bc5-4a99-83bf-f86272b725db   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        80E8C127E8C11C72                       ntfs       backup                        
/dev/sdb2        55e6cae3-93df-4e78-aad8-101dd066b6b7   ext4                                     
/dev/sdb3        gYCbY8-9QgL-1to1-S2Ej-Skrn-ZQm4-eOui30 LVM2_member                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro  splash quiet vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    echo    Loading Linux 2.6.32-14-generic ...
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single  splash quiet vga=773
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52a0c5f8a0c5e299
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

echo "Adding Fedora" >&2
menuentry "Chainload Fedora on sdb2" {
set root=(hd1,2)
chainloader +1
} 
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.sh ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

echo "Adding Fedora" >&2
menuentry "Fedora (2.6.31.5-127.fc12.x86_64) on sdb2" {
set root=(hd1,2)
recordfail
insmod ext2
search --no-floppy --fs-uuid --set 55e6cae3-93df-4e78-aad8-101dd066b6b7
linux /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=/dev/mapper/vg_790x-lv_root setkmap=us
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
} 
### END /etc/grub.d/40_custom.sh ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=358dff3b-4bc5-4a99-83bf-f86272b725db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tmpfs /dev/shm tmpfs defaults,ro 0 0 

=================== sda5: Location of files loaded by Grub: ===================


 210.1GB: boot/grub/core.img
 210.2GB: boot/grub/grub.cfg
 210.3GB: boot/initrd.img-2.6.32-14-generic
 210.3GB: boot/vmlinuz-2.6.32-14-generic
 210.3GB: initrd.img
 210.3GB: vmlinuz

============================= sdb2/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_790x-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sdb
default=0
timeout=5
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.12-174.2.22.fc12.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.31.12-174.2.22.fc12.x86_64 ro root=/dev/mapper/vg_790x-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.12-174.2.22.fc12.x86_64.img
title Fedora (2.6.31.5-127.fc12.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=/dev/mapper/vg_790x-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
title Ubuntu 10.4 Lucid
    rootnoverify (hd1,4)
    chainloader +1
title Windows XP
    rootnoverify (hd1,0)
    chainloader +1

=================== sdb2: Location of files loaded by Grub: ===================


  77.0GB: grub/grub.conf
  77.0GB: grub/menu.lst
  77.0GB: grub/stage2
  77.0GB: initramfs-2.6.31.12-174.2.22.fc12.x86_64.img
  77.0GB: initramfs-2.6.31.5-127.fc12.x86_64.img
  77.0GB: vmlinuz-2.6.31.12-174.2.22.fc12.x86_64
  77.0GB: vmlinuz-2.6.31.5-127.fc12.x86_64
```

---

### Post by darkod on 2010-02-25
I'm not sure you can chainload to the MBR. In your chainload command you put set root=(hd1,2) which is correct but in this case Fedora's grub should be on /dev/sdb2, on the actual partition. Yours is on /dev/sdb, the MBR of the disk.

Reinstall Fedora's grub on /dev/sdb2, and the entry in ubuntu grub menu should work.

But since you can boot Fedora from karmic's grub2 I really see no point in chainloading. It also adds delay in booting.

---

### Post by andrewthomas on 2010-02-25
The way I have it set up now.  I can't boot to fedora from grub2.  The only way that I can boot fedora is changing the boot order in bios.  I just got rid of my 40_custom and now need know what to put in it.

---

### Post by darkod on 2010-02-25
Currently fedora grub is on the MBR of /dev/sdb. That's why you can boot it by changing drives in BIOS.
I don't know what to put in 40_custom when the bootloader is on the MBR. Usually it would be on the partition when you plan to chainload.
From within fedora, you should be able to install it to the partition with something like (remember these commands are for grub1 from fedora):

sudo grub
find /boot/grub/stage1

That should return something like (hd1,1) or maybe (hd0,1) because of the change in BIOS fedora might consider the disk where it is as hd0. So just do:

setup (hd1,1) or setup (hd0,1) depending what the previous command returned
quit

That should put grub from fedora on the /dev/sdb2 partition.

---

### Post by dE_logics on 2010-02-25
My suggestion mount the root partition of fedora and run - 

```
sudo dpkg-reconfigure grub-pc
```

I think the mounting part is optional...never tried this.

---

### Post by darkod on 2010-02-25
> **dE_logics said:**
> My suggestion mount the root partition of fedora and run - 

```
sudo dpkg-reconfigure grub-pc
```I think the mounting part is optional...never tried this.

And what should that achieve? The OP wants to chainload from karmic grub2 to fedora grub1.
I don't even think fedora uses grub2 and that command is for grub2 (grub-pc package is grub2).

---

### Post by darkod on 2010-02-25
> **andrewthomas said:**
>   I can't boot to fedora from grub2.

Did you try running

sudo update-grub

in karmic after you installed fedora?

---

### Post by andrewthomas on 2010-02-25
> **darkod said:**
> Did you try running

sudo update-grub

in karmic after you installed fedora?

Yeah.  I also tried to go into fedora and edit the grub.conf with no success

Do I have to get rid of the fedora's grub on the MBR of sdb for Ubuntu to be able to find my fedora installation in grub2?

I haven't tried to move fedora's grub from the MBR and would like to wait until I can get Ubuntu to recognize fedora in grub2 first.  

Any more ideas?  

Here is what the boot info looks like now

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 
    150403411 on boot drive #1 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #2 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sdb3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   145,950,524   145,950,462   7 HPFS/NTFS
/dev/sda2         145,950,525   488,392,064   342,441,540   5 Extended
/dev/sda5         145,950,588   474,415,514   328,464,927  83 Linux
/dev/sda6         474,415,578   488,392,064    13,976,487  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   150,384,464   150,384,402   7 HPFS/NTFS
/dev/sdb2    *    150,384,465   150,794,064       409,600  83 Linux
/dev/sdb3         150,794,065   625,137,344   474,343,280  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        52A0C5F8A0C5E299                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        022b33a9-6c12-44bc-b573-114ffe8ae906   ext4                                     
/dev/sda6        358dff3b-4bc5-4a99-83bf-f86272b725db   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        80E8C127E8C11C72                       ntfs       backup                        
/dev/sdb2        55e6cae3-93df-4e78-aad8-101dd066b6b7   ext4                                     
/dev/sdb3        gYCbY8-9QgL-1to1-S2Ej-Skrn-ZQm4-eOui30 LVM2_member                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro  splash quiet vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    echo    Loading Linux 2.6.32-14-generic ...
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single  splash quiet vga=773
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52a0c5f8a0c5e299
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

echo "Adding Fedora" >&2
menuentry "Chainload Fedora on sdb2" {
set root=(hd1,2)
chainloader +1
} 
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=358dff3b-4bc5-4a99-83bf-f86272b725db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tmpfs /dev/shm tmpfs defaults,ro 0 0 

=================== sda5: Location of files loaded by Grub: ===================


 210.1GB: boot/grub/core.img
 133.1GB: boot/grub/grub.cfg
 210.3GB: boot/initrd.img-2.6.32-14-generic
 210.3GB: boot/vmlinuz-2.6.32-14-generic
 210.3GB: initrd.img
 210.3GB: vmlinuz

============================= sdb2/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_790x-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sdb
default=0
timeout=5
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.12-174.2.22.fc12.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.31.12-174.2.22.fc12.x86_64 ro root=/dev/mapper/vg_790x-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.12-174.2.22.fc12.x86_64.img
title Fedora (2.6.31.5-127.fc12.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=/dev/mapper/vg_790x-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
title Ubuntu 10.4 Lucid
    rootnoverify (hd1,2)
    chainloader +1
title Windows XP
    rootnoverify (hd1,0)
    chainloader +1

=================== sdb2: Location of files loaded by Grub: ===================


  77.0GB: grub/grub.conf
  77.0GB: grub/menu.lst
  77.0GB: grub/stage2
  77.0GB: initramfs-2.6.31.12-174.2.22.fc12.x86_64.img
  77.0GB: initramfs-2.6.31.5-127.fc12.x86_64.img
  77.0GB: vmlinuz-2.6.31.12-174.2.22.fc12.x86_64
  77.0GB: vmlinuz-2.6.31.5-127.fc12.x86_64

```

---

### Post by darkod on 2010-02-25
No, you don't have to remove grub from /dev/sdb in order for karmic to find fedora. It seems /dev/sdb2 is your fedora /boot partition and it should be detected by karmic grub2.
Even though you are using LVM for fedora it shouldn't matter.

I'm not sure why it can't see it.

As for fedora grub.conf, that only applies when you are booting the fedora grub1.

---

### Post by andrewthomas on 2010-02-25
> **darkod said:**
> 

As for fedora grub.conf, that only applies when you are booting the fedora grub1.

I was trying to edit the grub.conf in fedora so it could try to load Ubuntu, but the changes that I made didn't work.  

As for grub2: Why is the 30_os-prober not able to find fedora?

---

### Post by oldfred on 2010-02-25
You can chainload to a partition or to another MBR if you have more than one drive. The advantage of chainloading is you are using the grub menu of the native system that gets updated with new kernels. 

Chainload to partition (PBR)

# Entry N - Chainload another bootloader on sdaN
menuentry "Chainload my OS" {
    set root=(hd0,N)
    chainloader +1
}

If you add this to 40_custom you will be able to boot.
Chainload to a MBR:

# Entry N - Chainload another bootloader on sdb (hd1)
menuentry "Chainload my OS on sdb" {
    set root=(hd1)
    chainloader +1
}

---

### Post by andrewthomas on 2010-02-25
> **oldfred said:**
> 

If you add this to 40_custom you will be able to boot.
Chainload to a MBR:

# Entry N - Chainload another bootloader on sdb (hd1)
menuentry &quot;Chainload my OS on sdb&quot; {
    set root=(hd1)
    chainloader +1
}


I added this to my 40_custom and updated grub. When I rebooted, the item  showed up in my menu, but when selected all I got was a blinking cursor  in the upper-left corner of a blank screen.

Any ideas?

---

### Post by QIII on 2010-02-25
Try editing 40_custom and changing


```
set root=(hd1)
```

to

```
set root=(hd1,x)
```

where x is the partition where your MBR resides in Fedora.

---

### Post by andrewthomas on 2010-02-25
> **QIII said:**
> Try editing 40_custom and changing


```
set root=(hd1)
```to

```
set root=(hd1,x)
```where x is the partition where your MBR resides in Fedora.


I had no luck with this either. Wouldn't grub have to be written to the partition instead of the MBR for this to work?

---

### Post by oldfred on 2010-02-25
QIII version will work if you have installed Fedora's grub to the PBR that has Fedora. 
Are you still able to boot Fedora from sdb with the drive selection? Chainload just jumps to another boot loader, grub, window, lilo etc. If not found it crashes the way you see it. I have chainloaded to the MBR of another drive.
I amybe should have posted with code tags as 
menuentry &quot;Chainload my OS on sdb&quot 
the &quot is not correct but should be just ".

```
menuentry "Chainload my OS on sdb" {
    set root=(hd1)
    chainloader +1
} 	
```

---

### Post by andrewthomas on 2010-02-25
> **oldfred said:**
> 
Are you still able to boot Fedora from sdb with the drive selection? 

Yes, I am.

> **oldfred said:**
> 
I amybe should have posted with code tags as 
menuentry &quot;Chainload my OS on sdb&quot 
the &quot is not correct but should be just ".

```
menuentry "Chainload my OS on sdb" {
    set root=(hd1)
    chainloader +1
}     
```

I think that you did, because I have the " and not the &quot

---

### Post by QIII on 2010-02-25
> **andrewthomas said:**
> I had no luck with this either. Wouldn't grub have to be written to the partition instead of the MBR for this to work?


Yes.  Sorry.  Hasty.

---

### Post by andrewthomas on 2010-02-25
> **QIII said:**
> Yes.  Sorry.  Hasty.


Not a problem.  I just don't understand why if I select the drive in BIOS it boots fine, but I can't point to it from the other drive.

---

### Post by oldfred on 2010-02-25
Did you make any other changes to the default lines in 40_custom?

An alternative version that should be equivalent, they use third drive:

[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

Another Linux example

menuentry “Drive sdc = hd2 by chainloader”  {
chainloader  (hd2)+1
}

If a bootloader (e.g., GRUB 2) has been installed to the Master Boot Record of drive sdc (= hd2), the menuentry will boot that hard drive by turning control over to the bootloader in its MBR.

For this example to work, a bootloader (e.g., GRUB 2) must be installed to the Master Boot Record of drive sdc (= hd2).  To install GRUB 2 to the Master Boot Record of drive sdc:
sudo grub-install /dev/sdc

---

### Post by andrewthomas on 2010-02-25
> **oldfred said:**
> Did you make any other changes to the default lines in 40_custom?


No I didn't.  Thanks for the link.  I need to spend some time later reading the entire post so I can figure out what is going on.  

BTW here is my 40_custom file after I tried the alternate entry ( it had the same result :confused:)

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

# Entry N - Chainload another bootloader on sdb (hd1)
menuentry "Drive Sdb = hd1 by chainloader" {
chainloader (hd1)+1
}
```

---

### Post by darkod on 2010-02-25
> **andrewthomas said:**
> No I didn't.  Thanks for the link.  I need to spend some time later reading the entire post so I can figure out what is going on.  

BTW here is my 40_custom file after I tried the alternate entry ( it had the same result :confused:)

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

# Entry N - Chainload another bootloader on sdb (hd1)
menuentry "Drive Sdb = hd1 by chainloader" {
chainloader (hd1)+1
}
```

To ask the obvious question here, you are running update-grub after any change to the config files right?

---

### Post by QIII on 2010-02-25
> **darkod said:**
> To ask the obvious question here, you are running update-grub after any change to the config files right?

Doh!  We all should have asked that question hours ago!  (Insert sheepish grin here.)

---

### Post by andrewthomas on 2010-02-25
> **darkod said:**
> To ask the obvious question here, you are running update-grub after any change to the config files right?

Yes I am.
I even tried out grub-mkconfig for the hell of it
```
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro  splash quiet vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    echo    Loading Linux 2.6.32-14-generic ...
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=022b33a9-6c12-44bc-b573-114ffe8ae906 ro single  splash quiet vga=773
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 022b33a9-6c12-44bc-b573-114ffe8ae906
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52a0c5f8a0c5e299
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

# Entry N - Chainload another bootloader on sdb (hd1)
menuentry "Drive Sdb = hd1 by chainloader" {
chainloader (hd1)+1
}
### END /etc/grub.d/40_custom ###
```

---

### Post by oldfred on 2010-02-25
It may be the same problem we have with windows as windows wants to be the first drive.  Lookiing back at your Fedora entries they show they are drive hd0, so maybe by booting Ubuntu first Fedora now is drive hd1? I would think chaining into the MBR would reset the drive order.

This is a guess if you want to experiment. This is from a window entry, not sure if it should be hd0 or hd1, the drivemap -s means switch drives but I do not know what the definition of {root} is:

       drivemap -s (hd0) ${root}
       chainloader +1

or this 

       drivemap -s (hd0) (hd1)
       chainloader +1

---

### Post by oldfred on 2010-02-25
Thinking some more, when you use the BIOS to boot each drive thinks it is the first drive. The solution may be to reinstall Fedora's grub and config file to it knows it is on the second drive.

---

### Post by andrewthomas on 2010-02-25
I was looking at this link from [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
that oldfred had pointed out to me and I decided to try 

```
menuentry "Drive Sdb = hd1 by chainloader" {
drivemap (hd0) (hd1)
drivemap (hd1) (hd0)
set root=(hd0)
chainloader (hd1)+1
}
```this did load the fedora grub menu, but after I selected the kernel, I got a message stating:
"Kernel panic -not syncing : out of memory and killable processes"


> **oldfred said:**
> Thinking some more, when you use the BIOS to boot each drive thinks it is the first drive. The solution may be to reinstall Fedora's grub and config file to it knows it is on the second drive.

How would I do this? Or should I try another variation of the drivemap command?

---

### Post by oldfred on 2010-02-25
I have seen more of the drivemap with the -s switch so try that. I am not sure if the double entry still works?

I also might try this as it is the partition:
drivemap -s (hd0) (hd1)
       set root = (hd1,2)
chainloader (hd1)+1

---

### Post by andrewthomas on 2010-02-26
> **oldfred said:**
> I have seen more of the drivemap with the -s switch so try that. I am not sure if the double entry still works?

I also might try this as it is the partition:
drivemap -s (hd0) (hd1)
       set root = (hd1,2)
chainloader (hd1)+1

For some reason when I use ```
 drivemap -s (hd0) (hd1)
```instead of
```
drivemap (hd0) (hd1)
drivemap (hd1) (hd0)
```the set root statement results in  "error: not an assignment"
but if I remove the set root line I get sent to Fedora's grub menu.
From there I can press e to edit the commands and the first line is
```
root (hd0,1)
``` I tried to change this with no luck
Any more ideas?
Thank you for all your help.

---

### Post by oldfred on 2010-02-26
I am just guessing so I am not sure I am helping. With a chainload set root should not be there as it is a chainload. Chainload is just causing the system to use another boot loader to load that system rather than direct booting. I am pretty sure the issue is related to drive 0 and drive 1 issues, but beyond that I do not know. All your Fedora statements make it the first drive but when booting thru both it must see it as the second and not work.

 I am also surprised that there  is a difference in the two versions of drivemap but that is how we learn sometimes.

---

### Post by darkod on 2010-02-26
> **oldfred said:**
> I am just guessing so I am not sure I am helping. With a chainload set root should not be there as it is a chainload. Chainload is just causing the system to use another boot loader to load that system rather than direct booting. I am pretty sure the issue is related to drive 0 and drive 1 issues, but beyond that I do not know. All your Fedora statements make it the first drive but when booting thru both it must see it as the second and not work.

 I am also surprised that there  is a difference in the two versions of drivemap but that is how we learn sometimes.

I believe the set root is still used but it needs to be before the drivemap command. From windows xp analogy, with set root you need to tell it where to look for the other bootloader, and with drivemap you're "lying" that it's the first hdd.

---

### Post by andrewthomas on 2010-02-26
Well, with 
```
menuentry "Drive Sdb = hd1 by chainloader" {
drivemap -s (hd0) (hd1)
chainloader (hd1)+1
}
```I am able to get to fedora's grub.  I then tried to switch the drives again by adding the map line after the root line and am still unable to boot

```
root (hd0,1)
map (hd1) (hd0)
....
....
```I guess that having to switch the boot order in BIOS isn't such a big deal.  I just think that since I am getting to the fedora grub menu I should be able to find the right commands to enter.

---

### Post by andrewthomas on 2010-02-27
I have come to the conclusion that it is not possible to chainload from a  grub on a MBR to another grub on another MBR.  Chainloading another  bootloader is only possible if the second bootloader is on a partition.    
Is this correct?[COLOR=Silver]
[/COLOR]Now have edited my /etc/grub.d/40_custom to
```
 #!/bin/sh
exec tail -n +3 $0
menuentry "Direct to Fedora 12"{
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 55e6cae3-93df-4e78-aad8-101dd066b6b7
linux /vmlinuz-2.6.31.12-174.2.22.fc12.x86_64 ro root=UUID=gYCbY8-9QgL-1to1-S2Ej-Skrn-ZQm4-eOui30 LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}
```This starts to load Fedora then prints "Fedora 12" in blue in the bottom right corner of the screen, then repeats the message FATAL : could not load /lib/modules/2.6.31.12-174.2.22.fc12.x86_64/modules.dep all the way down the screen before stating something about not booting going to sleep.

What could be the problem?

---

### Post by andrewthomas on 2010-02-27
> **andrewthomas said:**
> I have come to the conclusion that it is not possible to chainload from a  grub on a MBR to another grub on another MBR.  Chainloading another  bootloader is only possible if the second bootloader is on a partition.    
Is this correct?[COLOR=Silver]
[/COLOR]
No it is not correct.  I just haven't figured out how to do it with grub2.  With fedora's legacy grub

```
title Ubuntu 10.4 Lucid
    rootnoverify (hd1)
    chainloader +1

```it is simple.  Ain't that a bitch

---

### Post by oldfred on 2010-02-27
I stand by my original chainboot entry (I have done it), not some of the updates tha tmay have been wrong. I have done it that way. I was pleasantly supprise that the drivemap command started to work, but I am now sure that the problem is both systems think they are the first drive. When you boot each individually are you unplugging the other drive, not just selecting the other in BIOS (F12 or whatever)?

The drivemap command must get grub .97 to boot to the Fedora menu, but Fedora must rescan drives rather than follow the drivemap so its menu is not correct. 

If all this is true a reinstall of Fedora's grub and recreate it's menu grub.conf so it has the correct drive.

title Fedora (2.6.31.12-174.2.22.fc12.x86_64)
    root (hd0,1)
this root needs to be (hd1,1) and all the other entries. You might try manually changing one entry with the drivemap in ubuntu's grub, or eliminated drivemap totally and reinstall Fedora's grub with both drives connected.

---

### Post by andrewthomas on 2010-02-27
Thank you so much for your help oldfred.  Sorry for wasting your time. I have to have Fedora first in the boot order for some unknown reason.

> **oldfred said:**
> I stand by my original chainboot entry (I have done it), not some of the updates that may have been wrong.
You are right: your original chainboot entry is correct. I have gotten it to work by booting to the Fedora hd first.  Then I can go back and forth all I want and select whenever I choose. 

For some reason, if I set Ubuntu's drive to load first in BIOS, I can not chainload to Fedora's grub. I can select the other entry and this will chainload itself though.  This must be some kind of bug.

 > **oldfred said:**
> I have done it that way. I was pleasantly supprise that the drivemap command started to work, but I am now sure that the problem is both systems think they are the first drive. When you boot each individually are you unplugging the other drive, not just selecting the other in BIOS (F12 or whatever)?

No, I am selecting them in BIOS. During install Ubuntu's was actually first.  I picked Sdb during the Fedora installation. Although that point is moot now.:P

```
# from grub2 40_custom file
menuentry "chainload to Fedora's grub if Fedora's 1st in BIOS"{
set root=(hd0)
chainloader +1
}
menuentry "chainload to Fedora's grub if Ubuntu's 1st in BIOS"{
set root=(hd1)
chainloader +1
}
``````
# grub/menu.lst entries
title Ubuntu's Grub2 if Fedora's 1st in BIOS
    rootnoverify (hd1)
    chainloader +1
title Ubuntu's Grub2 if Ubuntu's 1st in BIOS
    rootnoverify (hd0)
    chainloader +1
```

---

### Post by oldfred on 2010-02-27
You did not waste my time, I like trying to understand these things and if anything I gave some incorrect advice that wasted your time.

So which entry works? When you boot you have to choose in BIOS one drive or the other and that should mean only one entry works for each system??

---

### Post by andrewthomas on 2010-02-27
> **oldfred said:**
> You did not waste my time, I like trying to understand these things and if anything I gave some incorrect advice that wasted your time.

So which entry works? When you boot you have to choose in BIOS one drive or the other and that should mean only one entry works for each system??

All is well if I list Fedora's drive first in the BIOS boot priority.  The entries all work.  It is just that one entry will chainload itself and the other will chainload to the other drive's MBR.  

As for when I list Ubuntu's drive first in the BIOS boot priority, the entry to chainload the other drive's grub fails, while the other entry will chainload itself. I have yet to successfully chainload Fedora's drive when booting to Ubuntu first, nor have I been successful with the direct entry to fedora's /boot partition ( the entry looks sound, but crashes loading a kernel module.)   

Keep in mind that when I have Fedora's drive first in priority, ALL the entries work.  I can loop back and forth and each grub is able to chainload itself.

Fedora's drive is a PATA drive and Ubuntu's is a SATA drive.  I read in a few places that this may cause complications. 

 I am still stumped as to why I can't boot to Ubuntu's drive first and then chainload Fedora's drive.  I used to have another version of ubuntu on the PATA drive and I was be able to boot that installation from Grub2 on the MBR of the SATA drive (although ubuntu was auto-detecting itself.)

Oh, well.  At least it works.  I just have to wait that extra few seconds for Fedora's grub to load, since I usually am using Ubuntu.

---

### Post by oldfred on 2010-02-27
Glad you got it working even if it is from Fedora and not Ubuntu.

It is possible that Pata vs. Sata can cause issues, but I do not know for sure.

---

### Post by andrewthomas on 2010-02-27
Thanks again oldfred.  I am kind of glad that it didn't work right away.  I learned a lot more about grub/grub2,trying to figure why it wasn't working, than I would have otherwise.:)

---

### Post by kansasnoob on 2010-02-27
This thread had sparked some interest in me because I've run into problems in the past getting grub2 to recognize Fedora 12 so I decided to install Fedora myself on my drive sdb and I chose to install Fedora's grub to sdb2:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.32-14-generic
Found initrd image: /boot/initrd.img-2.6.32-14-generic
Found linux image: /boot/vmlinuz-2.6.32-13-generic
Found initrd image: /boot/initrd.img-2.6.32-13-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda11
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda13
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Fedora release 12 (Constantine) on /dev/sdb2
done

```

Of course I haven't rebooted yet, we'll see what happens. And both of my drives are IDE with sda the master and sdb the slave so this may be a totally different thing.

And just BTW I see you have this solved but thought this might be as good of a place as any for myself, darkod, oldfred, presence*?, meierfra, and others to compare notes :)

Oh and I'm using Lucid's grub2:

```
lance@lance-desktop:~$ grub-install -v
grub-install (GNU GRUB 1.98~20100128-1ubuntu3)

```

Also this is the grub.cfg entry automatically produced by "update-grub":

```
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/sdb2)" {
	insmod ext2
	set root=(/dev/sdb,2)
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
}
```

Of course the proof's in the pudding so I'll let you know if I boot or not :)

Success! All boots just fine, in case it might help someone else I'll atach my Boot Info Script results.

[ATTACH]148486[/ATTACH]

We can hope this all helps someone else in the future :D

---

### Post by oldfred on 2010-02-28
kansasnoob - It looks like your use of grub 1.98 has solved the problem as it must have a updated osprober that does a better job. That will solve many issues when Lucid is official but should we be recommending 1.98 now? I have seen several other posts where that also seemed to solve an issue. Grub 1.97 has worked just fine for me on two computers so I am assuming many users do not have issues but those that do have unusual installs may be helped by a newer grub?? 

I also noticed the root line has a slightly different format with a /dev/sdb for both windows and fedora.
set root=(/dev/sdb,2)

---

### Post by kansasnoob on 2010-02-28
> I am assuming many users do not have issues but those that do have unusual installs may be helped by a newer grub?? 

That is my exact thought. Basically "if it ain't broke don't fix it", but if things seem very problematic install the newest "grub-common", and "grub-pc" packages from the Lucid package list:

[http://packages.ubuntu.com/lucid/admin/grub-common](http://packages.ubuntu.com/lucid/admin/grub-common)

[http://packages.ubuntu.com/lucid/admin/grub-pc](http://packages.ubuntu.com/lucid/admin/grub-pc)

The "os-prober" package has not changed from Karmic to Lucid yet, or at least not that I can see.

Of course you must first purge the old packages and I like to start with a new /boot/grub directory after backing up the old directory.

Then I like to follow up by actually reinstalling grub to the proper mbr(s) or partitions, and of course "update-grub".

> I also noticed the root line has a slightly different format with a /dev/sdb for both windows and fedora.
set root=(/dev/sdb,2) 

I had not noticed that. I'll have to look a bit closer.

If I hadn't said so earlier you did an excellent job with this :D

I'd just been curious what would happen if I actually tried it. I might try booting into my Karmic and see what happens if I hand boot off to it. But even booting Karmic is an "iffy" proposition for me due to problems with it's X causing crashes.

I'd also like to try this with a SATA drive added to the mix but my board is still SATA 1.5 and all of my spare SATA drives are 3.0 only :sad:

---

### Post by andrewthomas on 2010-03-01
> **oldfred said:**
> Glad you got it working even if it is from Fedora and not Ubuntu.

It is possible that Pata vs. Sata can cause issues, but I do not know for sure.

Well, I now have moved Fedora's grub from the MBR of sdb (PATA) to it's partition and installed grub2 on the MBR.  Now I don't have to go through Fedora's grub to get to Ubuntu.

> **kansasnoob said:**
> ```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.32-14-generic
Found initrd image: /boot/initrd.img-2.6.32-14-generic
Found linux image: /boot/vmlinuz-2.6.32-13-generic
Found initrd image: /boot/initrd.img-2.6.32-13-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda11
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda13
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Fedora release 12 (Constantine) on /dev/sdb2
done

```Also this is the grub.cfg entry automatically produced by "update-grub":

```
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/sdb2)" {
    insmod ext2
    set root=(/dev/sdb,2)
    search --no-floppy --fs-uuid --set  4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
    linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro  root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8  SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
}
```
I do wish that performing "update-grub" on my machine would produce an entry for Fedora, but oh well.
BTW, I am using the latest version.
```
andrew@790Fx:~$ grub-install -v
grub-install (GNU GRUB 1.98~20100128-1ubuntu3)
```

---

### Post by andrewthomas on 2010-03-01
> **oldfred said:**
> Glad you got it working even if it is from Fedora and not Ubuntu.

It is possible that Pata vs. Sata can cause issues, but I do not know for sure.

I finally found the problem.  There was a BIOS option setting in the boot loader device selection in the Fedora installer. Since I just had Fedora installed a for few days, I reinstalled and it now works just like I wanted from the start.  Check out the screenshot.

---

