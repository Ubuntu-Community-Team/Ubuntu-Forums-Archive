---
title: "Grub Error No Such Disk"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by kize37 on 2009-12-06
My wife is going to kill me!!!   I have been playing around with Ubuntu live for a few days and really like it.  I just installed Ubuntu with dual booting in XP.  Now I cannot boot.

Grub loading:
Grub Error
No such disk.

I'm using the live cd now just so I can get help.  I used the boot script in another thread and here it is.
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=544ad9c1-cec5-49dd-b680-3a338ed0d92e)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13ab13aa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   163,557,764   163,557,702   7 HPFS/NTFS
/dev/sdb2         163,557,765   234,436,544    70,878,780   5 Extended
/dev/sdb5         163,557,828   231,432,389    67,874,562  83 Linux
/dev/sdb6         231,432,453   234,436,544     3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="781C15701C152AA0" TYPE="ntfs" 
/dev/sdb1: UUID="F24852ED4852AFD9" TYPE="ntfs" 
/dev/sdb5: UUID="544ad9c1-cec5-49dd-b680-3a338ed0d92e" TYPE="ext4" 
/dev/sdb6: UUID="325dbb53-5ad2-4dc1-a4c1-75a378b137ce" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 544ad9c1-cec5-49dd-b680-3a338ed0d92e
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
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 544ad9c1-cec5-49dd-b680-3a338ed0d92e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=544ad9c1-cec5-49dd-b680-3a338ed0d92e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 544ad9c1-cec5-49dd-b680-3a338ed0d92e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=544ad9c1-cec5-49dd-b680-3a338ed0d92e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 781c15701c152aa0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f24852ed4852afd9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=544ad9c1-cec5-49dd-b680-3a338ed0d92e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=325dbb53-5ad2-4dc1-a4c1-75a378b137ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  83.7GB: boot/grub/grub.cfg
  83.7GB: boot/initrd.img-2.6.31-14-generic
  83.7GB: boot/vmlinuz-2.6.31-14-generic
  83.7GB: initrd.img
  83.7GB: vmlinuz

