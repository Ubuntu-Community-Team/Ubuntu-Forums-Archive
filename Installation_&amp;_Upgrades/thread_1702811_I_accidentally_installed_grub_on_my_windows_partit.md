---
title: "I accidentally installed grub on my windows partition!"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by contrafactus on 2011-03-08
Ok so I've been through a bunch of the threads here and elsewhere about fixing boot issues and I'm not sure if I just can't find the solution to the specific problem I have, or if I'm just not doing things in the right order or what.

I just installed ubuntu on a partition on my laptop that already had a windows 7 partition.  First I had Kubuntu installed, but I decided to just try Ubuntu instead.  I did things the right way when I installed Kubuntu and I could switch between OSes on reboot.  Then when I installed Ubuntu I accidentally put grub on /dev/sda1 instead of /dev/sda.  I didn't even notice for a while because I never felt like I needed to go back to Windows until I felt like playing starcraft 2.  That's when I noticed that when the boot options screen appears and I select Windows, the screen goes black, a cursor flashes in the upper left corner for about a second, then the boot options screen reappears.  

If I boot using my windows 7 cd and go into recovery, get a command prompt and type Bootrec.exe /FixMbr and Bootrec.exe /FixBoot, the options appear to complete successfully, but then when I reboot, I get a permanent flashing cursor.

If I follow that by inserting my parted magic cd and running testdisk and overwriting the mbr, I get back to the first situation where the boot options screen will appear, but the windows boot loader just returns me to the boot options screen.  I can get into ubuntu, at least.

Whenever I run testdisk I can't replace the boot with the backup boot because I'm pretty sure it's identical to the flawed one.

So can you folks help me?  how can I get grub onto /dev/sda and then restore the windows boot loader to /dev/sda1?

---

