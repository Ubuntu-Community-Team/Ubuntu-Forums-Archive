---
title: "No boot load for ubuntu 10.0.4"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by phampson on 2010-06-16
My pc runs windows xp with two drives 1 x 200gb with windows and 1tb data disk.

I tried to use wubi but that would only acknowledge the 200gb disk drive existed and then when booting said no rootfs was defined.

So I partitioned 40 off the 200gb disk and tried to install off the live cd. This couldnt see the 200gb disk at all. it could only see the 1tb. So I partitioned 60gb off the 1tb and intalled with the live cd to that.

After rebooting the machine booted into Ubuntu and had lost the windows.

So I restored a clonezilla image for the system disk. Now I can boot into windows but cant access the ubuntu install

Does anyone know how I can get windows/boot loader to offer me the chance to boot ubuntu. Ie can I change the boot loader to boot this os.

The disk under linux is /dev/sdb6  It was 10.0.4 LTS

---

### Post by darkod on 2010-06-16
Download the boot info script from my signature, run it and post the content of the results file as explained:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You probably didn't need to do anything you did. Just it depends where the bootloader is and which disk are you booting from.

---

### Post by phampson on 2010-06-17
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/pdc_cadbciifjd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 57. But according to the info from fdisk, 
                       sdb5 starts at sector 4613295.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_cadbciifjd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   398,267,414   398,267,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   2     4,096,001     4,096,000  83 Linux
/dev/sdb2           4,096,002     4,608,001       512,000  82 Linux swap / Solaris
/dev/sdb3           4,613,293 1,953,523,711 1,948,910,419   f W95 Ext d (LBA)
/dev/sdb5           4,613,295 1,827,431,171 1,822,817,877   7 HPFS/NTFS
/dev/sdb6       1,827,432,448 1,948,289,023   120,856,576  83 Linux
/dev/sdb7       1,948,291,072 1,953,523,711     5,232,640  82 Linux swap / Solaris


Drive: pdc_cadbciifjd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cadbciifjd: 203.9 GB, 203928043520 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398296960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cadbciifjd1   *             63   398,267,414   398,267,352   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cadbciifjd1 20FC8BFCFC8BCA8C                       ntfs                                     
/dev/mapper/pdc_cadbciifjd: PTTYPE="dos" 
/dev/sda1        20FC8BFCFC8BCA8C                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        5a87314c-856b-4eb4-810f-e39bb39e6bd7   ext3                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        D210FFEE10FFD805                       ntfs       NEW                           
/dev/sdb6        e8ef383c-0533-4e8d-b3ca-572abfc56165   ext4                                     
/dev/sdb7        2b8ea36f-e26f-4d88-bd59-83ddf09829e5   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set e8ef383c-0533-4e8d-b3ca-572abfc56165
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set e8ef383c-0533-4e8d-b3ca-572abfc56165
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e8ef383c-0533-4e8d-b3ca-572abfc56165
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e8ef383c-0533-4e8d-b3ca-572abfc56165 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e8ef383c-0533-4e8d-b3ca-572abfc56165
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e8ef383c-0533-4e8d-b3ca-572abfc56165 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e8ef383c-0533-4e8d-b3ca-572abfc56165
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e8ef383c-0533-4e8d-b3ca-572abfc56165
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=e8ef383c-0533-4e8d-b3ca-572abfc56165 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=2b8ea36f-e26f-4d88-bd59-83ddf09829e5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 950.8GB: boot/grub/core.img
 978.9GB: boot/grub/grub.cfg
 950.8GB: boot/initrd.img-2.6.32-21-generic
 950.8GB: boot/vmlinuz-2.6.32-21-generic
 950.8GB: initrd.img
 950.8GB: vmlinuz