```

Help Please!

Thanks,

Todd

---

### Post by raymondh on 2009-12-06
Todd,

In BIOS, what is the HD set to boot first?  Try sdb.

---

### Post by kize37 on 2009-12-06
I will have to re-boot my system.  I think I only have 1 option HD.  I will get back to you shortly.

Todd

---

### Post by kize37 on 2009-12-06
Got it!!  Works Great.

This may help some others having the same problem.  I'm using the Dell Optiplex  GX270. 

When I entered the bios Drive Config.  Only 1 primary HD was showing, the rest said N/A.  I just set them to auto and the dual boot menu came up.  When I booted up Windows it did a check disk but booted up fine and so did Ubuntu which I'm using now.

Thanks,


Todd

---

### Post by raymondh on 2009-12-07
Glad you got it working ..... Happy ubuntu-ing :)

---

### Post by endelsisalik on 2010-12-11
> **kize37 said:**
> I just installed Ubuntu with dual booting in XP.  Now I cannot boot.
Grub loading:
Grub Error
No such disk.


i have the same problem and nothing seems to help, i am typing this from another PC…
in BIOS everything is set right.
can somebody guide me step by step, cause, i am allready way too frustated and i am going to smash this damn machine (first time i have a installing problem with ubuntu) soon if i do not get this machine running. thanks.

---

### Post by endelsisalik on 2010-12-11
> **endelsisalik said:**
> ...in BIOS everything is set right...
.
i forgot, i booted from LiveCD also and i got this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x479fa8f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       30402   191770242    f  W95 Ext'd (LBA)
/dev/sda5            6528       14248    62011719    7  HPFS/NTFS
/dev/sda6           14248       21944    61822976   83  Linux
/dev/sda7           21944       22277     2675712   82  Linux swap / Solaris
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found

---

### Post by Rubi1200 on 2010-12-11
Hi and welcome to the forums endelsisalik  :-)  From the LiveCD, post the results of the boot info script linked at the bottom of my post.  Thanks.

---

### Post by pickarooney on 2010-12-11
it's in the first post...

---

### Post by Rubi1200 on 2010-12-11
> **pickarooney said:**
> it's in the first post...
Thanks, but I was responding to the next poster; will edit it now.

---

### Post by endelsisalik on 2010-12-11
> **Rubi1200 said:**
> Hi and welcome to the forums endelsisalik  :-)  From the LiveCD, post the results of the boot info script linked at the bottom of my post.  Thanks.

here its
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,856,316   488,396,799   383,540,484   f W95 Ext d (LBA)
/dev/sda5         104,856,318   371,049,683   266,193,366   7 HPFS/NTFS
/dev/sda6         371,050,496   483,512,319   112,461,824  83 Linux
/dev/sda7         483,514,368   488,396,799     4,882,432  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A4FCA34EFCA31A16                       ntfs       XPSYSTEM                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        36F6E83020289291                       ntfs       PC                            
/dev/sda6        d5469f18-9164-4540-8d2e-4a4cb96b1404   ext4                                     
/dev/sda7        6c7c8293-aeed-4693-a1fa-0caec728c143   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /numproc=2 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set d5469f18-9164-4540-8d2e-4a4cb96b1404
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set d5469f18-9164-4540-8d2e-4a4cb96b1404
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d5469f18-9164-4540-8d2e-4a4cb96b1404
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d5469f18-9164-4540-8d2e-4a4cb96b1404 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d5469f18-9164-4540-8d2e-4a4cb96b1404
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d5469f18-9164-4540-8d2e-4a4cb96b1404 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d5469f18-9164-4540-8d2e-4a4cb96b1404
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d5469f18-9164-4540-8d2e-4a4cb96b1404
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a4fca34efca31a16
    drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d5469f18-9164-4540-8d2e-4a4cb96b1404 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6c7c8293-aeed-4693-a1fa-0caec728c143 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 192.3GB: boot/grub/core.img
 213.7GB: boot/grub/grub.cfg
 213.9GB: boot/initrd.img-2.6.35-22-generic
 192.3GB: boot/vmlinuz-2.6.35-22-generic
 213.9GB: initrd.img
 192.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  83 92 2b 1e a5 22 da a8  44 4d 69 4d 83 32 21 2c  |..+.."..DMiM.2!,|
00000010  a8 0e ac 21 65 4a 4d 83  2d 1c ba 9c 11 49 4d 68  |...!eJM.-....IMh|
00000020  60 3d 4d 68 9a 2b a2 4e  43 2d 0e a5 aa 0b 41 43  |`=Mh.+.NC-....AC|
00000030  4d 68 62 4d 8d 51 52 4d  7e 44 4d 83 33 b1 2b 19  |MhbM.QRM~DM.3.+.|
00000040  1d 1e 1b a1 14 44 4d 83  31 1e cf b2 3e 4a 4d 83  |.....DM.1...>JM.|
00000050  6d 4d 83 98 2c 0d a8 a2  68 2d 11 17 10 21 2c 18  |mM..,...h-...!,.|
00000060  b1 2b 21 f0 2d 22 a2 68  2c c6 a2 68 2b 14 21 2b  |.+!.-".h,..h+.!+|
00000070  18 a2 4e 43 88 68 54 2c  22 a2 2b 0e 9f 9f 4d 68  |..NC.hT,".+...Mh|
00000080  64 4a 4d 83 8d 3d 4c 4d  83 4e 43 4d 90 4d 5c 44  |dJM..=LM.NCM.M\D|
00000090  4d 83 8e 52 4d 92 68 29  05 fd 2c 0b 41 43 69 2b  |M..RM.h)..,.ACi+|
000000a0  23 af 2f cb 21 2b 18 a2  68 2b a8 21 29 19 c5 3d  |#./.!+..h+.!)..=|
000000b0  4f 52 31 1d 0b a0 21 68  6b 2b d3 46 2e 15 a4 21  |OR1...!hk+.F...!|
000000c0  2d e5 a0 21 68 6b 2c 10  a2 2b 0e b7 18 3e 4a 4d  |-..!hk,..+...>JM|
000000d0  83 6d 4d 83 95 29 ad 2d  a7 a2 4e 43 88 68 54 2d  |.mM..).-..NC.hT-|
000000e0  d2 a8 a2 4e 43 88 68 2f  18 21 2b a8 21 68 2c 23  |...NC.h/.!+.!h,#|
000000f0  b9 a2 2c a2 4e 43 88 68  54 2c 18 a2 2b 15 ca 21  |..,.NC.hT,..+..!|
00000100  2e a8 a2 2c a2 55 3d 4c  4d 83 4e 43 4d 90 4d 68  |...,.U=LM.NCM.Mh|
00000110  52 4d 2d 11 15 9f 10 af  41 43 4d 68 62 4d 8d 51  |RM-.....ACMhbM.Q|
00000120  52 4d 75 3e 4a 4d 83 6d  4d 83 34 b1 2b 1e 1c b7  |RMu>JM.mM.4.+...|
00000130  14 44 4d 69 4d 83 2e 20  cc 23 b0 44 4d 65 4a 4d  |.DMiM.. .#.DMeJM|
00000140  83 83 2e 22 ef 1c a3 44  4d 69 4d 83 30 24 44 4d  |..."...DMiM.0$DM|
00000150  69 4d 83 2d c4 b0 44 4d  65 4a 4d 83 83 98 29 d9  |iM.-..DMeJM...).|
00000160  17 3d 2d ca 10 3d 4f 69  2f 27 a4 21 2c c2 2d cc  |.=-..=Oi/'.!,.-.|
00000170  a2 2c af a0 21 68 6b 2c  10 0c b2 2c bc 46 8e 2b  |.,..!hk,...,.F.+|
00000180  14 a2 05 46 5e 3d 4f 52  2f c9 a2 4e 43 88 68 2d  |...F^=OR/..NC.h-|
00000190  ec a8 21 2d a4 05 a2 68  2b a2 4e 43 88 68 2c 17  |..!-...h+.NC.h,.|
000001a0  c9 a4 21 2f 1d 17 10 21  2e c6 a2 4e 43 88 68 2b  |..!/...!...NC.h+|
000001b0  14 a2 4e 43 88 68 54 2c  a8 21 2d 18 a2 68 00 fe  |..NC.hT,.!-..h..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 d6 c9 dd 0f 00 fe  |................|
000001d0  ff ff 05 fe ff ff d8 c9  dd 0f 2c 0b b4 06 00 00  |..........,.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

