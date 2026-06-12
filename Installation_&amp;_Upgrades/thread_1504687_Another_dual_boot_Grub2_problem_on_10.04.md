---
title: "Another dual boot Grub2 problem on 10.04"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by jan3z on 2010-06-08
[FONT=Arial]**Hello! I'm very new to Ubuntu. I've already had WinXP SP3 installed on one HDD, so i've installed 10.04 on my spare HDD. When I try to boot to Win, I get **[B]ntoskrnl.exe missing error. This is my boot info script report:
[/B][/FONT]
```
                                                                     
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   321,669,494   321,669,432   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   482,402,303   482,400,256  83 Linux
/dev/sdc2         482,404,350   488,396,799     5,992,450   5 Extended
/dev/sdc5         482,404,352   488,396,799     5,992,448  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FC4066144065D5C4                       ntfs       Shramba                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A4D48A3FD48A1428                       ntfs       System                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2293f14f-84f9-450d-8f1d-c419bad23657   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        38d221a7-bb5e-40d8-a105-5df709dbc4d1   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
set locale_dir=($root)/boot/grub/locale
set lang=sl
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2293f14f-84f9-450d-8f1d-c419bad23657 ro  vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2293f14f-84f9-450d-8f1d-c419bad23657 ro single  vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2293f14f-84f9-450d-8f1d-c419bad23657 ro  vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2293f14f-84f9-450d-8f1d-c419bad23657 ro single  vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 2293f14f-84f9-450d-8f1d-c419bad23657
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a4d48a3fd48a1428
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2293f14f-84f9-450d-8f1d-c419bad23657 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=38d221a7-bb5e-40d8-a105-5df709dbc4d1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 120.4GB: boot/grub/core.img
 120.4GB: boot/grub/grub.cfg
 120.4GB: boot/initrd.img-2.6.32-21-generic
 120.4GB: boot/initrd.img-2.6.32-22-generic
 120.3GB: boot/vmlinuz-2.6.32-21-generic
 120.4GB: boot/vmlinuz-2.6.32-22-generic
 120.5GB: boot/vmlinuz-2.6.32-22-generic.dpkg-new
 120.4GB: boot/vmlinuz-2.6.32-22-generic.dpkg-tmp
 120.4GB: initrd.img
 120.4GB: initrd.img.old
 120.4GB: vmlinuz
 120.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  3c 26 de 14 bf 06 10 a0  dc 47 45 2f 7a c8 01 c5  |<&.......GE/z...|
00000010  3f 84 53 25 71 53 ce e4  7c f9 20 66 0a e0 d9 1c  |?.S%qS..|. f....|
00000020  66 af 51 f1 d1 90 dd 46  a0 f1 b1 1c e3 24 b8 ef  |f.Q....F.....$..|
00000030  c0 a7 c7 97 68 93 c7 a8  0f 1e 2c 41 2f 33 7f 56  |....h.....,A/3.V|
00000040  1f 5f 33 60 66 a0 24 98  77 71 3d ac 4f 4c c8 61  |._3`f.$.wq=.OL.a|
00000050  71 22 23 ec 2c 69 90 76  c4 42 b0 24 e5 47 4b 35  |q"#.,i.v.B.$.GK5|
00000060  5a 6c 95 52 73 10 7a 44  b3 2b 95 e3 69 c8 36 d2  |Zl.Rs.zD.+..i.6.|
00000070  93 55 5a 70 8f cc 53 35  13 b3 18 87 ac ef 4e 81  |.UZp..S5......N.|
00000080  cb 3b 39 72 54 bd b7 36  e9 48 da a9 8a 74 2d c8  |.;9rT..6.H...t-.|
00000090  b5 90 57 80 0b 77 80 f6  1c 30 e1 df f0 ec 92 40  |..W..w...0.....@|
000000a0  00 03 ff 8f ed 4b 57 a6  16 e2 fa 1e 1e 1e 5d 5d  |.....KW.......]]|
000000b0  18 1a c4 6b 9b 03 48 2d  74 60 6a 03 55 5b 20 b6  |...k..H-t`j.U[ .|
000000c0  f6 da b7 2f d7 3d d5 69  f3 f7 d0 a1 3f a4 a9 f4  |.../.=.i....?...|
000000d0  3f 70 f2 be a5 ed f4 d2  8a fd 73 db 6e 6e 88 7b  |?p........s.nn.{|
000000e0  0d 53 e7 d5 d3 be 4c e9  54 28 70 d3 56 a5 4d a5  |.S....L.T(p.V.M.|
000000f0  75 65 5f 3e 84 fa 27 46  ae c2 55 ad eb 48 6a 5c  |ue_>..'F..U..Hj\|
00000100  c4 4a f6 bd 2e 09 69 bd  ad 21 52 65 e9 95 26 7c  |.J....i..!Re..&||
00000110  a5 f2 b4 af 9f 43 74 d3  98 90 e2 29 be 85 d3 e7  |.....Ct....)....|
00000120  12 13 3f 83 5a 9d 2a cf  df 2d e1 3d 53 dd ef dc  |..?.Z.*..-.=S...|
00000130  5c 72 a6 bc 34 b5 ab f5  4b 85 6e 0b 6b a6 86 85  |\r..4...K.n.k...|
00000140  e4 37 ef d3 25 85 ad f5  27 f6 d5 b9 56 a9 4b f4  |.7..%...'...V.K.|
00000150  97 1d 39 a6 f6 bb e5 7d  aa 87 5e c2 57 ce 6c a1  |..9....}..^.W.l.|
00000160  65 71 fb aa d4 9f 67 ac  fa b4 52 c8 2a 29 b0 86  |eq....g...R.*)..|
00000170  6d 77 2f a1 aa 4c e7 5f  f7 ac e5 fd 13 87 0e 1c  |mw/..L._........|
00000180  38 70 e4 01 05 4e d7 9b  0e 32 93 64 c5 7a 3c 2a  |8p...N...2.d.z<*|
00000190  a1 f1 20 c7 36 13 a1 28  d3 c2 e2 36 3e 98 43 85  |.. .6..(...6>.C.|
000001a0  1b 2f 39 9b 90 38 54 55  78 18 35 de e6 43 48 4d  |./9..8TUx.5..CHM|
000001b0  ec 71 de 5f 59 d8 e9 b8  40 bf 7f 7f 48 1b 00 fe  |.q._Y...@...H...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 5b 00 00 00  |...........p[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```I've tried with different boot orders in bios, reinstalling Grub2 (several times :)), I've even tried to install lilo through software center but didn't know how to configure it :(...

