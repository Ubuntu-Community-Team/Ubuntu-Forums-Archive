---
title: "Ubuntu not booting after upgrade"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by lalala987 on 2010-05-02
Dear all

Inital situation:

I tried to update my 9.10 to 10.04 with the update manager.  there were some error messages during that, the upgrade was not successful and the upgrade was rolled back automatically.. i thought...
Now the new version of GRUB is beeing booted, i can boot windows successfully. if i want to boot ubuntu the screen gets black and after a while all HD-activity stops. i can not boot ubuntu.
I assume the upgrade was not successful, the system is in an undefined state. if i try to (re)install 10.04 i see at the partionion manager screen, that a 10.04 version is already installed. 
Booting with the live-cd works fine. my (old) /home is still there, the files are accessible. 

Question:

What can i do to be able to boot my system?
How can i analyze the error?
Are there any logs (i do think there are some!) and how are they interpreted?

thanks for your help!
Stefan

---

### Post by frantid on 2010-05-02
Please run the bootinfoscript, it will provide the background needed:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by lalala987 on 2010-05-02
> **frantid said:**
> Please run the bootinfoscript, it will provide the background needed:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

hi

i have downloaded the script. as i can not boot into the "broken" system i started with a 10.04 live CD. no i want to copy the bootinfoscript to the /home of my "broken" ubuntu but i get the error "permission denied". is it possible at all to write on a HD with a live-cd booted?

---

### Post by davidmohammed on 2010-05-02
plug in a memory stick and write to that.

---

### Post by frantid on 2010-05-02
> **lalala987 said:**
> hi

i have downloaded the script. as i can not boot into the "broken" system i started with a 10.04 live CD. no i want to copy the bootinfoscript to the /home of my "broken" ubuntu but i get the error "permission denied". is it possible at all to write on a HD with a live-cd booted?

You just have to mount it.  Easiest is go to Places/Computer on the menu and mount the device your /home is on.

---

### Post by lalala987 on 2010-05-02
hurray, got it :)
here are the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

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
    Operating System:  Ubuntu 10.04 LTS
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

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 640.1 GByte, 640135028736 Byte
255 Köpfe, 63 Sektoren/Spur, 77825 Zylinder, zusammen 1250263728 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   808,535,384   808,535,322   7 HPFS/NTFS
/dev/sda2         808,535,385 1,250,258,624   441,723,240   5 Extended
/dev/sda5         808,535,448 1,232,265,824   423,730,377  83 Linux
/dev/sda6       1,232,265,888 1,250,258,624    17,992,737  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Platte /dev/sdb: 640.1 GByte, 640135028736 Byte
255 Köpfe, 63 Sektoren/Spur, 77825 Zylinder, zusammen 1250263728 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Platte /dev/sdc: 1030 MByte, 1030750208 Byte
16 Köpfe, 32 Sektoren/Spur, 3932 Zylinder, zusammen 2013184 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     2,013,183     2,013,152   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A2A427BCA42791B9                       ntfs       cplatte                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6ca5ad71-1f2d-4440-9246-2323fb4e8c89   ext4                                     
/dev/sda6        beaa2fb3-9111-41da-8e49-4d5154dcb7f2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        42A09697A0969151                       ntfs       Daten                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        A28F-C533                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/A28F-C533         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    echo    'Loading Linux 2.6.31-19-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    echo    'Loading Linux 2.6.31-17-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6ca5ad71-1f2d-4440-9246-2323fb4e8c89
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a2a427bca42791b9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
UUID=6ca5ad71-1f2d-4440-9246-2323fb4e8c89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=beaa2fb3-9111-41da-8e49-4d5154dcb7f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 424.0GB: boot/grub/core.img
 414.2GB: boot/grub/grub.cfg
 414.2GB: boot/initrd.img-2.6.31-17-generic-pae
 415.5GB: boot/initrd.img-2.6.31-19-generic-pae
 417.5GB: boot/initrd.img-2.6.31-20-generic-pae
 417.7GB: boot/initrd.img-2.6.31-21-generic-pae
 414.5GB: boot/vmlinuz-2.6.31-17-generic-pae
 415.3GB: boot/vmlinuz-2.6.31-19-generic-pae
 417.6GB: boot/vmlinuz-2.6.31-20-generic-pae
 417.7GB: boot/vmlinuz-2.6.31-21-generic-pae
 416.0GB: boot/vmlinuz-2.6.32-21-generic-pae
 417.7GB: initrd.img
 417.5GB: initrd.img.old
 417.7GB: vmlinuz
 417.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 20 01 00  |.<.DOK01.02.. ..|