/////////////////////////////////////

```

P.S. if I connect my other drive (win7) later, will it corrupt it and i will be in the same spot again? or it\s not important?

---

### Post by Rubi1200 on 2010-12-11
Thanks for posting the results.

From what I can see, everything looks fairly normal.

When you installed Ubuntu was the other drive (with Windows 7) plugged in?

I would re-check the BIOS settings just to make sure.

Anyway, let's try and sort this out by reinstalling GRUB.

From the LiveCD:
```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

After rebooting and, hopefully, getting into Ubuntu run:
```
sudo update-grub
```

---

### Post by endelsisalik on 2010-12-11
> **Rubi1200 said:**
> Thanks for posting the results.

From what I can see, everything looks fairly normal.

When you installed Ubuntu was the other drive (with Windows 7) plugged in?

I would re-check the BIOS settings just to make sure.

Anyway, let's try and sort this out by reinstalling GRUB.

From the LiveCD:
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```After rebooting and, hopefully, getting into Ubuntu run:
```
sudo update-grub
```

thank y for the answer!
no all my OS-s are installed only that disk in what needed just in case

i got this error> 

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
ubuntu@ubuntu:~$

---

### Post by Rubi1200 on 2010-12-11
Have you rebooted?

Are you able to get into Ubuntu?

---

### Post by endelsisalik on 2010-12-11
> **Rubi1200 said:**
> Have you rebooted?

Are you able to get into Ubuntu?

no, i am in the same situation as i started. i think it is about MBR and that damn FlexNet. how to format MBR in the way that anything old is gone?
and yes i rebooted.

---

### Post by Rubi1200 on 2010-12-11
Hmm, I suspected as much when I saw the message, but I was kind of hoping...

This link has some explanations and possible solutions for the problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

To be honest, I would first try and disable the program causing the problem from within Windows.

Hope this helps.

EDIT: this sounds quite similar to your situation [http://gutsywww.ubuntuforums.org/showthread.php?t=1620377](http://gutsywww.ubuntuforums.org/showthread.php?t=1620377)

---

### Post by endelsisalik on 2010-12-11
> **Rubi1200 said:**
> Hmm, I suspected as much when I saw the message, but I was kind of hoping...

This link has some explanations and possible solutions for the problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

To be honest, I would first try and disable the program causing the problem from within Windows.

Hope this helps.

i have nothing installed in windows what\s related to FlexNet, at least i don\t know, but i can, yes, uninstall everything waht\s there... but i am quite sure it do not resolve the problem

---

### Post by oldfred on 2010-12-11
Someone else had the flexnet issue.

Flexnet in Boot area (DRM "rights"/security)

It is from several companies that want to control their software. I think the post I saw before had installed some demo software from Adobe, but it can be from other companies. It is more of a boot sector virus as it is difficult to remove.

[http://ubuntuforums.org/archive/index.php/t-1605076.html](http://ubuntuforums.org/archive/index.php/t-1605076.html)

[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)

---

### Post by Rubi1200 on 2010-12-11
@ oldfred

Would it not be possible to completely recreate/rewrite the MBR to get rid of this thing?

---

### Post by Rubi1200 on 2010-12-11
> **endelsisalik said:**
> i have nothing installed in windows what\s related to FlexNet, at least i don\t know, but i can, yes, uninstall everything waht\s there... but i am quite sure it do not resolve the problem
So, here is something I don't understand. You have 10.10 installed right?

See here:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)
> **In dual boot installs, after using Windows applications that use the [FlexNet Publisher]("http://en.wikipedia.org/wiki/Flexnet"), as a license manager, such software will overwrite GRUB, effectively breaking the boot process.**  This has been fixed for applications including Adobe Photoshop (CS4),  Dell Datasafe backup, Autocad 2009,Adobe Flash Builder 4,UtraISO. If you  have this problem with a new application, see the bug report to add its  signature to prevent future problems ([441941]("https://bugs.launchpad.net/bugs/441941"))  

---

### Post by oldfred on 2010-12-11
As I understand it, it is the area right after the MBR where grub2 adds part of its boot and that is where a lot of windows software hides serial numbers and things like the flexnet virus. I think booting XP causes it to be recreated so grub2 ends up having to work around it.

---

### Post by Rubi1200 on 2010-12-11
But isn't that exactly the problem here that GRUB is not working it's way around the issue since the user is still having issues despite reinstalling GRUB?

Would creating and using a separate /boot partition resolve the issue here specifically and/or in general?

---

### Post by oldfred on 2010-12-11
Separate /boot partition just moves the /boot from the Ubuntu partition to another partition. It does not change the way grub is installed on the hard drive.

I think this is one reason to like the gpt partition instead of MBR, but you cannot use gpt with windows.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. Make it 128 kiB as recommended in the following link. Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32. You can set bios_grub flag in gparted or with command line:

---

### Post by endelsisalik on 2010-12-11
> **Rubi1200 said:**
> So, here is something I don't understand. You have 10.10 installed right?

See here:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)

yes, it's 10.10 i think – at least i think it's the latest…

---

### Post by endelsisalik on 2010-12-12
> **Rubi1200 said:**
> 
To be honest, I would first try and disable the program causing the problem from within Windows.
[]("http://gutsywww.ubuntuforums.org/showthread.php?t=1620377")

hmmm, i reformated the hole disk... and grub problem is STILL there... so it can't be "software problem". it's probably about mbr or something else... i am out of ideas...

now i am killing all data on the disk with (on epass zeros (1 pass) - [http://www.killdisk.com/](http://www.killdisk.com/)), and i hope that MBR will be also deleted... if not, i can try to format the damn disk under mac to hfs+ and THEN the MBR is certainly gone. and then back to PC and the dance will start again... 
but why i have i weird feeling that even this does not help? 
where is that bug in my system? can it be hardware problem??

---

### Post by drs305 on 2010-12-12
You could also use TestDisk to try to wipe the MBR. I don't know if it will wipe the area that Dell DataSafe, FlexNet, etc write to, but it certainly kills the bootloader part of the MBR.

Install testdisk, then "sudo testdisk /dev/sd**X**"
Verify the drive > Proceed > Intel > MBR Code > Y > Y

You will need to install a new bootloader after accomplishing the above.

Also, how old is your BIOS/motherboard? Your entire Grub boot section is beyond 137GB deep. If you have an older BIOS your system may not 'see' the grub files until after the OS starts running. You can check in BIOS to see if it correctly identifies the full size of your drive.

---

### Post by endelsisalik on 2010-12-12
disk should be formated now and there\s not MBR anymore, something else  instead of MBR what winn7 proposed to me (just to get rid of the mbr).  and new ubuntu has been installed and we are still at the starting point  - grub rescue etc...

i am too confused allready - sda or sda1? sorry, this is allready too much to me.

i just made one disk (no extra partitions etc) and let live cd make the hole disk as the installer wanted.

---

### Post by drs305 on 2010-12-12
Go for broke and just type these two commands. Press ENTER after typing "ls" in the first command and look at the result. If you run the second command and press ENTER, you won't see a menu but in less than a minute it should boot if it's going to work.
```

ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
```

---

### Post by endelsisalik on 2010-12-12
> **drs305 said:**
> Go for broke and just type these two commands. Press ENTER after typing "ls" in the first command and look at the result. If you run the second command and press ENTER, you won't see a menu but in less than a minute it should boot if it's going to work.
```

ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
```

sorry, but where should i write it? - when the error message occures on start up or after i have booted from LiveCD and in the terminal?

---

### Post by endelsisalik on 2010-12-12
> **endelsisalik said:**
> sorry, but where should i write it? - when the error message occures on start up or after i have booted from LiveCD and in the terminal?

ok, after reboot, if the error shows up, any commands do not work> f.e. man, help, ls, whatever...

---

### Post by endelsisalik on 2010-12-12
> **endelsisalik said:**
> disk should be formated now and there\s not MBR anymore, something else  instead of MBR...
now it is GPT

---

### Post by drs305 on 2010-12-12
> **endelsisalik said:**
> sorry, but where should i write it? - when the error message occures on start up or after i have booted from LiveCD and in the terminal?

**[COLOR="Red"]EDIT:[/COLOR]** I wrote the following before or simultaneously with your last post about it being GPT and did not see it. See *oldfred's * comments in the next post.

You would run these commands from the grub prompt. 

But if you are already booted to the LiveCD, I would just purge/reinstall grub following the procedures in the "G2-Chroot" link in my signature line.

To determine which partition to mount in those instructions, run "sudo fdisk -l" (lowercase L). Your Ubuntu partition will be shown as "Linux". It should be either sda1, but it could be sda5.

That will be the partition you mount in the chroot instructions (or in the 'What Should I Try First' section).

---

### Post by oldfred on 2010-12-12
If you changed to gpt from MBR(msdos) that should be fine, but you should add a bios_grub partition so grub has a place for its files. You also still have a MBR for compatiblity with other software to know it is really gpt.

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

I converted one of my 160GB drives to gpt just to see how it works. No problems that I can identify. It just used the bios_grub partition when it installed grub. Some older tools do not identify everything correctly. 
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

