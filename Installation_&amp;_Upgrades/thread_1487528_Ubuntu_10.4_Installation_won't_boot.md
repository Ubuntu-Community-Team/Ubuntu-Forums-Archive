---
title: "Ubuntu 10.4 Installation won't boot"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by scouter on 2010-05-19
Installed ubuntu 10.4 over previous ubuntu on Intel 945G. After installation and reboot the system does not boot: "no bootable device - insert boot disk and press any key".

Installation was done from USB-stick, prepared by UNETBOOTin.  I have two HD's, one used for system + storage, another one just for storage. I manually deleted previous system partitions of previous ubuntu install in system HD.  The system HD had about 1/3 of free and unallocated space for system partitions, which ubuntu installer created during the installation. 

I tried to reinstall grub from bootable USB-stick and it succeeded but it did not help. The system is still not bootable. 

I have used ubuntu for years and never happened something like this. Am I missing something or is ubuntu missing something???:confused:

HW failure is ofcourse possible but I am quite skeptical about it because Live ubuntu from USB-stick works well.

---

### Post by -Jeremy- on 2010-05-19
Perhaps a silly question but are you sure that the new partition you made to replace the old one is flagged as "bootable"?

---

### Post by Catharsis on 2010-05-19
Please use [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and paste the output here with code tags (# in the message toolbar).

---

### Post by scouter on 2010-05-19
> **-Jeremy- said:**
> Perhaps a silly question but are you sure that the new partition you made to replace the old one is flagged as "bootable"?

I haven't check that and I have to do that. But I guess it should have, since ubuntu installer made it automatically. I did not do new partitions manually.

---

### Post by darkod on 2010-05-19
Windows depends on the boot flag to be set on the correct partition, where the boot files are. Ubuntu doesn't need it because it doesn't use it.

However, reinstalling grub2 should have sorted it out. Unless there is another problem you are not aware of.

As suggested, run the boot info script which will show us more details. If you need more detailed instructions how to do that, look here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by scouter on 2010-05-19
Here you go.  Hmm seems like there is something indeed wrong with location of core.img

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 9766912 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34     9,765,659     9,765,626 Linux Swap
/dev/sda2       9,766,912     9,768,959         2,048 Bios Boot Partition
/dev/sda3       9,768,960   197,609,471   187,840,512 Linux or Data
/dev/sda4     197,609,472   205,662,207     8,052,736 Linux Swap
/dev/sda5     205,664,100   693,945,350   488,281,251 Linux or Data
/dev/sda6     693,945,351   976,773,134   282,827,784 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e90fd4d0-053e-4a65-867b-f1bff20bbe9b   swap                                     
/dev/sda3        55f06a8f-1369-42ac-a1ab-788a372be725   ext4                                     
/dev/sda4        586b59b3-053d-4181-8f08-6215192c2e3e   swap                                     
/dev/sda5        364869e3-6b65-44bb-acae-22a7ce4f840f   ext4                                     
/dev/sda6        2cd86920-9c1a-4ddd-8578-ffaf5b413233   ext4                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        4f886024-ce21-4c30-8f98-982390684af4   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         7CB8-727A                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 55f06a8f-1369-42ac-a1ab-788a372be725
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 55f06a8f-1369-42ac-a1ab-788a372be725
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
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 55f06a8f-1369-42ac-a1ab-788a372be725
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=55f06a8f-1369-42ac-a1ab-788a372be725 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 55f06a8f-1369-42ac-a1ab-788a372be725
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=55f06a8f-1369-42ac-a1ab-788a372be725 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 55f06a8f-1369-42ac-a1ab-788a372be725
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 55f06a8f-1369-42ac-a1ab-788a372be725
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=55f06a8f-1369-42ac-a1ab-788a372be725 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=586b59b3-053d-4181-8f08-6215192c2e3e none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  67.4GB: boot/grub/core.img
  43.9GB: boot/grub/grub.cfg
  67.4GB: boot/initrd.img-2.6.32-21-generic
  67.4GB: boot/vmlinuz-2.6.32-21-generic
  67.4GB: initrd.img
  67.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 95 00  00 00 00 00 2f 00 20 08  |............/. .|
00000200


```

---

### Post by scouter on 2010-05-19
I checked that does  /boot/grub/core.img file exist  in /dev/sda3 and it does!

---

### Post by darkod on 2010-05-19
Your disk /dev/sda is a GPT disk, and not the older standard type MBR or DOS partition table. In theory, grub2 supports GPT and should be OK with it. But I haven't worked with GPT and can't guarantee it.

Yes, core.img does exist but grub2 is looking at the wrong place for it. Lets try to reinstall grub2 on /dev/sda. Boot into ubuntu live mode and execute:

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and see if it helped.

---

### Post by scouter on 2010-05-19
> **darkod said:**
> Your disk /dev/sda is a GPT disk, and not the older standard type MBR or DOS partition table. In theory, grub2 supports GPT and should be OK with it. But I haven't worked with GPT and can't guarantee it.

Yes, core.img does exist but grub2 is looking at the wrong place for it. Lets try to reinstall grub2 on /dev/sda. Boot into ubuntu live mode and execute:

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and see if it helped.

Thank you for reply.  Unfortunately this is exactly what I did already previously and I tried again (in case of I made some mistake).  grub-install does something for couple seconds and then prints that it is finished and no errors.

Ubuntu still doesn't boot though. :confused:

Maybe GPT table is corrupted and should be rewritten?

---

### Post by darkod on 2010-05-19
> **scouter said:**
> Thank you for reply.  Unfortunately this is exactly what I did already previously and I tried again (in case of I made some mistake).  grub-install does something for couple seconds and then prints that it is finished and no errors.

Ubuntu still doesn't boot though. :confused:

Maybe GPT table is corrupted and should be rewritten?

I have no idea what to do with GPT, sorry. The disk is only 500GB and GPT started to be used with larger drives. You don't even need to use it, but I'm not sure how easy/difficult it is to change it now to DOS type without losing the data on the partitions.

There are guides on google how to switch GPT to DOS partition table. If you want to do it.

---

### Post by scouter on 2010-05-19
> **darkod said:**
> I have no idea what to do with GPT, sorry. The disk is only 500GB and GPT started to be used with larger drives. You don't even need to use it, but I'm not sure how easy/difficult it is to change it now to DOS type without losing the data on the partitions.

There are guides on google how to switch GPT to DOS partition table. If you want to do it.

All right. I will look for it.

Well the question is why Ubuntu 9.10 worked without problems.

---

### Post by oldfred on 2010-05-19
I am wondering if your BIOS boot partition is too small.

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

would you add GPT to the end of your title. srs5694 is very knowlegeable on GPT and has been very active on GPT issues, but may not look at boot issues.

---

### Post by scouter on 2010-05-19
> **oldfred said:**
> I am wondering if your BIOS boot partition is too small.

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

would you add GPT to the end of your title. srs5694 is very knowlegeable on GPT and has been very active on GPT issues, but may not look at boot issues.

I found also this thread: [http://ubuntuforums.org/showthread.php?t=1480504&highlight=grub+gpt](http://ubuntuforums.org/showthread.php?t=1480504&highlight=grub+gpt) where GPT partitions didn't boot.  Maybe due to incompatibility with motherboard.  

I back upped all the data from my HDs and I created a new DOS type partition table over GPT (deleting all previous partitions). Then I reinstalled Ubuntu 10.4 and everything works.

So indeed it looks like my Intel945G mobo was not compatible with GPT or something was corrupted or badly configured.

All I can say is that Ubuntu 10.4 installer needs some extra work to notice this kind of situations.

---