00000010  02 00 02 00 00 f8 f6 00  20 00 10 00 20 00 00 00  |........ ... ...|
00000020  e0 b7 1e 00 80 01 29 33  c5 8f a2 00 00 00 00 00  |......)3........|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


```

---

### Post by frantid on 2010-05-02
I don't see any errors there.

next time you boot into grub, highlight the ubuntu entry press e.  Use the arrow keys to get to the end of the kernel line.  delete "quiet splash"  try to boot using crtl-x

watch the screen for errors.

you could also try adding nomodeset to the end of that line to see if that works.  What type of video card do you have?

---

### Post by davidmohammed on 2010-05-02
looks like the default grub entry is trying to boot into the lucid kernel.  Your karmic entry is lower down.

Try pressing shift while booting to display grub and then choosing one of the .31 kernels (i.e. the karmic kernel).

---

### Post by lalala987 on 2010-05-02
@frantid

i do have a PCI-E 2.0 SAPPHIRE Radeon HD 4870, Lite Retail, 1024MB

 i ll try what you wrote...

@davidmohammed

i ll try that too. if i boot an older kernel i get similar results (black screen)

---

### Post by lalala987 on 2010-05-02
i deleted the quiet splash entry and got the output as in the attached camera-screenshots.

[LEFT]i assume the error lies in[SIZE=1] "could not mount because of unsupported optional  features...”[/SIZE]
[/LEFT]

any ideas on that?

---

### Post by davidmohammed on 2010-05-02
did you get the same errors when booting from your older karmic kernels but without the "quiet splash" for these?

---

### Post by frantid on 2010-05-02
> **lalala987 said:**
> i deleted the quiet splash entry and got the output as in the attached camera-screenshots.

[LEFT]i assume the error lies in[SIZE=1] "could not mount because of unsupported optional  features...”[/SIZE]
[/LEFT]

any ideas on that?

it's the fatal errors on the second shot.  you''ve got dependent modules missing from the failed upgrade.  I believe you can chroot to your root dev and run apttitude to try to fix the modules.

I've never done it, here's a thread:
[http://ubuntuforums.org/showthread.php?t=422523](http://ubuntuforums.org/showthread.php?t=422523)

hopefully someone who has done will chime in.

---

### Post by lalala987 on 2010-05-03
> **davidmohammed said:**
> did you get the same errors when booting from your older karmic kernels but without the "quiet splash" for these?

hi

when i select an older kernel, i can boot into a console of my old system. i can not start x-server tough or do any updates. the system seems to be "very broken".

---

### Post by lalala987 on 2010-05-03
> **frantid said:**
> it's the fatal errors on the second shot.  you''ve got dependent modules missing from the failed upgrade.  I believe you can chroot to your root dev and run apttitude to try to fix the modules.

I've never done it, here's a thread:
[http://ubuntuforums.org/showthread.php?t=422523](http://ubuntuforums.org/showthread.php?t=422523)

hopefully someone who has done will chime in.

the above seems very promising, as it should "repair" the failed install. nevertheless i fail at 
" sudo apt-get upgrade "

```

root@ubuntu:/# sudo apt-get upgrade 
sudo: unable to resolve host ubuntu
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Probieren Sie »apt-get -f install«, um dies zu korrigieren.
Die folgenden Pakete haben nicht-erfüllte Abhängigkeiten:
  fglrx-amdcccle: Hängt ab: fglrx ist aber nicht installiert
  xorg-driver-fglrx: Hängt ab: fglrx ist aber nicht installiert
