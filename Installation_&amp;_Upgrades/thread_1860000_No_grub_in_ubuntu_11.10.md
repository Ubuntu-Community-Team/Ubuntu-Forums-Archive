---
title: "No grub in ubuntu 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by CyberNeT85 on 2011-10-14
I've reinstalled Windows 7 on my laptop wiping the HD. Then i  reinstalled Ubuntu 11.10 along side it on the same partition, but  everytime i boot, there's no option to boot into Ubuntu. HELP!!
  Alex

---

### Post by shimanotaka on 2011-10-14
I just upgraded and I have a similar problem, that there are no options. It just starts booting 11.10 and then hangs halfway through.

---

### Post by drs305 on 2011-10-14
> **CyberNeT85 said:**
> I've reinstalled Windows 7 on my laptop wiping the HD. Then i  reinstalled Ubuntu 11.10 along side it on the same partition, but  everytime i boot, there's no option to boot into Ubuntu. HELP!!
  Alex

Do you mean there is no option in the Windows bootloader or that you don't get the Grub menu as expected?

You may be able to see the Grub menu by holding down the SHIFT key during boot, although normally in cases like that it should boot Ubuntu and not Windows.

Please boot the Ubuntu LiveCD and download/run the Boot Info Script. Post the contents of RESULTS.txt

It will tell us the status of your boot files and whether you are using Wubi or a full Ubuntu installation. Since you say "same partition" it sounds like a Wubi installation, but the script will tell us.

You can go to the script's download page via the "BIS" link in my signature line.

@ shimanotaka,

Your problem does not sound related. Please start your own thread. You may be able to hold down the SHIFT key to see the menu. If so, try the recovery mode option. But please start your own thread regardless.

---

### Post by CyberNeT85 on 2011-10-14
no, it boots straight into windows, no option to boot into ubuntu. i'll see if i have to hold the shift button and ill run the script now. thanks

---

### Post by CyberNeT85 on 2011-10-14
ok, here are the results...
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
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    49,302,232    49,095,385   7 NTFS / exFAT / HPFS
/dev/sda3          49,303,550   488,396,799   439,093,250   5 Extended
/dev/sda5         480,014,336   488,396,799     8,382,464  82 Linux swap / Solaris
/dev/sda6          49,303,552   471,629,823   422,326,272  83 Linux
/dev/sda7         471,631,872   480,006,143     8,374,272  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0p1   6665-6235                              vfat       
/dev/sda1        0862FE6362FE54C2                       ntfs       System Reserved
/dev/sda2        501C01FB1C01DD3A                       ntfs       
/dev/sda5        de288d63-7ae6-435a-b2ad-4d1151e9dc72   swap       
/dev/sda6        8ca8d84b-5aae-4d8e-afd3-a3f1353ff575   ext4       
/dev/sda7        332fc3a6-398e-43ee-a8ce-c0b21dbe0444   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/6665-6235         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/501C01FB1C01DD3A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/8ca8d84b-5aae-4d8e-afd3-a3f1353ff575 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=8ca8d84b-5aae-4d8e-afd3-a3f1353ff575 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=8ca8d84b-5aae-4d8e-afd3-a3f1353ff575 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8ca8d84b-5aae-4d8e-afd3-a3f1353ff575 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8ca8d84b-5aae-4d8e-afd3-a3f1353ff575 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 8ca8d84b-5aae-4d8e-afd3-a3f1353ff575
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 0862FE6362FE54C2
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8ca8d84b-5aae-4d8e-afd3-a3f1353ff575 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=332fc3a6-398e-43ee-a8ce-c0b21dbe0444 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-12-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  fd cc f1 ee 3a fd 7f ff  ff fe 3f c6 c2 d4 2e a8  |....:.....?.....|
00000010  4f 45 0f cf d9 65 97 98  47 a6 77 7d c7 5e 3f 83  |OE...e..G.w}.^?.|
00000020  31 86 2a 4a 62 26 6b 20  1f 5a 59 4d d1 d8 4f f2  |1.*Jb&k .ZYM..O.|
00000030  c9 3f ea a5 5e 91 25 c5  05 58 67 d1 9d 4b 07 05  |.?..^.%..Xg..K..|
00000040  31 08 90 4e db 4c af 38  b3 06 2e 2b cf e5 cc 4c  |1..N.L.8...+...L|
00000050  ec 81 9b 6c f7 92 ea da  7d 88 ca 2e cc c8 cd f5  |...l....}.......|
00000060  f9 4e 50 f2 c6 a1 fa 68  a6 89 8b a5 de 2d a1 fb  |.NP....h.....-..|
00000070  d5 aa ca 78 a0 4e 1e 06  1e ae 72 6b cb bd 9e d6  |...x.N....rk....|
00000080  07 c4 18 a5 f3 4b 28 e8  bc 70 38 4e 31 e7 7a 21  |.....K(..p8N1.z!|
00000090  be fd 93 a9 0e d1 0b 64  98 82 9a 8a 66 5c 72 70  |.......d....f\rp|
000000a0  5c 64 aa aa aa aa aa aa  aa aa aa aa aa aa aa aa  |\d..............|
000000b0  aa aa aa aa aa aa aa aa  aa aa aa aa aa aa aa aa  |................|
*
00000150  aa aa aa aa 35 20 00 02  31 85 61 0c b4 ac 0c 6c  |....5 ..1.a....l|
00000160  05 4f 1c 4e 4a 60 40 19  9a 00 23 c1 8c 15 16 b9  |.O.NJ`@...#.....|
00000170  43 ff fb e0 60 0e 85 07  f7 72 d1 cb 79 8d f0 7e  |C...`....r..y..~|
00000180  ec 3a ad 69 e7 96 20 95  cb 44 8d e6 57 c2 65 b0  |.:.i.. ..D..W.e.|
00000190  ea 7d 96 36 d0 c4 89 52  a5 ac 42 98 12 52 27 52  |.}.6...R..B..R'R|
000001a0  5e a6 88 60 4b ce f0 0d  30 18 20 02 16 b7 31 d0  |^..`K...0. ...1.|
000001b0  96 96 28 00 fb c7 67 5a  fc 38 c9 02 c1 13 00 fe  |..(...gZ.8......|
000001c0  ff ff 82 fe ff ff 02 20  ac 19 00 e8 7f 00 00 fe  |....... ........|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 30 2c 19 00 00  |...........0,...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2011-10-14
Reviewing your RESULTS.txt, it appears that the MBR still points to Windows rather than your Ubuntu partition. You can fix this by installing Grub, which will rewrite the MBR and add the necessary files to Ubuntu. 

This process will remove the Windows pointer, but the good news is that the Grub files that already exist have located Windows and it should be displayed in the Grub menu.

To install Grub, you will boot the 11.10 LiveCD, mount your Ubuntu partition *with the first command*, run the [s]following 2[/s] *second* command and then reboot. Do NOT include the partition number in the second command.

```

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