Any ideas how to solve this?

---

### Post by darkod on 2010-06-08
If you set /dev/sdb, the 164GB disk, as first in boot order in BIOS, does XP boot fine?

---

### Post by ronparent on 2010-06-08
Also grub2 is installled to the sdc MBR. I suspect that if you select that as the bood disk in bios that everything will work as intended - including windows.

---

### Post by Mark Phelps on 2010-06-08
I could be wrong, but I don't think changing the physical boot order of the drives is going to fix this -- because the GRUB CFG file has the current physical order encoded into the boot stanzas.

My guess is that booting from drive #3 (Ubuntu drive) is not going to work with the current GRUB CFG file in place.  However, you should be able to do the following:
1) disconnect the other drives
2) insert an Ubuntu LiveCD
3) Boot from that CD
4) Regenerate the GRUB CFG file on the drive using "sudo update-grub"

You should then be able to boot Ubuntu from drive #3 -- with only that drive connected.

Then, reconnect the other drives, but keep booting from drive #3.

Once in Ubuntu, do "sudo update-grub" again, and it will regenerate the GRUB CFG file, now pointing to the new order of the drives.

If you STILL can not boot into MS Windows after that, it's not a GRUB-related problem.

---

### Post by darkod on 2010-06-08
> **Mark Phelps said:**
> 
If you STILL can not boot into MS Windows after that, it's not a GRUB-related problem.

