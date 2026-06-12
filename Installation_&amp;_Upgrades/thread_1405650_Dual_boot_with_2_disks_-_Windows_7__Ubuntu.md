---
title: "Dual boot with 2 disks - Windows 7 / Ubuntu"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by go29habs on 2010-02-12
I've installed Windows 7 onto one hard drive, and then installed Ubuntu 9.10 onto a second hard drive.  The installations seemed to go fine, and I can boot into Ubuntu from the GRUB menu.  However when I try to boot into Windows from the GRUB menu, I get a message saying  "error:  no such device:  446e94786e946488".

Very grateful for any advice.

---

### Post by raymondh on 2010-02-12
Set the Ubuntu HD as first-to-boot in BIOS.

Did you update GRUB after booting into ubuntu?  If not, boot into Ubuntu and access a terminal and type:

```
sudo update-grub
```

hopefully, that will pick up your win7 install.  Post back error or success :)

Raymond

---

### Post by go29habs on 2010-02-13
I updated the GRUB as you suggested, but the same error still comes up when I try to boot Windows 7.  I also tried switching the hard drive boot order in the BIOS, but when I do this nothing boots at all, there is just a flashing cursor.  Does this mean that I must re-install one or both of the operating systems?  Many thanks.

---

### Post by darkod on 2010-02-13
No, you don't have to reinstall (yet). :)
Look at post #2 here:
[http://ubuntuforums.org/showthread.php?t=1405953](http://ubuntuforums.org/showthread.php?t=1405953)

and post the content of your results.txt here so we can have a better look.

---

### Post by go29habs on 2010-02-13
Here is the RESULTS.TXT file produced by the boot info script.
In the other thread, you mentioned putting it in CODE tags for
easier reading, but I just don't know what that is, sorry.

```

   ============================= Boot Info Summary: ================
   
   => Grub 2 is installed in the MBR of /dev/sda and looks for 
      (UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5)/boot/grub.
   => No boot loader is installed in the MBR of /dev/sdb
   
  sda1: ___________________________________________________________
   
      File system:       ntfs
      Boot sector type:  Windows Vista/7
      Boot sector info:  No errors found in the Boot Parameter Block.
      Operating System:  
      Boot files/dirs:   /bootmgr /Boot/BCD
   
  sda2: ____________________________________________________________
   
      File system:       ntfs
      Boot sector type:  Windows Vista/7
      Boot sector info:  No errors found in the Boot Parameter Block.
      Operating System:  Windows 7
      Boot files/dirs:   /Windows/System32/winload.exe
   
  sdb1: ____________________________________________________________
   
      File system:       Bios Boot Partition
      Boot sector type:  -
      Boot sector info:  
   
  sdb2: ____________________________________________________________
   
      File system:       ext4
      Boot sector type:  -
      Boot sector info:  
      Operating System:  Ubuntu 9.10
      Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
   
  sdb3: ____________________________________________________________
   
      File system:       swap
      Boot sector type:  -
      Boot sector info:  
   
  sdc: _____________________________________________________________
   
      File system:       vfat
      Boot sector type:  Unknown
      Boot sector info:  No errors found in the Boot Parameter Block.
      Operating System:  
      Boot files/dirs:   
   
   
  =========================== Drive/Partition Info: ======================
   
  Drive: sda ___________________ _____________________________________________________
   
  Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
  255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Disk identifier: 0x0619e3a1
   
  Partition  Boot         Start           End          Size  Id System
   
  /dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
  /dev/sda2             206,848 3,907,026,943 3,906,820,096   7 HPFS/NTFS
   
   
  Drive: sdb ___________________ _____________________________________________________
   
  Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
  255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Disk identifier: 0x00000000
   
  Partition  Boot         Start           End          Size  Id System
   
  /dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT
   
   
  GUID Partition Table detected.
   
  Partition           Start           End          Size System
  /dev/sdb1              34         1,987         1,954 Bios Boot Partition
  /dev/sdb2           1,988 3,888,933,628 3,888,931,641 Linux or Data
  /dev/sdb3   3,888,933,629 3,907,029,134    18,095,506 Linux Swap
   
  blkid -c /dev/null: ____________________________________________________________
   
  Device           UUID                                   TYPE       LABEL                         
   
  /dev/sda1        446E94786E946488                       ntfs       System Reserved               
  /dev/sda2        625697B556978905                       ntfs                                     
  /dev/sdb2        327bd90f-0ae2-4eba-bfad-b5ce0cd235e5   ext4                                     
  /dev/sdb3        4c6dc530-75b1-44e5-a3c5-6ce5d4476ec3   swap                                     
  /dev/sdc         2966-7B88                              vfat                                     
   
  ============================ "mount | grep ^/dev  output: ===========================
   
  Device           Mount_Point              Type       Options
   
  /dev/sdb2        /                        ext4       (rw,errors=remount-ro)
  /dev/sdc         /media/2966-7B88         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
   
   
  =========================== sdb2/boot/grub/grub.cfg: ===========================
   
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
  set root=(hd1,2)
  search --no-floppy --fs-uuid --set 327bd90f-0ae2-4eba-bfad-b5ce0cd235e5
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
        set root=(hd1,2)
        search --no-floppy --fs-uuid --set 327bd90f-0ae2-4eba-bfad-b5ce0cd235e5
        linux /boot/vmlinuz-2.6.31-14-generic root=UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5 ro   quiet splash
        initrd      /boot/initrd.img-2.6.31-14-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd1,2)
        search --no-floppy --fs-uuid --set 327bd90f-0ae2-4eba-bfad-b5ce0cd235e5
        linux /boot/vmlinuz-2.6.31-14-generic root=UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5 ro single 
        initrd      /boot/initrd.img-2.6.31-14-generic
  }
  ### END /etc/grub.d/10_linux ###
   
  ### BEGIN /etc/grub.d/20_memtest86+ ###
  menuentry "Memory test (memtest86+)" {
        linux16     /boot/memtest86+.bin
  }
  menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16     /boot/memtest86+.bin console=ttyS0,115200n8
  }
  ### END /etc/grub.d/20_memtest86+ ###
   
  ### BEGIN /etc/grub.d/30_os-prober ###
  menuentry "Windows 7 (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 446e94786e946488
        chainloader +1
  }
  ### END /etc/grub.d/30_os-prober ###
   
  ### BEGIN /etc/grub.d/40_custom ###
  # This file provides an easy way to add custom menu entries.  Simply type the
  # menu entries you want to add after this comment.  Be careful not to change
  # the 'exec tail' line above.
  ### END /etc/grub.d/40_custom ###
   
  =============================== sdb2/etc/fstab: ===============================
   
  # /etc/fstab: static file system information.
  #
  # Use 'blkid -o value -s UUID' to print the universally unique identifier
  # for a device; this may be used with UUID= as a more robust way to name
  # devices that works even if disks are added and removed. See fstab(5).
  #
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc            /proc           proc    defaults        0       0
  # / was on /dev/sdb2 during installation
  UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5 /               ext4    errors=remount-ro 0       1
  # swap was on /dev/sdb3 during installation
  UUID=4c6dc530-75b1-44e5-a3c5-6ce5d4476ec3 none            swap    sw              0       0
  /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
   
  =================== sdb2: Location of files loaded by Grub: ===================
   
   
     2.3GB: boot/grub/core.img
      .2GB: boot/grub/grub.cfg
      .2GB: boot/initrd.img-2.6.31-14-generic
      .1GB: boot/vmlinuz-2.6.31-14-generic
      .2GB: initrd.img
      .1GB: vmlinuz
  =========================== Unknown MBRs/Boot Sectors/etc =======================
   
  Unknown BootLoader  on sdc
   
  00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.<.MSWIN4.1..@ .|
  00000010  02 00 02 00 00 f8 00 01  3f 00 ff 00 00 00 00 00  |........?.......|
  00000020  00 40 3c 00 80 00 29 88  7b 66 29 4e 4f 20 4e 41  |.@<...).{f)NO NA|
  00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
  00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
  00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
  00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
  00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
  00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
  00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
  000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
  000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
  000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
  000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
  000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
  000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
  00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
  00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
  00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
  00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
  00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
  00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
  00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
  00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
  00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
  00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
  000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
  000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
  000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
  000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
  000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
  000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
  00000200
   
   
  =============================== StdErr Messages: ===============================
   
   
  WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


```

---

### Post by oldfred on 2010-02-13
When you are editing your thread the top panel shows editing commands, the # is code tag, do if you highlight/select a section and click on the # it will add code tags around the highlighted section.

Generally with 2 drives I like to have the windows MBR in the windows drive and grub in the Ubuntu drive and set the Ubuntu drive first in BIOS so it can find and let you also boot windows. But you have GPT on your ubuntu drive. GPT is a newer partitioning scheme over the MBR which we have had since the IBM PC came out. GPT is used by Apple and some windows servers and is required for drives over 2TB as MBR has a hard limit of 2TB. Not all tools have been updated for GPT so you do need to be aware. Grub2 & Ubuntu are or can be GPT aware.

I do not have GPT and have found some conflicting info on whether you can just install grub2 to the MBR (GPT has MBR just for compatibility) or if you have to have a small BIOS Boot Partition. You have the BIOS boot partition per the script so I would install grub2 on the GPT drive and set it first in BIOS. Then run an update-grub to find windows on the other drive.
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)