### Post by Rubi1200 on 2011-03-08
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by contrafactus on 2011-03-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 839899214 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   717,896,654   717,894,607   7 HPFS/NTFS
/dev/sda2         717,896,716   950,331,391   232,434,676   f W95 Ext d (LBA)
/dev/sda5         717,896,718   893,677,967   175,781,250  83 Linux
/dev/sda6         893,679,616   950,331,391    56,651,776  82 Linux swap / Solaris
/dev/sda3         950,331,392   976,766,975    26,435,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CBD60174406640                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        D2A6CADDA6CAC0E9                       ntfs       RECOVERY                      
/dev/sda5        eceee759-e138-4af4-8259-20eb62c604c9   ext4                                     
/dev/sda6        2e7d68d9-a804-4c36-8e1e-4a5001d9650c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set eceee759-e138-4af4-8259-20eb62c604c9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set eceee759-e138-4af4-8259-20eb62c604c9
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eceee759-e138-4af4-8259-20eb62c604c9
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=eceee759-e138-4af4-8259-20eb62c604c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eceee759-e138-4af4-8259-20eb62c604c9
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=eceee759-e138-4af4-8259-20eb62c604c9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eceee759-e138-4af4-8259-20eb62c604c9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eceee759-e138-4af4-8259-20eb62c604c9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cbd60174406640
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2e7d68d9-a804-4c36-8e1e-4a5001d9650c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 430.0GB: boot/grub/core.img
 381.0GB: boot/grub/grub.cfg
 370.4GB: boot/initrd.img-2.6.35-27-generic
 430.1GB: boot/vmlinuz-2.6.35-27-generic
 370.4GB: initrd.img
 430.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  16 fc 86 00 30 61 b0 c3  3d 08 99 60 43 8d c7 1a  |....0a..=..`C...|
00000010  92 64 f6 fd 85 59 fa 32  77 ea b3 e6 00 03 da 79  |.d...Y.2w......y|
00000020  57 f7 a6 16 cf 63 a8 72  4e 4b b8 3e b5 82 cb c0  |W....c.rNK.>....|
00000030  26 44 a8 64 6d 30 5a e9  88 cf d1 6e c3 ed 81 77  |&D.dm0Z....n...w|
00000040  6b 1c e7 4e e1 d2 55 ea  27 56 11 9b 06 8b 0f 7c  |k..N..U.'V.....||
00000050  4f 7e 79 13 58 3c 65 af  a3 16 10 ae 50 f5 d1 f9  |O~y.X<e.....P...|
00000060  97 0f 6e bc d4 d2 30 e4  52 6f 51 10 dc 4e b7 d8  |..n...0.RoQ..N..|
00000070  43 d8 02 70 a9 6e 39 e1  ab 24 82 8d c7 32 67 1c  |C..p.n9..$...2g.|
00000080  c9 6d e2 11 73 08 5e 50  31 6e 43 58 ef 06 0e 42  |.m..s.^P1nCX...B|
00000090  9c 08 21 4e 29 40 fb c1  83 1e 7c 3f f6 c3 a6 ea  |..!N)@....|?....|
000000a0  0c cf 3c c3 24 65 eb 81  d2 11 bc cd b1 52 1d df  |..<.$e.......R..|
000000b0  f6 b3 ff 29 df f7 4d 3e  45 ab 63 87 8b 33 84 56  |...)..M>E.c..3.V|
000000c0  f7 a6 55 cf 5f 5d d0 ba  3e 67 47 b0 26 f4 5c f4  |..U._]..>gG.&.\.|
000000d0  29 c0 01 e2 2a 81 26 eb  38 39 b5 d5 dd c3 cf 03  |)...*.&.89......|
000000e0  c1 6c a1 ea d8 72 12 a9  19 df e4 73 e3 6c 13 f9  |.l...r.....s.l..|
000000f0  bb b6 7a 5d 2a 6b 4e 4c  f8 8e c6 72 36 75 6c 4b  |..z]*kNL...r6ulK|
00000100  bd 3d c2 3b 5a 5d a7 0a  9c 86 78 b9 bc df 95 b1  |.=.;Z]....x.....|
00000110  e0 51 19 3b 71 e9 9c 27  96 f2 70 33 32 7a 77 95  |.Q.;q..'..p32zw.|
00000120  aa 4f 64 3d 0f 88 80 83  88 74 0a 3c 80 cf 3c f2  |.Od=.....t.<..<.|
00000130  4c 53 71 b3 4d 40 0d 6c  39 61 15 3f 5f 32 cd 38  |LSq.M@.l9a.?_2.8|
00000140  1e 1e b2 67 2d d9 ee ce  01 fb 8f 2e 32 1e 25 ef  |...g-.......2.%.|
00000150  07 6c f4 29 d0 f8 03 9e  1f 6d fc 10 66 f7 da 14  |.l.).....m..f...|
00000160  8e 9c 41 8f 80 18 10 0b  45 5d ee b7 a7 be 70 8a  |..A.....E]....p.|
00000170  cc e6 05 92 93 f2 4c 93  2f 6a 63 68 d1 e4 6b de  |......L./jch..k.|
00000180  b1 c8 6c fd 16 21 9c c3  99 43 92 72 c2 17 ad 5f  |..l..!...C.r..._|
00000190  3b 1c 06 ad 33 a0 d6 8d  08 ba 4a e9 90 51 67 8a  |;...3.....J..Qg.|
000001a0  3f 85 24 2b 27 39 64 c7  96 4c 79 67 bc a8 cf 58  |?.$+'9d..Lyg...X|
000001b0  a9 0d b0 33 c7 3a 98 f8  72 13 16 13 82 87 00 fe  |...3.:..r.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 82 35 7a 0a 00 fe  |...........5z...|
000001d0  ff ff 05 fe ff ff 84 35  7a 0a 70 76 60 03 00 00  |.......5z.pv`...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

TIA for your help!

---

### Post by YesWeCan on 2011-03-08
Have you visited a Windows forum?
I wouldn't try using linux tools to get your Windows install fixed. Use Windows tools.

Then start over again with Ubuntu. BTW you can avoid these Grub problems by adding Ubuntu to your Windows bootloader menu. You need to install EasyBCD (free) in Windows and when you install Ubuntu, install Grub in the Ubuntu partition not the MBR.