---

### Post by CyberNeT85 on 2011-10-14
sorry, noobie here. how do i mount the partition?

---

### Post by drs305 on 2011-10-14
> **CyberNeT85 said:**
> sorry, noobie here. how do i mount the partition?

The mounting is accomplished by the first command:
"sudo mount ..."

---

### Post by CyberNeT85 on 2011-10-14
lol. kk

just cus you sed to mount the partition, THEN issue the 2 commands... thanks!

---

### Post by drs305 on 2011-10-14
> **CyberNeT85 said:**
> lol. kk

just cus you sed to mount the partition, THEN issue the 2 commands... thanks!

I knew exactly what happened as soon as I read your question. It was my error for not being more precise.

---

### Post by pakattak on 2011-10-18
drs305, how can I check to see which sda to mount (sda#)?

thanks!

---

### Post by elzipa on 2011-11-01
I did the procedure you discribed ; however, Every time I boot I have trough Ubunto Grub Menu no mater if I go to windows or Ubunto! 
 
I do have installed EFI in my laptop and Have Mac OS X Win7 and Ubunto...Is it possible to boot Trough the EFI menu in windows without foing to Grub Ubunto?
 
  
 
> **drs305 said:**
> Reviewing your RESULTS.txt, it appears that the MBR still points to Windows rather than your Ubuntu partition. You can fix this by installing Grub, which will rewrite the MBR and add the necessary files to Ubuntu. 
 
This process will remove the Windows pointer, but the good news is that the Grub files that already exist have located Windows and it should be displayed in the Grub menu.
 
To install Grub, you will boot the 11.10 LiveCD, mount your Ubuntu partition *with the first command*, run the [s]following 2[/s] *second* command and then reboot. Do NOT include the partition number in the second command.
 
```

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

---

### Post by drs305 on 2011-11-01
> **elzipa said:**
> I did the procedure you discribed ; however, Every time I boot I have trough Ubunto Grub Menu no mater if I go to windows or Ubunto! 
 
I do have installed EFI in my laptop and Have Mac OS X Win7 and Ubunto...Is it possible to boot Trough the EFI menu in windows without foing to Grub Ubunto?

I have no experience with EFI. It would be best if you opened your own thread. Include "Grub 2" and "EFI" in the title so those who can help will look at your thread.

---

### Post by elzipa on 2011-11-01
Just a question before adventure to open a new thread...

mY Laptop is a Mac with OSX, WIN 7 and Ubuntu 11.10. Can I triple-boot a system using a different suggested way..I am just looking to get rid off rEFIt
and boot computer in a different way... Any suggestions would be appreciated!

---