GPT info 
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by go29habs on 2010-02-13
I installed GRUB2 to /dev/sdb1, which is the small BIOS boot partition on my second hard drive.  I ran update-grub and switched the boot order of the hard disks in the BIOS.  The behaviour of the machine did not change.  It will not boot at all from the second drive, and when booting from the first, GRUB will boot Ubuntu but not Windows.  Below is the new RESULTS.TXT file from the boot info script:

 ```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 468124 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #2 for /boot/grub.

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0619e3a1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 3,907,026,943 3,906,820,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34         1,987         1,954 Bios Boot Partition
/dev/sdb2           1,988 3,888,933,628 3,888,931,641 Linux or Data
/dev/sdb3   3,888,933,629 3,907,029,134    18,095,506 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        446E94786E946488                       ntfs       System Reserved               
/dev/sda2        625697B556978905                       ntfs                                     
/dev/sdb2        327bd90f-0ae2-4eba-bfad-b5ce0cd235e5   ext4                                     
/dev/sdb3        4c6dc530-75b1-44e5-a3c5-6ce5d4476ec3   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 327bd90f-0ae2-4eba-bfad-b5ce0cd235e5
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
      set root=(hd1,2)
      search --no-floppy --fs-uuid --set 327bd90f-0ae2-4eba-bfad-b5ce0cd235e5
      linux /boot/vmlinuz-2.6.31-14-generic root=UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5 ro   quiet splash
      initrd      /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      insmod ext2
      set root=(hd1,2)
      search --no-floppy --fs-uuid --set 327bd90f-0ae2-4eba-bfad-b5ce0cd235e5
      linux /boot/vmlinuz-2.6.31-14-generic root=UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5 ro single 
      initrd      /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
      linux16     /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
      linux16     /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
      insmod ntfs
      set root=(hd0,1)
      search --no-floppy --fs-uuid --set 446e94786e946488
      chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=327bd90f-0ae2-4eba-bfad-b5ce0cd235e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=4c6dc530-75b1-44e5-a3c5-6ce5d4476ec3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: initrd.img
    .1GB: vmlinuz
=============================== StdErr Messages: ===============================


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.

  
```