---

### Post by Rubi1200 on 2011-03-08
I can only assume whatever happened with sda3 is a result of messing around with various tools?

As you already knew, GRUB was installed to the boot sector of sda1.

Here is what you can try and do:

1. restore the Windows boot sector; fixmbr and fixboot need only be run once. The startup repair may need to be run 3 times before it works.

First try that and see where it gets you.

2. if the above does not work, try installing a basic Windows-like bootloader called lilo.
This can be done from the LiveCD:

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Ignore warnings, we just want lilo in the MBR.

If this gets you booting Windows again, we can reinstall GRUB properly.

By the way, I respectfully disagree with the assessment of the situation posted by YesWeCan. There is no need, at this stage, to redo everything. We are not out of options yet. And, since you are booting Ubuntu, I see no reason why we should not offer help with booting Windows.

---

### Post by contrafactus on 2011-03-08
I don't know if this is progress at all or not.  At least sda1's boot info looks more accurate.  Only problem is now I just get a permanent cursor flashing on boot up and nothing else.  

It looks like all I need to do is get grub back into the MBR of /dev/sda.  Am I right?  And how do you do that?

Oh, and I believe sda3 is a windows recovery partition...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   717,896,654   717,894,607   7 HPFS/NTFS
/dev/sda2         717,896,716   950,331,391   232,434,676   f W95 Ext d (LBA)
/dev/sda5         717,896,718   893,677,967   175,781,250  83 Linux
/dev/sda6         893,679,616   950,331,391    56,651,776  82 Linux swap / Solaris
/dev/sda3         950,331,392   976,766,975    26,435,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CBD60174406640                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        D2A6CADDA6CAC0E9                       ntfs       RECOVERY                      
/dev/sda5        c41b157b-7782-4117-b7f6-178dd749cbaa   ext4                                     
/dev/sda6        2e7d68d9-a804-4c36-8e1e-4a5001d9650c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c41b157b-7782-4117-b7f6-178dd749cbaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c41b157b-7782-4117-b7f6-178dd749cbaa
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c41b157b-7782-4117-b7f6-178dd749cbaa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c41b157b-7782-4117-b7f6-178dd749cbaa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c41b157b-7782-4117-b7f6-178dd749cbaa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c41b157b-7782-4117-b7f6-178dd749cbaa ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c41b157b-7782-4117-b7f6-178dd749cbaa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c41b157b-7782-4117-b7f6-178dd749cbaa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cbd60174406640
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c41b157b-7782-4117-b7f6-178dd749cbaa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2e7d68d9-a804-4c36-8e1e-4a5001d9650c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 408.5GB: boot/grub/core.img
 384.8GB: boot/grub/grub.cfg
 368.5GB: boot/initrd.img-2.6.35-22-generic
 408.5GB: boot/vmlinuz-2.6.35-22-generic
 368.5GB: initrd.img
 408.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  16 fc 86 00 30 61 b0 c3  3d 08 99 60 43 8d c7 1a  |....0a..=..`C...|
00000010  92 64 f6 fd 85 59 fa 32  77 ea b3 e6 00 03 da 79  |.d...Y.2w......y|
00000020  57 f7 a6 16 cf 63 a8 72  4e 4b b8 3e b5 82 cb c0  |W....c.rNK.>....|
00000030  26 44 a8 64 6d 30 5a e9  88 cf d1 6e c3 ed 81 77  |&D.dm0Z....n...w|
00000040  6b 1c e7 4e e1 d2 55 ea  27 56 11 9b 06 8b 0f 7c  |k..N..U.'V.....||
00000050  4f 7e 79 13 58 3c 65 af  a3 16 10 ae 50 f5 d1 f9  |O~y.X<e.....P...|
00000060  97 0f 6e bc d4 d2 30 e4  52 6f 51 10 dc 4e b7 d8  |..n...0.RoQ..N..|
00000070  43 d8 02 70 a9 6e 39 e1  ab 24 82 8d c7 32 67 1c  |C..p.n9..$...2g.|
00000080  c9 6d e2 11 73 08 5e 50  31 6e 43 58 ef 06 0e 42  |.m..s.^P1nCX...B|
00000090  9c 08 21 4e 29 40 fb c1  83 1e 7c 3f f6 c3 a6 ea  |..!N)@....|?....|
000000a0  0c cf 3c c3 24 65 eb 81  d2 11 bc cd b1 52 1d df  |..<.$e.......R..|
000000b0  f6 b3 ff 29 df f7 4d 3e  45 ab 63 87 8b 33 84 56  |...)..M>E.c..3.V|
000000c0  f7 a6 55 cf 5f 5d d0 ba  3e 67 47 b0 26 f4 5c f4  |..U._]..>gG.&.\.|
000000d0  29 c0 01 e2 2a 81 26 eb  38 39 b5 d5 dd c3 cf 03  |)...*.&.89......|
000000e0  c1 6c a1 ea d8 72 12 a9  19 df e4 73 e3 6c 13 f9  |.l...r.....s.l..|
000000f0  bb b6 7a 5d 2a 6b 4e 4c  f8 8e c6 72 36 75 6c 4b  |..z]*kNL...r6ulK|
00000100  bd 3d c2 3b 5a 5d a7 0a  9c 86 78 b9 bc df 95 b1  |.=.;Z]....x.....|
00000110  e0 51 19 3b 71 e9 9c 27  96 f2 70 33 32 7a 77 95  |.Q.;q..'..p32zw.|
00000120  aa 4f 64 3d 0f 88 80 83  88 74 0a 3c 80 cf 3c f2  |.Od=.....t.<..<.|
00000130  4c 53 71 b3 4d 40 0d 6c  39 61 15 3f 5f 32 cd 38  |LSq.M@.l9a.?_2.8|
00000140  1e 1e b2 67 2d d9 ee ce  01 fb 8f 2e 32 1e 25 ef  |...g-.......2.%.|
00000150  07 6c f4 29 d0 f8 03 9e  1f 6d fc 10 66 f7 da 14  |.l.).....m..f...|
00000160  8e 9c 41 8f 80 18 10 0b  45 5d ee b7 a7 be 70 8a  |..A.....E]....p.|
00000170  cc e6 05 92 93 f2 4c 93  2f 6a 63 68 d1 e4 6b de  |......L./jch..k.|
00000180  b1 c8 6c fd 16 21 9c c3  99 43 92 72 c2 17 ad 5f  |..l..!...C.r..._|
00000190  3b 1c 06 ad 33 a0 d6 8d  08 ba 4a e9 90 51 67 8a  |;...3.....J..Qg.|
000001a0  3f 85 24 2b 27 39 64 c7  96 4c 79 67 bc a8 cf 58  |?.$+'9d..Lyg...X|
000001b0  a9 0d b0 33 c7 3a 98 f8  72 13 16 13 82 87 00 fe  |...3.:..r.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 82 35 7a 0a 00 fe  |...........5z...|
000001d0  ff ff 05 fe ff ff 84 35  7a 0a 70 76 60 03 00 00  |.......5z.pv`...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```
THANKS AGAIN!

And as for your last post, Startup Repair only ran once then claimed it couldn't find any more problems.  And lilo didn't seem to do anything.

---

### Post by drs305 on 2011-03-08
You should be able to restore G2 from the LiveCD. It will be installed in the sda MBR and point to sda5 (Ubuntu):

From a LiveCD terminal:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not include the partition number in the second command.

If Windows is not in the Grub2 menu *after* you reboot, run "sudo update-grub".

---

### Post by contrafactus on 2011-03-08
ubuntu@ubuntu:~$ sudo grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory =/mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for =/mnt/boot/grub (is /dev mounted?).


Here's the error I got.  any ideas?

Thanks!

OH!  I added a space.  now it looks like:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.

OK so now I've made a little progress.  Windows' boot loader WAS still listed in the grub boot options menu after boot, but it still wouldn't start.  When I select the windows option, it just goes to the perma-flashing-cursor.  I even went into ubuntu and did the update-grub command.  Any suggestions?  I was just going to go back and see if the windows 7 cd repair options might work.

---

### Post by drs305 on 2011-03-08
> **contrafactus said:**
> OK so now I've made a little progress.  Windows' boot loader WAS still listed in the grub boot options menu after boot, but it still wouldn't start.  When I select the windows option, it just goes to the perma-flashing-cursor.  I even went into ubuntu and did the update-grub command.  Any suggestions?  I was just going to go back and see if the windows 7 cd repair options might work.

I was under the impression you had Windows working and just wanted to get Grub back so you could boot both OS's.

I don't know my way around Windows very well. My recommendation would be to get your Windows installation working - even if you have to do the "lilo" routine again to get back to the Windows bootloader. Fix Windows, then reinstall G2 as described. There aren't many Windows problems you can fix directly from within Linux.

All G2 does with Windows is to transfer control to the Windows loader. If you get it to boot from the Windows loader, it should also work once you change to Grub as long as the boot flag points to your Windows boot partition (Grub doesn't use it but Windows does, and it looks like it is currently correct).

---

### Post by YesWeCan on 2011-03-08
Here's the thing. When you originally accidentally installed Grub to sda1 you corrupted Windows' bootloader.

Grub is not a replacement bootloader for Windows. So Grub just boots the Windows bootloader (just like the Windows bootloader can boot Grub). If it is corrupted it won't work.

So you have to repair the Windows bootloader before you will ever be able to boot Windows. AFAIK you cannot do this with linux tools and that is why I suggest you visit a Windows forum for help.


Once you have restored Windows bootloader you will not be able to boot Ubuntu. This is because you will have removed the Grub-style MBR and replaced it with a standard MBR, which suits Windows bootloader. To be able to boot Ubuntu again you have to reinstall Grub, and you have a choice:

1) You reinstall Grub to the Ubuntu partition sda5 and then you use EasyBCD to add Ubuntu to your Windows boot menu. The MBR will boot the Windows bootloader on sda1 and this will boot Grub on sda5. This is good because Windows updates won't break anything.

2) You reinstall Grub to the MBR and then use update-grub to add Windows to the Grub boot menu. The Grub2 MBR will boot Grub2 bootloader on sda5 and this will boot the Windows bootloader on sda1.

---

### Post by oldfred on 2011-03-08
Boot script did look like everything was corrected, but sometimes the fixes have to be rerun. Did you try running chkdsk as part of the fixes? And you have to run chkdsk until there are no errors as it does not fix everything on one pass.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by Rubi1200 on 2011-03-09
Windows boot sector appears to be normal as do the rest of the results. 

As oldfred suggested, try running chkdsk and see if that resolves the problem with booting into Windows.

---

### Post by contrafactus on 2011-03-09
I know this isn't a windows help forum, so I really appreciate your help.  I ran chkdsk and it took forever, bit it fixed some errors and then I ran bootrec /fixboot and then bootrec /scanos.  After a few seconds scanos completed and said, "windows installations found: 0."

On the previous screen where it searches for installs to be repaired, it was able to identify my windows partition but then scanos couldn't find it.

And of course windows wouldn't boot.  I'm running chkdsk again and it seems to have fixed a couple of errors.  I'll let you know if it changes anything.

Startup repair can't find any problems...but then it might not think there's a windows partition at all.

Might it be possible to install lilo on /dev/sda1?

---

### Post by billbear on 2011-03-09
By design, the last sector of ntfs is a backup of its boot sector, if I were you, I would immediately copy the last sector of /dev/sda1 to its first sector. But now you have done much fixes and I don't know if the last sector still keep unchanged.

---

### Post by billbear on 2011-03-09
if the last sector and the first sector are identical, the last sector may have changed. If they are different, you can try overwrite the first sector with the last. Backup both sector first, of course.

---

### Post by Rubi1200 on 2011-03-09
As oldfred already said, keep running chkdsk until there are no more errors reported and then see where you are holding before trying other things.

---

### Post by oldfred on 2011-03-09
Script showed boot flag on sda1, is it still there. And the boot sector must be a valid NTFS.

As billbear discussed Windows keeps a backup. Testdisk has a function to restore the boot sector (BS) or rebuild it. Windows fixboot should also work.

Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.

---

### Post by contrafactus on 2011-03-09
Nothing has worked yet.  The backup boot sector was identical to the main boot sector.  Rebuilding (bcd in windows, boot sector in linux) doesn't work . . . 

When I get home today I'm going to try restoring the MFT with testdisk.  If that doesn't work, I may be out of luck.  Seriously, is there any way to use lilo to generate a boot sector for my windows partition?  Anything else at all to try?

Or do I need to get some commercial recovery software?  Or just scrap both installs and start over?  I could get all my data off the machine if I had to.

What really makes it seem hopeless is that scanos reports that it can't find any windows installations on the hard drive at all . . . 

Thanks for all your suggestions.

EDIT: And I ran chkdsk til it found no errors, too . . .

---

### Post by Rubi1200 on 2011-03-09
Wait for oldfred to respond, but in any event backup your data now.

---

### Post by oldfred on 2011-03-09
Lilo is just another boot loader like windows or grub, it just happens to use the boot flag to jump to lilo code in the partition boot sector like windows boot loader. It will not fix a windows BS.

Windows tools should work. But if you ran the auto repair only once, then it may not have fixed everything. The auto repair has to be run 3 times and even then may not always work. Did you run the command line windows repairs?

---

### Post by contrafactus on 2011-03-09
You mean the windows startup repair?  It didn't take long for startup repair to say that it cannot detect any problems.  So it does nothing.  I think it might be for the same reason that scanos says it can't find any windows installations.  If the MFT thing doesn't work, I'm gonna try just reinstalling windows on that partition.

Think that'll work? :-k

Thanks for your help.

---

### Post by oldfred on 2011-03-09
Often the auto repair does not work. You have to use the commands from the command line.

See post #11.

---

### Post by contrafactus on 2011-03-09
I've followed tons of guides.  I've done absolutely everything mentioned in this thread.  My windows disk doesn't seem to have bootsect.

It's not too bad, it's a pretty new installation of windows anyway.  Just have to reinstall a few programs after I backup and reinstall windows.

I wish I could get rid of windows entirely, but after I burned an entire weekend getting starcraft 2 installed under WINE on ubuntu, I read (and confirmed) that ATI video cards just don't play nice enough with Linux to run SC2 very efficiently, even at ridiculously low settings.  nVidia cards work pretty well, apparently, but it looked awful AND ran slowly through WINE.  Installing SC2 taught me a good bit about linux, tho.

And installing linux incorrectly has taught me a good bit about boot records and sectors and MFT's, etc.

I guess this thread almost deserves a new tag, [UNSOLVABLE]

But if backing up all my data and re-installing win7 to that partition works I'll mark this [SOLVED]

---

### Post by billbear on 2011-03-09
You can try using grub4dos to bypass the boot sector code of ntfs.
download [http://nufans.net/grub4dos/current_release/grub4dos-0.4.4-2009-10-16.zip](http://nufans.net/grub4dos/current_release/grub4dos-0.4.4-2009-10-16.zip)
unzip it, you only need one file: grub.exe, copy it somewhere, say /boot
edit /etc/grub.d/40_custom, add 
menuentry "Grub4Dos" {
set root='the partition you put grub.exe to'
linux /path/to/grub.exe
}

then 
sudo update-grub

reboot to grub4dos
and type 
chainloader (hd0,0)/bootmgr
boot

to see what happens.
if you can enter windows, create a file menu.lst under C:\ and write into the file:

default 0
timeout 0
title Windows
chainloader (hd0,0)/bootmgr

---

### Post by contrafactus on 2011-03-10
I'd like to give your suggestion a try, but I'm not sure I know exactly what to do . . . where it says 'the partition you put grub.exe to' . . . I'm on my linux partition which is /dev/sda5 . . . so do I type /dev/sda5 for that line?  I don't want to do this incorrectly and somehow not be able to boot at all.

And then for the next line, I copied grub.exe to /boot . . . so all I have to put there is /boot/grub.exe  ??

Thanks, and thanks to everyone for your suggestions.  If this last suggestion does not work, I'll probably just reinstall windows.

EDIT: OK i went ahead and entered the above in custom_40 and there was a new option in grub, Grub4Dos, but when I chose it, it said, "error, no such disk" or something like that.  What SHOULD I put in there for set  root?

---

### Post by billbear on 2011-03-11
edit /etc/grub.d/40_custom, 
```