E: Nicht-erfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.
root@ubuntu:/# 

```
some dependencies have not been met.
i am truly clueless now :(
:confused:

---

### Post by lalala987 on 2010-05-04
after getting over the faulty dependency on 'fglrx' by manually installing it i do run now into the following:

```

root@ubuntu:/usr/share# sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
1210 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Schreiben des Protokolls nicht möglich, openpty() schlug fehl (/dev/pts nicht eingehangen?)
Richte shared-mime-info ein (0.71-1ubuntu2) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-mime-database.real: symbol lookup error: update-mime-database.real: undefined symbol: g_malloc0_n
dpkg: Fehler beim Bearbeiten von shared-mime-info (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 127 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgtk2.0-0:
 libgtk2.0-0 hängt ab von shared-mime-info; aber:
  Paket shared-mime-info ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgtk2.0-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libglade2-0:
 libglade2-0 hängt ab von libgtk2.0-0 (>= 2.8.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libglade2-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnomevfs2-common:
 libgnomevfs2-common hängt ab von shared-mime-info; aber:
  Paket shared-mime-info ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgnomevfs2-common (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnomevfs2-0:
 libgnomevfs2-0 hängt ab von libgnomevfs2-common (>= 1:2.24); aber:
  Paket libgnomevfs2-common ist noch nicht konfiguriert.
 libgnomevfs2-0 hängt ab von libgnomevfs2-common (<< 1:2.25); aber:
  Paket libgnomevfs2-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgnomevfs2-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libdbusmenu-gtk1:
 libdbusmenu-gtk1 hängt ab von libgtk2.0-0 (>= 2.16.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libdbusmenu-gtk1 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libindicator0:
 libindicator0 hängt ab von libgtk2.0-0 (>= 2.16.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libindicator0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libappindicator0:
 libappindicator0 hängt ab von libdbusmenu-gtk1 (>= 0.2.5); aber:
  Paket libdbusmenu-gtk1 ist noch nicht konfiguriert.
 libappindicator0 hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 libappindicator0 hängt ab von libindicator0 (>= 0.3.6); aber:
  Paket libindicator0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libappindicator0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von policykit-1-gnome:
 policykit-1-gnome hängt ab von libappindicator0; aber:
  Paket libappindicator0 ist noch nicht konfiguriert.
 policykit-1-gnome hängt ab von libgtk2.0-0 (>= 2.17.1); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von policykit-1-gnome (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gvfs:
 gvfs hängt ab von policykit-1-gnome; aber:
  Paket policykit-1-gnome ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von gvfs (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnome2-0:
 libgnome2-0 hängt ab von libgnomevfs2-0 (>= 1:2.17.90); aber:
  Paket libgnomevfs2-0 ist noch nicht konfiguriert.
 libgnome2-0 hängt ab von gvfs; aber:
  Paket gvfs ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgnome2-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgail18:
 libgail18 hängt ab von libgtk2.0-0 (= 2.20.0-0ubuntu4); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgail18 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnomecanvas2-0:
 libgnomecanvas2-0 hängt ab von libgail18 (>= 1.18.0); aber:
  Paket libgail18 ist noch nicht konfiguriert.
 libgnomecanvas2-0 hängt ab von libglade2-0 (>= 1:2.6.1); aber:
  Paket libglade2-0 ist noch nicht konfiguriert.
 libgnomecanvas2-0 hängt ab von libgtk2.0-0 (>= 2.8.17); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgnomecanvas2-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libbonoboui2-0:
 libbonoboui2-0 hängt ab von libglade2-0 (>= 1:2.6.1); aber:
  Paket libglade2-0 ist noch nicht konfiguriert.
 libbonoboui2-0 hängt ab von libgnome2-0 (>= 2.17.3); aber:
  Paket libgnome2-0 ist noch nicht konfiguriert.
 libbonoboui2-0 hängt ab von libgnomecanvas2-0 (>= 2.11.1); aber:
  Paket libgnomecanvas2-0 ist noch nicht konfiguriert.
 libbonoboui2-0 hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libbonoboui2-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnome-desktop-2-17:
 libgnome-desktop-2-17 hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgnome-desktop-2-17 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von liblaunchpad-integration1:
 liblaunchpad-integration1 hängt ab von libgtk2.0-0 (>= 2.8.2); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von liblaunchpad-integration1 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgucharmap7:
 libgucharmap7 hängt ab von libgtk2.0-0 (>= 2.16.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 libgucharmap7 hängt ab von liblaunchpad-integration1 (>= 0.1.17); aber:
  Paket liblaunchpad-integration1 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgucharmap7 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgweather1:
 libgweather1 hängt ab von libgtk2.0-0 (>= 2.11.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgweather1 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libnotify1:
 libnotify1 hängt ab von libgtk2.0-0 (>= 2.10.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libnotify1 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libpanel-applet2-0:
 libpanel-applet2-0 hängt ab von libbonoboui2-0 (>= 2.15.1); aber:
  Paket libbonoboui2-0 ist noch nicht konfiguriert.
 libpanel-applet2-0 hängt ab von libgtk2.0-0 (>= 2.20.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because the error message indicates its a followup error from a previous failure.dpkg: Fehler beim Bearbeiten von libpanel-applet2-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libwnck22:
 libwnck22 hängt ab von libgtk2.0-0 (>= 2.20.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because the error message indicates its a followup error from a previous failure.dpkg: Fehler beim Bearbeiten von libwnck22 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libnautilus-extension1:
 libnautilus-extension1 hängt ab von libgtk2.0-0 (>= 2.20); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von libnautilus-extension1 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libunique-1.0-0:
 libunique-1.0-0 hängt ab von libgtk2.0-0 (>= 2.12.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libunique-1.0-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
Richte desktop-file-utils ein (0.16-0ubuntu2) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_malloc_n
dpkg: Fehler beim Bearbeiten von desktop-file-utils (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 127 zurück
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von nautilus:
 nautilus hängt ab von libappindicator0; aber:
  Paket libappindicator0 ist noch nicht konfiguriert.
 nautilus hängt ab von libgail18 (>= 1.18.0); aber:
  Paket libgail18 ist noch nicht konfiguriert.
 nautilus hängt ab von libgnome-desktop-2-17 (>= 1:2.29.92); aber:
  Paket libgnome-desktop-2-17 ist noch nicht konfiguriert.
 nautilus hängt ab von libgtk2.0-0 (>= 2.20.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 nautilus hängt ab von liblaunchpad-integration1 (>= 0.1.17); aber:
  Paket liblaunchpad-integration1 ist noch nicht konfiguriert.
 nautilus hängt ab von libnautilus-extension1 (>= 1:2.29.1); aber:
  Paket libnautilus-extension1 ist noch nicht konfiguriert.
 nautilus hängt ab von libunique-1.0-0 (>= 1.0.0); aber:
  Paket libunique-1.0-0 ist noch nicht konfiguriert.
 nautilus hängt ab von shared-mime-info (>= 0.50); aber:
  Paket shared-mime-info ist noch nicht konfiguriert.
 nautilus hängt ab von desktop-file-utils (>= 0.7); aber:
  Paket desktop-file-utils ist noch nicht konfiguriert.
 nautilus hängt ab von gvfs (>= 1.3.2); aber:
  Paket gvfs ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von nautilus (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libcanberra-gtk0:
 libcanberra-gtk0 hängt ab von libgtk2.0-0 (>= 2.14.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von libcanberra-gtk0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnomekbd4:
 libgnomekbd4 hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von libgnomekbd4 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-settings-daemon:
 gnome-settings-daemon hängt ab von libappindicator0 (>= 0.0.19); aber:
  Paket libappindicator0 ist noch nicht konfiguriert.
 gnome-settings-daemon hängt ab von libcanberra-gtk0 (>= 0.2); aber:
  Paket libcanberra-gtk0 ist noch nicht konfiguriert.
 gnome-settings-daemon hängt ab von libgnome-desktop-2-17 (>= 1:2.29.92); aber:
  Paket libgnome-desktop-2-17 ist noch nicht konfiguriert.
 gnome-settings-daemon hängt ab von libgnomekbd4 (>= 2.29.5); aber:
  Paket libgnomekbd4 ist noch nicht konfiguriert.
 gnome-settings-daemon hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 gnome-settings-daemon hängt ab von libnotify1 (>= 0.4.5); aber:
  Paket libnotify1 ist noch nicht konfiguriert.
 gnome-settings-daemon hängt ab von libnotify1-gtk2.10; aber:
  Paket libnotify1-gtk2.10 ist nicht installiert.
  Paket libnotify1, das libnotify1-gtk2.10 bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von gnome-settings-daemon (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-session-bin:
 gnome-session-bin hängt ab von libgtk2.0-0 (>= 2.14.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 gnome-session-bin hängt ab von policykit-1-gnome; aber:
  Paket policykit-1-gnome ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von gnome-session-bin (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von notify-osd:
 notify-osd hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 notify-osd hängt ab von libwnck22 (>= 2.22.0); aber:
  Paket libwnck22 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von notify-osd (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-power-manager:
 gnome-power-manager hängt ab von libappindicator0; aber:
  Paket libappindicator0 ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von libcanberra-gtk0 (>= 0.10); aber:
  Paket libcanberra-gtk0 ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von libnotify1 (>= 0.4.5); aber:
  Paket libnotify1 ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von libnotify1-gtk2.10; aber:
  Paket libnotify1-gtk2.10 ist nicht installiert.
  Paket libnotify1, das libnotify1-gtk2.10 bereitstellt, ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von libpanel-applet2-0 (>= 2.26.0); aber:
  Paket libpanel-applet2-0 ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von libunique-1.0-0 (>= 1.0.0); aber:
  Paket libunique-1.0-0 ist noch nicht konfiguriert.
 gnome-power-manager hängt ab von notification-daemon; aber:
  Paket notification-daemon ist nicht installiert.
  Paket notify-osd, das notification-daemon bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von gnome-power-manager (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached alreadydpkg: Abhängigkeitsprobleme verhindern Konfiguration von libmetacity-private0:
 libmetacity-private0 hängt ab von libcanberra-gtk0 (>= 0.2); aber:
  Paket libcanberra-gtk0 ist noch nicht konfiguriert.
 libmetacity-private0 hängt ab von libgtk2.0-0 (>= 2.10.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.

dpkg: Fehler beim Bearbeiten von libmetacity-private0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached alreadydpkg: Abhängigkeitsprobleme verhindern Konfiguration von zenity:
 zenity hängt ab von libgtk2.0-0 (>= 2.16.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 zenity hängt ab von libnotify1 (>= 0.4.5); aber:
  Paket libnotify1 ist noch nicht konfiguriert.
 zenity hängt ab von libnotify1-gtk2.10; aber:
  Paket libnotify1-gtk2.10 ist nicht installiert.
  Paket libnotify1, das libnotify1-gtk2.10 bereitstellt, ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von zenity (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von metacity:
 metacity hängt ab von libcanberra-gtk0 (>= 0.2); aber:
  Paket libcanberra-gtk0 ist noch nicht konfiguriert.
 metacity hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 metacity hängt ab von libmetacity-private0 (>= 1:2.26.0); aber:
  Paket libmetacity-private0 ist noch nicht konfiguriert.
 metacity hängt ab von zenity; aber:
  Paket zenity ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von metacity (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnome-window-settings1:
 libgnome-window-settings1 hängt ab von libgnome-desktop-2-17 (>= 1:2.29.92); aber:
  Paket libgnome-desktop-2-17 ist noch nicht konfiguriert.
 libgnome-window-settings1 hängt ab von libgtk2.0-0 (>= 2.15.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached alreadydpkg: Fehler beim Bearbeiten von libgnome-window-settings1 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von librsvg2-2:
 librsvg2-2 hängt ab von libgtk2.0-0 (>= 2.16); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von librsvg2-2 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von compiz-plugins:
 compiz-plugins hängt ab von libgtk2.0-0 (>= 2.8.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 compiz-plugins hängt ab von librsvg2-2 (>= 2.26.0); aber:
  Paket librsvg2-2 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von compiz-plugins (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von compiz-gnome:
 compiz-gnome hängt ab von libgnome-desktop-2-17 (>= 1:2.29.92); aber:
  Paket libgnome-desktop-2-17 ist noch nicht konfiguriert.
 compiz-gnome hängt ab von libgnome-window-settings1 (>= 1:2.17.5); aber:
  Paket libgnome-window-settings1 ist noch nicht konfiguriert.
 compiz-gnome hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 compiz-gnome hängt ab von libmetacity-private0 (>= 1:2.26.0); aber:
  Paket libmetacity-private0 ist noch nicht konfiguriert.
 compiz-gnome hängt ab von libwnck22 (>= 2.22.0); aber:
  Paket libwnck22 ist noch nicht konfiguriert.
 compiz-gnome hängt ab von compiz-plugins (= 1:0.8.4-0ubuntu15); aber:
  Paket compiz-plugins ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von compiz-gnome (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libedataserverui1.2-8:
 libedataserverui1.2-8 hängt ab von libglade2-0 (>= 1:2.6.1); aber:
  Paket libglade2-0 ist noch nicht konfiguriert.
 libedataserverui1.2-8 hängt ab von libgtk2.0-0 (>= 2.14.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libedataserverui1.2-8 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von python-gtk2:
 python-gtk2 hängt ab von libgtk2.0-0 (>= 2.19.1); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von python-gtk2 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von python-gmenu:
 python-gmenu hängt ab von python-gtk2; aber:
  Paket python-gtk2 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached alreadydpkg: Fehler beim Bearbeiten von python-gmenu (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-menus:
 gnome-menus hängt ab von python-gmenu (= 2.30.0-0ubuntu4); aber:
  Paket python-gmenu ist noch nicht konfiguriert.
No apport report written because MaxReports is reached alreadydpkg: Fehler beim Bearbeiten von gnome-menus (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgtk2.0-bin:
 libgtk2.0-bin hängt ab von libgtk2.0-0 (>= 2.20.0-0ubuntu4); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
No apport report written because MaxReports is reached alreadydpkg: Fehler beim Bearbeiten von libgtk2.0-bin (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert

No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von librsvg2-common:
 librsvg2-common hängt ab von gtk2.0-binver-2.10.0; aber:
  Paket gtk2.0-binver-2.10.0 ist nicht installiert.
  Paket libgtk2.0-0, das gtk2.0-binver-2.10.0 bereitstellt, ist noch nicht konfiguriert.
 librsvg2-common hängt ab von libgtk2.0-0 (>= 2.16); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 librsvg2-common hängt ab von librsvg2-2 (= 2.26.2-0ubuntu2); aber:
  Paket librsvg2-2 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von librsvg2-common (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-icon-theme:
 gnome-icon-theme hängt ab von libgtk2.0-bin; aber:
  Paket libgtk2.0-bin ist noch nicht konfiguriert.
 gnome-icon-theme hängt ab von librsvg2-common; aber:
  Paket librsvg2-common ist noch nicht konfiguriert.
No apport report written because MaxReports is reached already
dpkg: Fehler beim Bearbeiten von gnome-icon-theme (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
No apport report written because MaxReports is reached already
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-control-center:
 gnome-control-center hängt ab von libappindicator0; aber:
  Paket libappindicator0 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libcanberra-gtk0 (>= 0.2); aber:
  Paket libcanberra-gtk0 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libgnome-desktop-2-17 (>= 1:2.29.92); aber:
  Paket libgnome-desktop-2-17 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libgnome-window-settings1 (= 1:2.30.0-0ubuntu4); aber:
  Paket libgnome-window-settings1 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libgnomekbd4 (>= 2.29.5); aber:
  Paket libgnomekbd4 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libgtk2.0-0 (>= 2.18.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libmetacity-private0 (>= 1:2.26.0); aber:
  Paket libmetacity-private0 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von librsvg2-2 (>= 2.26.0); aber:
  Paket librsvg2-2 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von libunique-1.0-0 (>= 1.0.0); aber:
  Paket libunique-1.0-0 ist noch nicht konfiguriert.
 gnome-control-center hängt ab von gnome-settings-daemon (>= 2.26); aber:
  Paket gnome-settings-daemon ist noch nicht konfiguriert.
 gnome-control-center hängt ab von gnome-menus (>= 2.12.0); aber:
  Paket gnome-menus ist noch nicht konfiguriert.
 gnome-control-center hängt ab von gnome-icon-theme (>= 2.24); aber:
  Paket gnome-icon-theme ist noch nicht konfiguriert.
 gnome-control-center hängt ab von desktop-file-utils; aber:
  Paket desktop-file-utils ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von gnome-control-center (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von python-gnomecanvas:
 python-gnomecanvas hängt ab von libgnomecanvas2-0 (>= 2.11.1); aber:
  Paket libgnomecanvas2-0 ist noch nicht konfiguriert.
 python-gnomecanvas hängt ab von libgtk2.0-0 (>= 2.8.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von python-gnomecanvas (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libgnomeui-0:
 libgnomeui-0 hängt ab von libbonoboui2-0 (>= 2.15.1); aber:
  Paket libbonoboui2-0 ist noch nicht konfiguriert.
 libgnomeui-0 hängt ab von libglade2-0 (>= 1:2.6.1); aber:
  Paket libglade2-0 ist noch nicht konfiguriert.
 libgnomeui-0 hängt ab von libgnome2-0 (>= 2.17.3); aber:
  Paket libgnome2-0 ist noch nicht konfiguriert.
 libgnomeui-0 hängt ab von libgnomecanvas2-0 (>= 2.11.1); aber:
  Paket libgnomecanvas2-0 ist noch nicht konfiguriert.
 libgnomeui-0 hängt ab von libgnomevfs2-0 (>= 1:2.17.90); aber:
  Paket libgnomevfs2-0 ist noch nicht konfiguriert.
 libgnomeui-0 hängt ab von libgtk2.0-0 (>= 2.14); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von libgnomeui-0 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von python-gnome2:
 python-gnome2 hängt ab von python-gnomecanvas; aber:
  Paket python-gnomecanvas ist noch nicht konfiguriert.
 python-gnome2 hängt ab von python-gtk2 (>= 2.10.3); aber:
  Paket python-gtk2 ist noch nicht konfiguriert.
 python-gnome2 hängt ab von python2.6-gnomecanvas; aber:
  Paket python2.6-gnomecanvas ist nicht installiert.
  Paket python-gnomecanvas, das python2.6-gnomecanvas bereitstellt, ist noch nicht konfiguriert.
 python-gnome2 hängt ab von python2.6-gtk2; aber:
  Paket python2.6-gtk2 ist nicht installiert.
  Paket python-gtk2, das python2.6-gtk2 bereitstellt, ist noch nicht konfiguriert.
 python-gnome2 hängt ab von libbonoboui2-0 (>= 2.15.1); aber:
  Paket libbonoboui2-0 ist noch nicht konfiguriert.
 python-gnome2 hängt ab von libgnome2-0 (>= 2.17.3); aber:
  Paket libgnome2-0 ist noch nicht konfiguriert.
 python-gnome2 hängt ab von libgnomecanvas2-0 (>= 2.11.1); aber:
  Paket libgnomecanvas2-0 ist noch nicht konfiguriert.
 python-gnome2 hängt ab von libgnomeui-0 (>= 2.22.0); aber:
  Paket libgnomeui-0 ist noch nicht konfiguriert.
 python-gnome2 hängt ab von libgnomevfs2-0 (>= 1:2.17.90); aber:
  Paket libgnomevfs2-0 ist noch nicht konfiguriert.
 python-gnome2 hängt ab von libgtk2.0-0 (>= 2.8.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von python-gnome2 (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-about:
 gnome-about hängt ab von python-gtk2; aber:
  Paket python-gtk2 ist noch nicht konfiguriert.
 gnome-about hängt ab von python-gnome2; aber:
  Paket python-gnome2 ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von gnome-about (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von gnome-panel:
 gnome-panel hängt ab von libbonoboui2-0 (>= 2.15.1); aber:
  Paket libbonoboui2-0 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libcanberra-gtk0 (>= 0.17); aber:
  Paket libcanberra-gtk0 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libedataserverui1.2-8 (>= 2.28.3.1); aber:
  Paket libedataserverui1.2-8 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libgnome-desktop-2-17 (>= 1:2.29.92); aber:
  Paket libgnome-desktop-2-17 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libgtk2.0-0 (>= 2.20.0); aber:
  Paket libgtk2.0-0 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libgweather1 (>= 2.28.0); aber:
  Paket libgweather1 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libpanel-applet2-0 (>= 2.26.0); aber:
  Paket libpanel-applet2-0 ist noch nicht konfiguriert.
 gnome-panel hängt ab von librsvg2-2 (>= 2.26.0); aber:
  Paket librsvg2-2 ist noch nicht konfiguriert.
 gnome-panel hängt ab von libwnck22 (>= 2.22.0); aber:
  Paket libwnck22 ist noch nicht konfiguriert.
 gnome-panel hängt ab von gnome-control-center (>= 1:2.8.2-3); aber:
  Paket gnome-control-center ist noch nicht konfiguriert.
 gnome-panel hängt ab von gnome-menus (>= 2.16.1); aber:
  Paket gnome-menus ist noch nicht konfiguriert.
 gnome-panel hängt ab von gnome-about (>= 2.10.0-1); aber:
  Paket gnome-about ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von gnome-panel (--configure):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
dpkg: Zu viele Fehler, stoppe hier
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Fehler traten auf beim Bearbeiten von:
 shared-mime-info
 libgtk2.0-0
 libglade2-0
 libgnomevfs2-common
 libgnomevfs2-0
 libdbusmenu-gtk1
 libindicator0
 libappindicator0
 policykit-1-gnome
 gvfs
 libgnome2-0
 libgail18
 libgnomecanvas2-0
 libbonoboui2-0
 libgnome-desktop-2-17
 liblaunchpad-integration1
 libgucharmap7
 libgweather1
 libnotify1
 libpanel-applet2-0
 libwnck22
 libnautilus-extension1
 libunique-1.0-0
 desktop-file-utils
 nautilus
 libcanberra-gtk0
 libgnomekbd4
 gnome-settings-daemon
 gnome-session-bin
 notify-osd
 gnome-power-manager
 libmetacity-private0
 zenity
 metacity
 libgnome-window-settings1
 librsvg2-2
 compiz-plugins
 compiz-gnome
 libedataserverui1.2-8
 python-gtk2
 python-gmenu
 gnome-menus
 libgtk2.0-bin
 librsvg2-common
 gnome-icon-theme
 gnome-control-center
 python-gnomecanvas
 libgnomeui-0
 python-gnome2
 gnome-about
 gnome-panel
Bearbeitung wurde angehalten, da zu viele Fehler auftraten.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/usr/share# 

```

does anyone have any idea on that? 
the errors start with some problems at "shared-mime-info"....

regards

---

### Post by frantid on 2010-05-04
hate to say it, but you might need to think about copying off the data you need and doing a fresh install.

---