The grub.cfg file is correct. That was my point exactly. Easiest way to see if XP will boot on its own is to boot from /dev/sdb, it has windows bootloader on it and should boot XP directly. If that doesn't work, it's not related to grub2.

No need to disconnect anything or for complicated procedures to try the above.

---

### Post by oldfred on 2010-06-08
Same issue as this thread but I do not know if my recommendation there work as the OP has not come back with anything that worked.

[http://ubuntuforums.org/showthread.php?t=1502267](http://ubuntuforums.org/showthread.php?t=1502267)

Did you change the drive order?
The windows boot.ini says it is rdisk(0), but it is sdb so it should be rdisk(1)? If windows boot ok from sdb then windows puts the drives in a different order than grub. If windows does not boot change the boot.ini entry.

The drivemap command may not be correct. Normally you are mapping to hd0 because window is on sda. Not sure if the drivemap command should be (hd1) ${root}?

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a4d48a3fd48a1428
    drivemap -s (hd0) ${root}
    chainloader +1
}

I have also noticed on my computer when I boot sdc my drive sda is hd1 for chainboot entries, not hd0 even though all the drives remain sda, sdb, sdc. That would mean whether you boot sda, sdb, or sdc the hdx entries would all have to be different.

---

### Post by ronparent on 2010-06-08
I more or less agree with darko. Unless specified otherwise I believe the installer will place the grub mbr on the same disk the OS was installed to. The simplest way to fix that is to use bios to boot from that disk first. All of the other references should fall in place. If for some reason they don't, a simple grub-update will square it away.

---

### Post by darkod on 2010-06-08
> **ronparent said:**
>  Unless specified otherwise I believe the installer will place the grub mbr on the same disk the OS was installed to. 

I still haven't figured it out. I actually think sometimes it puts grub on the disk first in boot order, similar to what windows does.

---

### Post by jan3z on 2010-06-08
> **darkod said:**
> If you set /dev/sdb, the 164GB disk, as first in boot order in BIOS, does XP boot fine?
Yes it does. At first when i installed ubuntu and grub it didn't because drive letters got screwed up. Windows boot partition was on E, but it should have been C. Anyway, I managed to repair that mixup so now booting into Windows works if I set the 164GB drive to the first place in bios.

[QUOTE=ronparent]Also grub2 is installled to the sdc MBR. I suspect that if you select  that as the bood disk in bios that everything will work as intended -  including windows.     [/QUOTE]
This is my current setup and booting into windows results into ntoskrnl.exe missing  error. Ubuntu works fine...

[QUOTE=oldfred]Did you change the drive order?[/QUOTE]
Well, I don't remember everything that i have done... I did play around with drive order when problem first occurred so I'm not sure what was the original state. The thing is I've installed ubuntu with only 250GB drive attached (/dev/sdc) as I didn't want to mess anything on my existing installation. Then i've attached the storage drive (/dev/sda) to see if ubuntu can read ntfs drive by default. After that I've finally attached the windows drive (/dev/sdb/) and installed a GUI manager for grub from software center. All that messed up the drive letters of windows partitions, so I disconnected all other drives except windows and repaired mbr with fixmbr and fixboot which also fixed the drive letter mixup. Finally i've reinstalled grub with Ubuntu LiveCD. Anyway, I also suspect that there is something wrong with drive boot order in config file. I will try the grub-update command ronparent suggested.

---

### Post by darkod on 2010-06-08
I haven't heard of ubuntu mixing up windows letters allocation yet.

With so many plug/unplug, you might check if device.map is correct at all.

sudo grub-mkdevicemap
sudo update-grub

---

### Post by jan3z on 2010-06-08
I've tried the sudo update-grub command but i still get the error. Tomorrow I'll try Mark Phelps's suggestion and will report back on how did it go.

---

### Post by jan3z on 2010-06-08
> **darkod said:**
> I haven't heard of ubuntu mixing up windows letters allocation yet.

With so many plug/unplug, you might check if device.map is correct at all.

sudo grub-mkdevicemap
sudo update-grub

Just tried it and nothing different.

---