menuentry "Grub4Dos" {
    set root='(hd0,msdos5)'
    linux /boot/grub.exe
}

```
Any mistakes here will not mess your system up so take it easy :)
Then run "sudo update-grub" again.

Write this down, you will need to type this after booting into grub4dos:
```
chainloader (hd0,0)/bootmgr
boot
```

---

### Post by contrafactus on 2011-03-11
I messed around with setting up Grub4Dos for a little while, but I couldn't get it to boot Windows.  I finally just went with the reinstall.  

I guess I'll type out the steps I took just in case that might help anyone else.  

After all the things in this thread led to errors rather than fixes, I put in the Windows 7 CD, booted from it and selected "install Windows."  The system popped up an error saying that the partition I was trying to install to was corrupted.  So I exited the installation, had to reboot back into the windows CD and run chkdsk.  After that found some errors and fixed them, I tried fixing the boot again, but with no success.

So I once again booted into the Windows 7 CD, chose install, chose which partition to install to, and set up the installation to reformat the partition before installing.  Of course, the windows installation took a long time, and when it was done, Windows had overwritten the mbr and the system did not boot to a grub boot options screen, instead it just started Windows.

So I booted from my Ubuntu Live CD and I followed the "**How to Restore GRUB2 after installing Windows**:" instructions from this page: [http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/) and just in case that page ever goes away:

```
How to Restore GRUB2 after installing Windows:
 