---

### Post by darkod on 2010-02-13
You are NOT supposed to edit grub.cfg manually but as a test, boot ubuntu, open grub.cfg with:

sudo gedit /boot/grub/grub.cfg

find the part with the win7 entry which looks like:

menuentry "Windows 7 (loader) (on /dev/sda1)" {
      insmod ntfs
      set root=(hd0,1)
      search --no-floppy --fs-uuid --set 446e94786e946488
      chainloader +1
}

and put the # symbol at the beginning of the seach line, like this:

menuentry "Windows 7 (loader) (on /dev/sda1)" {
      insmod ntfs
      set root=(hd0,1)
      # search --no-floppy --fs-uuid --set 446e94786e946488
      chainloader +1
}

Then save and close that file. Reboot and see if it will boot win7 like that. DO NOT run update-grub after you made the change.

---

### Post by go29habs on 2010-02-13
I made the change to grub.cfg that you suggested, but when I tried to save the file, a big red banner popped up and I got an error message that read:

"Could not save the file /boot/grub/grub.cfg .  You are trying to save the file on a read-only disk.  Please check that you typed the location correctly and try again."

I don't remember setting any disk as read-only, but I don't really know what I'm doing (obviously).  I do appreciate the advice, and I'd be grateful for any more help.

---

### Post by darkod on 2010-02-13
> **go29habs said:**
> I made the change to grub.cfg that you suggested, but when I tried to save the file, a big red banner popped up and I got an error message that read:

"Could not save the file /boot/grub/grub.cfg .  You are trying to save the file on a read-only disk.  Please check that you typed the location correctly and try again."

I don't remember setting any disk as read-only, but I don't really know what I'm doing (obviously).  I do appreciate the advice, and I'd be grateful for any more help.

No problem, actually there is an easier way to try. Restart the computer and in the grub menu move the option on the windows entry but DON'T hit Enter. Instead press 'e'. That will show you the list of commands that are booting win7, should be the same commands from the win7 entry in grub.cfg. You can move the cursor with the arrows. Delete the line starting with search....
Press Ctrl+X to boot and see whether it will boot win7 correctly. If it does, we will make that change permanent (if I can figure out how coz I haven't done it before). :)

---

### Post by go29habs on 2010-02-13
I deleted that line from the Windows 7 entry as you suggested.  After pressing Ctrl+X to boot, I received the following message:

error:  no such partition

---

### Post by darkod on 2010-02-13
> **go29habs said:**
> I deleted that line from the Windows 7 entry as you suggested.  After pressing Ctrl+X to boot, I received the following message:

error:  no such partition

I found the article how to resolve that but if it didn't boot with the line deleted, it's not the same problem. Sorry, I don't have any other idea what might be the problem. :( As oldfred, I'm also not sure how would GPT affect grub2 and ubuntu as a whole. And whether that is a problem at all.

---

### Post by oldfred on 2010-02-13
If you are willing to test I think you just need to install grub2 to sdb not sdb1. It will use the space in the BIOS boot partition for core.img.


_For GRUB 2 you will need a BIOS Boot Partition in the GPT scheme_

GRUB 2 boot.img will go into the protective MBR (using the first 446 bytes of the MBR).
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.  Thus, you must make a separate "BIOS boot partition" to hold core.img.  Make it 128 kiB as recommended in the following link.  Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32.

---

### Post by meierfra. on 2010-02-13
Grub 2 malfunctions with a mixture of GPT  and MS_DOS partition tables.  But there is an easy fix:

Open /etc/default/grub via

```
gksudo gedit /etc/default/grub
```

and add the line

GRUB_PRELOAD_MODULES="part_msdos"

to the  end of the file. Save the file and update "grub.cfg" via

```
sudo update-grub
```

---

### Post by darkod on 2010-02-13
> **meierfra. said:**
> Grub 2 malfunctions with a mixture of GPT  and MS_DOS partition tables.  But there is an easy fix:

Open /etc/default/grub via

```
gksudo gedit /etc/default/grub
```and add the line

GRUB_PRELOAD_MODULES="part_msdos"

to the  end of the file. Save the file and update "grub.cfg" via

```
sudo update-grub
```

And here comes the cavalry. :popcorn:

---

### Post by go29habs on 2010-02-16
I did as meierfra suggested and now GRUB works perfectly.  I can choose to boot into Windows or Ubuntu at startup and either one works.  Many many thanks meierfra, and to all others who took the time to help.  I'll try to mark this thread as solved if I can figure out how.

---

### Post by meierfra. on 2010-02-17
> now GRUB works perfectly.
Great. Have fun with Windows 7 and Ubuntu

---

