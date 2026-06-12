---
title: "Need Urgent help with Grub 2 and three OS"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-14
i now have three is installed on my computer one is windows 7 on sdb1  two is windows server 2008 on sda3 and ubuntu 10.04 on sda1 and sda2 is  swap now when i installed grub 2 on bote mbr using this commands: 

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev  /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo  chroot /mnt

Code:

grub-install /dev/sda

Code:

grub-install /dev/sdb

Code:

exit

Code:

sudo umount /mnt/dev && sudo umount /mnt/proc && sudo  umount /mnt
```it detected seven and ubuntu but not 2008 how can i  add it there?

thanks in advance.

---

### Post by dino99 on 2010-02-14
could you boot ?
i don't understand what you are doing with mount & unmount things.

into console:
- sudo grub-mkconfig
- sudo update-grub

---

### Post by VMC on 2010-02-14
Run the [boot-info-script]("http://sourceforge.net/projects/bootinfoscript/") so we can see actually how your booting is set up.

---

### Post by aviramof on 2010-02-14
here you go:

thanks in advance:

```
                    Boot Info Script 0.54 of  February 14th, 2010                         

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    52,436,159    52,436,097  83 Linux
/dev/sda2          52,436,160    58,733,639     6,297,480  82 Linux swap / Solaris
/dev/sda3          58,733,640   160,826,714   102,093,075   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sdb2          78,157,824   162,043,903    83,886,080   7 HPFS/NTFS
/dev/sdb3         162,043,904   312,577,499   150,533,596   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4cd8b522-0312-4d4d-8db1-990a710da630   ext4                                     
/dev/sda2        07ec86a2-0540-4289-8c40-c97097b6306e   swap                                     
/dev/sda3        22CE2E75441D4836                       ntfs                                     
/dev/sdb1        C44451F64451EC24                       ntfs       Windows 7                     
/dev/sdb2        58544AAE544A8F26                       ntfs       &#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;           
/dev/sdb3        EA9635979635656B                       ntfs       &#1491;&#1497;&#1505;&#1511; &#1502;&#1511;&#1493;&#1502;&#1497;           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
set locale_dir=($root)/boot/grub/locale
set lang=he
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
menuentry "Ubuntu, with Linux 2.6.32-13-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
    linux    /boot/vmlinuz-2.6.32-13-generic root=UUID=4cd8b522-0312-4d4d-8db1-990a710da630 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-13-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
    echo    Loading Linux 2.6.32-13-generic ...
    linux    /boot/vmlinuz-2.6.32-13-generic root=UUID=4cd8b522-0312-4d4d-8db1-990a710da630 ro single  splash vga=795
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-13-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=4cd8b522-0312-4d4d-8db1-990a710da630 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=4cd8b522-0312-4d4d-8db1-990a710da630 ro single  splash vga=795
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4cd8b522-0312-4d4d-8db1-990a710da630
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c44451f64451ec24
    chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4cd8b522-0312-4d4d-8db1-990a710da630 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=07ec86a2-0540-4289-8c40-c97097b6306e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.6GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
   6.7GB: boot/initrd.img-2.6.32-12-generic
   6.8GB: boot/initrd.img-2.6.32-13-generic
   6.7GB: boot/vmlinuz-2.6.32-12-generic
   6.7GB: boot/vmlinuz-2.6.32-13-generic
   6.8GB: initrd.img
   6.7GB: initrd.img.old
   6.7GB: vmlinuz
   6.7GB: vmlinuz.old
```

---

### Post by VMC on 2010-02-14
I don't see anything wrong with your boot info. My only questions is, how is your BOIS setup. Is it set to boot off of the first hard drive?

Also, what exactly is the problem? Do you see the grub menu when you boot up?

Edit: I see. Windows 2008 doesn't show up. Add a menuentry to 40_custom, like so:
```
menuentry "Windows Server 2008 (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 22CE2E75441D4836
    chainloader +1
}
```

---

### Post by ubername on 2010-02-14
> **dino99 said:**
> could you boot ?
i don't understand what you are doing with mount & unmount things.

into console:
- sudo grub-mkconfig
- sudo update-grub

Not sure why you would want to run grub-mkconfig before grub-update? (without any other parameters, as above) Is it just to see the output before it gets written to grub.cfg?

---

### Post by aviramof on 2010-02-15
my bios is set to work from what for me is the first hd but for ubuntu  it's sdb i really don't know why.

i tried to add 40_custom but it didn't worked it said bootmgr is missing  press ctrl-alt-delete to restart,

but i did discoverd something i should have noticed it earlier when i  press 

Windows 7 (loader) (on /dev/sdb1) i get a dual boot there to seven or windows server 2008 so i do 

have a way to enter windows server 2008 altoughe not the way i wanted it.:)

and maybe this problem and why os-prober didn't discovered this os should be looked at.

thanks for your help.

---