[LIST=1]
[*]Boot from an Ubuntu Live CD or Live USB
[*]Once up and running, Open a Terminal
[*]Type sudo su (press enter after typing each command)
[*]Type fdisk -l Note which device contains your Linux partition (IE: /dev/sda1)
[*]Note which device contains your Linux partition (IE: /dev/sda1)
[*]Type mount /dev/sdx# /mnt (replacing x# with your actual device and partition number)
[*]Type mount --bind /dev /mnt/dev
[*]Type mount --bind /proc /mnt/proc
[*]Type cp /etc/resolv.conf /mnt/etc/resolv.conf
[*]Type chroot /mnt
[*]Type grub-install --recheck /dev/sdx (replacing x with your actual device)
[*]Type reboot (to reboot your PC)
[/LIST]
 Make sure to remove your Live USB or CD. Upon reboot you should be  presented 
with a GRUB2 menu. However, Windows is missing. Now, I show  you how to fix that.
 Making GRUB 2 detect Windows Installs:
 
[LIST=1]
[*]Proceed to boot into your Linux environment.
[*]Open a terminal and type sudo update-grub (enter your root password when prompted)
[/LIST]


```I didn't even have to follow the "**Making GRUB 2 detect Windows Installs**:" instructions at the bottom of the page, because Windows wasn't missing from the boot list.  It just worked after the first 12 steps.

After doing everything in that list, my system rebooted, and loaded the grub boot options screen.  I booted into windows, restarted again and booted into Linux just to make sure that both worked.  They did!

I wish I had been able to fix this problem without reinstalling windows, but at least I got everything working again.  I hope this thread helps some other people.

And thanks to everyone who offered help!

Now it's time to go play some SC2 on my windows partition!  \\:D/

---