========================== pdc_cadbciifjd1/boot.ini: ==========================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  94 4e 6a 40 0f 12 8b f9  99 f5 1f a8 36 e5 18 59  |.Nj@........6..Y|
00000010  af 6b 67 20 30 20 83 0f  81 e0 20 7b 62 03 32 0c  |.kg 0 .... {b.2.|
00000020  07 41 05 50 28 01 9a 1e  8f d2 03 0f 19 4e ce 7d  |.A.P(........N.}|
00000030  96 47 62 48 37 ff 83 c1  20 48 12 8b bd cf a7 4e  |.GbH7... H.....N|
00000040  0a 7d 4c 9d 3f e5 8c 0e  87 98 d9 7a 5d cf 48 7c  |.}L.?......z].H||
00000050  53 ef 16 db d6 58 4c d6  34 ca b6 52 a7 b3 12 17  |S....XL.4..R....|
00000060  24 48 d5 56 3f 1e a5 ff  62 84 83 e4 d9 f5 69 f4  |$H.V?...b.....i.|
00000070  44 6b 3a 42 0d d0 78 0f  b8 c1 e0 3f 39 a0 f0 1f  |Dk:B..x....?9...|
00000080  a6 83 02 1d 60 10 1b 57  e0 78 08 1e c1 84 80 53  |....`..W.x.....S|
00000090  81 e0 60 3c 3e fd df 51  de 6f f8 21 83 0e c7 ed  |..`<>..Q.o.!....|
000000a0  75 61 0c 14 69 e5 56 9a  a8 52 3e 11 b0 b9 57 ac  |ua..i.V..R>...W.|
000000b0  0f 5c 50 30 84 0c c7 c1  be 25 95 ee aa 12 8b 83  |.\P0.....%......|
000000c0  d4 a9 50 5b 65 cf 31 86  ff 6f 51 0d 8f 30 36 81  |..P[e.1..oQ..06.|
000000d0  dc 08 43 ee 67 2a 55 7d  8d 35 4d 49 db a4 9c 5b  |..C.g*U}.5MI...[|
000000e0  82 b6 a2 c0 a5 11 b5 86  76 d5 f5 8f fd 86 78 bc  |........v.....x.|
000000f0  52 c2 db f5 af 39 fe cd  cb 16 b9 65 71 a0 5a 83  |R....9.....eq.Z.|
00000100  c0 42 6e 0f 01 fa 8a 60  78 0f d2 41 e0 20 9f 12  |.Bn....`x..A. ..|
00000110  98 08 23 f8 d8 30 21 83  02 12 a1 e0 30 f8 18 0f  |..#..0!.....0...|
00000120  b4 dd 95 38 fd 32 6f 07  c0 cc 03 17 e4 0e f5 50  |...8.2o........P|
00000130  41 1e 66 09 42 4b 36 28  54 10 47 cd e3 7a 57 87  |A.f.BK6(T.G..zW.|
00000140  c5 42 48 f2 8f 19 d8 22  5b 79 78 70 c0 50 84 06  |.BH...."[yxp.P..|
00000150  40 f0 86 9c 78 dc a5 ac  6d 5e e7 3a d5 a0 63 f0  |@...x...m^.:..c.|
00000160  da 9c 5c fa 84 21 df 84  b1 f3 0a fc 56 5b 99 db  |..\..!......V[..|
00000170  d4 5f c9 cd c0 9d 86 69  04 c0 87 e5 6a 9a 1d 02  |._.....i....j...|
00000180  8d 25 08 65 cc 48 d2 a4  f9 f1 c0 1d 1e 60 88 0a  |.%.e.H.......`..|
00000190  61 fe f4 3f 6b 01 e1 60  11 1f c6 fc b4 99 be 84  |a..?k..`........|
000001a0  56 b9 d3 6e 22 ab 21 9d  5a c1 59 77 d2 f0 dc 21  |V..n".!.Z.Yw...!|
000001b0  6c 73 f1 19 28 8c 58 08  60 84 25 d2 f1 f0 00 01  |ls..(.X.`.%.....|
000001c0  41 49 07 f5 f9 ff 02 00  00 00 55 fe a5 6c 00 f5  |AI........U..l..|
000001d0  f9 ff 05 f5 f9 ff 57 fe  a5 6c fc 24 34 07 00 00  |......W..l.$4...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```


Heres the results as requested thanks for your help

---

### Post by darkod on 2010-06-17
```
Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cadbciifjd1 20FC8BFCFC8BCA8C                       ntfs                                     
/dev/mapper/pdc_cadbciifjd: PTTYPE="dos" 
/dev/sda1        20FC8BFCFC8BCA8C                       ntfs                                     
/dev/sda                                                [COLOR=Red]promise_fasttrack_raid_member [/COLOR]                              
/dev/sdb1        5a87314c-856b-4eb4-810f-e39bb39e6bd7   ext3                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        D210FFEE10FFD805                       ntfs       NEW                           
/dev/sdb6        e8ef383c-0533-4e8d-b3ca-572abfc56165   ext4                                     
/dev/sdb7        2b8ea36f-e26f-4d88-bd59-83ddf09829e5   swap                                     
/dev/sdb: PTTYPE="dos"
```The 200GB disk was used in raid earlier and metadata info stayed on it. That's why the ubuntu installer didn't "see" it. You should have asked for help, or googled before deciding to change the plans and install on the 1TB disk. That has an easy fix.

Plus, you don't have grub2 installed at all, so of course ubuntu can't boot.

Boot the ubuntu cd in live mode, and remove the metadata with:

sudo dmraid -r -E /dev/sda

After that install grub2 to the MBR of /dev/sdb with:

sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Restart and in BIOS set to boot from the 1TB disk first. Windows bootloader will remain on /dev/sda.

That should boot ubuntu directly, windows was not recognized because of the raid metadata. Once ubuntu loads, just run:

sudo update-grub

and it should detect windows. I'm not sure what's on /dev/sdb1 and /dev/sdb2, it seems like another ubuntu installation which doesn't work and can't even be properly recognized.

---

### Post by phampson on 2010-06-17
Hi thanks for the reply will try that now

I actually did post regarding wubi not installing. I was told about the raid metadata. But when I checked thru the live cd I couldnt see it so didnt run the command. Hence I changed my plans.

I know grubs isnt installed as it was put onto the 200gb disk which I overwrote with the clonezilla image. Hence this post. 


You live and learn.

Paul

---

### Post by von Stalhein on 2010-06-17
I too have a similar issue.

I can't work out what's happened, but my dual boot won't start XP, after a blinking cursor it just goes to a blank screen.

I did try to make XP the default (my biggest mistake no doubt!!!) but AFAIK the grub.cfg is the same as before.

My results.txt is attached - thanks for any assistance  :redface::

---

### Post by darkod on 2010-06-17
OK, see how it goes.

---

### Post by darkod on 2010-06-17
> **von Stalhein said:**
> I too have a similar issue.

I can't work out what's happened, but my dual boot won't start XP, after a blinking cursor it just goes to a blank screen.

I did try to make XP the default (my biggest mistake no doubt!!!) but AFAIK the grub.cfg is the same as before.

My results.txt is attached - thanks for any assistance  :redface::

Your issue is not the same. Usually it would be better to open your own thread in such case.

Boot the 10.04 cd in live mode, in terminal execute:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

Make the /dev/sdc, 160GB disk, first in BIOS hdd boot order.

You should see your grub2 menu and both ubuntu and XP should work fine as far as I can see.

---

### Post by von Stalhein on 2010-06-17
I apologise for the thread hijack, I will try your suggestion.
Many thanks.

---

### Post by phampson on 2010-06-17
Hi

I booted off the live cd and then got rid of the raid meta data.

Wubi now installs fine. However I couldnt run the second command it said it was too small for the program and said I could force it. I think for now Ill delete it off the 1tb. And try again with the free space on 200gb. It should hopefully install correctly now as it will see 200gb drive.

Thanks for all of your help.

Paul

---

