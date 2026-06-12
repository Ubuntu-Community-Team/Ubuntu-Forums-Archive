---
title: "GRUB ignored in multi-boot setup with Windows 7"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by mase83 on 2010-06-19
Hello,

My sister got a new netbook (Samsung N210) and asked me to install Ubuntu 10.04 Netbook Edition on it.
The netbook had already Windows 7 and Phoenix Hyperspace ([www.hyperspace.com]("http://www.hyperspace.com")) installed so a triple-boot
setup was needed.

Installation was easy: I used Windows Disk Management to shrink D-drive (/dev/sda5) from 105GB to 25GB, then booted
Ubuntu Installer from USB stick and instructed it to use largest continuous free space for installation.
I also checked that GRUB will be installed to "(hd0)".

After installation was completed and computer was rebooted, there was no GRUB menu - computer booted
straight into Windows 7. When I booted into Ubuntu using USB stick and ran bootinfoscript, I got the following
output:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 479195136. According to the info 
                       in the boot sector, sda6 has 0 sectors.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128   260,026,367   228,362,240   7 HPFS/NTFS
/dev/sda4         260,028,414   488,392,064   228,363,651   f W95 Ext d (LBA)
/dev/sda5         260,028,416   311,420,927    51,392,512   7 HPFS/NTFS
/dev/sda6         479,195,136   488,392,064     9,196,929  49 Unknown
/dev/sda7         311,422,976   473,233,407   161,810,432  83 Linux
/dev/sda8         473,235,456   479,186,943     5,951,488  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2006 MB, 2006974464 bytes
62 heads, 62 sectors/track, 1019 cylinders, total 3919872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,917,035     3,916,974   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c4b4d040-05af-4c71-8ead-b0d68e04a7ca   ext3                                     
/dev/sda1        9486DB3886DB1996                       ntfs       RECOVERY                      
/dev/sda2        EEF6DC74F6DC3E91                       ntfs       SYSTEM                        
/dev/sda3        FC9ADEBC9ADE729E                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7C60005460001792                       ntfs                                     
/dev/sda6        4B13-E037                              vfat                                     
/dev/sda7        b2eb694d-77f0-4589-918f-fa8300ab8c2e   ext4                                     
/dev/sda8        3c7f5454-c6fb-47d0-96af-7d810f73e90b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        78FA-0990                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda6/grub/grub.cfg: =============================

#
# grub.cfg for a simple text menu.
# In the current architecture, this always just boots hyperspace.
# see normal/main.c
#
set quietmenu=1
set default=0
set timeout=0

menuentry "Hypercore" {
         sethsroot
         psaloader psa0
}

=================== sda6: Location of files loaded by Grub: ===================


    ??GB: grub/core.img
    ??GB: grub/grub.cfg

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set b2eb694d-77f0-4589-918f-fa8300ab8c2e
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set b2eb694d-77f0-4589-918f-fa8300ab8c2e
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b2eb694d-77f0-4589-918f-fa8300ab8c2e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b2eb694d-77f0-4589-918f-fa8300ab8c2e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b2eb694d-77f0-4589-918f-fa8300ab8c2e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b2eb694d-77f0-4589-918f-fa8300ab8c2e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b2eb694d-77f0-4589-918f-fa8300ab8c2e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set b2eb694d-77f0-4589-918f-fa8300ab8c2e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9486db3886db1996
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set eef6dc74f6dc3e91
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=b2eb694d-77f0-4589-918f-fa8300ab8c2e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=3c7f5454-c6fb-47d0-96af-7d810f73e90b none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 181.0GB: boot/grub/core.img
 202.9GB: boot/grub/grub.cfg
 181.0GB: boot/initrd.img-2.6.32-21-generic
 181.0GB: boot/vmlinuz-2.6.32-21-generic
 181.0GB: initrd.img
 181.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  eb 4b 90 6d 6b 64 6f 73  66 73 00 00 02 04 3f 00  |.K.mkdosfs....?.|
00000010  02 00 02 00 10 f8 03 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 00 00 29 37  e0 13 4b 20 20 20 20 20  |......)7..K     |
00000030  20 20 20 20 20 20 46 41  54 31 32 20 20 20 04 00  |      FAT12   ..|
00000040  00 80 00 08 01 f0 8f 1c  00 00 00 00 80 fa eb 07  |................|
00000050  f6 c2 80 75 02 b2 80 ea  5c 7c 00 00 31 c0 8e d8  |...u....\|..1...|
00000060  8e d0 bc 00 20 fb a0 4c  7c 3c ff 74 02 88 c2 52  |.... ..L|<.t...R|
00000070  be 71 7d e8 23 01 be 05  7c f6 c2 80 74 48 b4 41  |.q}.#...|...tH.A|
00000080  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
00000090  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000a0  c7 04 10 00 66 8b 1e 44  7c 66 89 5c 08 66 8b 1e  |....f..D|f.\.f..|
000000b0  48 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |H|f.\..D..p.B..r|
000000c0  05 bb 00 70 eb 73 b4 08  cd 13 73 0a f6 c2 80 0f  |...p.s....s.....|
000000d0  84 f0 00 e9 83 00 66 0f  b6 c6 88 64 ff 40 66 89  |......f....d.@f.|
000000e0  44 04 0f b6 d1 c1 e2 02  88 e8 88 f4 40 89 44 08  |D...........@.D.|
000000f0  0f b6 c2 c0 e8 02 66 89  04 66 a1 48 7c 66 09 c0  |......f..f.H|f..|
00000100  75 4f 66 a1 44 7c 66 31  d2 66 f7 34 88 d1 31 d2  |uOf.D|f1.f.4..1.|
00000110  66 f7 74 04 3b 44 08 7d  38 fe c1 88 c5 30 c0 c1  |f.t.;D.}8....0..|
00000120  e8 02 08 c1 88 d0 5a 88  c6 bb 00 70 8e c3 31 db  |......Z....p..1.|
00000130  b8 01 02 cd 13 72 2a 8c  c3 8e 06 42 7c 60 1e b9  |.....r*....B|`..|
00000140  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 40  |....1.1.....a.&@|
00000150  7c be 77 7d e8 42 00 eb  0e be 7c 7d e8 3a 00 eb  ||.w}.B....|}.:..|
00000160  06 be 86 7d e8 32 00 be  8b 7d e8 2c 00 cd 18 eb  |...}.2...}.,....|
00000170  fe 00 00 00 00 00 00 47  65 6f 6d 00 48 61 72 64  |.......Geom.Hard|
00000180  20 44 69 73 6b 00 52 65  61 64 00 20 45 72 72 6f  | Disk.Read. Erro|
00000190  72 00 bb 01 00 b4 0e cd  10 ac 3c 00 75 f4 c3 00  |r.........<.u...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 24 12  |..............$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 c1 ff  eb 8d 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 b8 01 02 b5  00 b6 00 cd 13 72 d7 b6  |...p.........r..|
000001f0  01 b5 4f e9 e0 fe 00 00  00 00 00 00 00 00 55 aa  |..O...........U.|
00000200

```Note that /dev/sdb is Ubuntu Live USB stick.

Here's a description of each partition:

```

/dev/sda1 - Samsung Recovery Partition
/dev/sda2 - Boot Partition of Windows 7 (just a guess)
/dev/sda3 - C-drive of Windows 7
/dev/sda4 - Extended partition
/dev/sda5 - D-drive of Windows 7
/dev/sda6 - Hyperspace partition
/dev/sda7 - Ubuntu Root Partition (created by installer)
/dev/sda8 - Ubuntu Swap Partition (created by installer)

```I noticed from fdisk output that Ubuntu partitions sda7 and sda8 are located between sda5 and 
sda6 inside extended partition - could this be a problem?

I have spent hours googling for a solution but without success. Here's what I have already tried:

1) I reinstalled GRUB using following commands:

```

# mount /dev/sda7 /mnt
# mount --bind /dev /mnt/dev
# mount --bind /proc /mnt/proc
# mount --bind /sys /mnt/sys
# chroot /mnt
# update-grub
# grub-install /dev/sda
# umount /mnt/dev
# umount /mnt/sys
# umount /mnt/proc
# umount /mnt

```update-grub gave some errors (ls: cannot access /casper-rw-backing: No such file or directory) but I don't
think they are fatal or related to this issue. grub-install succeeded but had no effect on boot - there
was no GRUB menu and computer booted straight into Windows 7.

2) I removed boot flag from /dev/sda2. As expected, boot didn't succeed at all.

3) I set boot flag to /dev/sda7. As expected, boot didn't succeed at all.

Any ideas why GRUB seems to be ignored in boot process?

---

### Post by darkod on 2010-06-19
You don't need chroot for simple grub2 reinstall to the MBR. I'm not sure if it made a difference. From live mode try only:

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and see if it helped.

Otherwise all looks good in the results, I'm confused too.

---

### Post by mase83 on 2010-06-19
> **darkod said:**
> 
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda


Thanks for your reply. I tried this method but unfortunately the result is same and GRUB remains hidden.

---

### Post by darkod on 2010-06-19
> **mase83 said:**
> Thanks for your reply. I tried this method but unfortunately the result is same and GRUB remains hidden.

Sorry to be nitpicking, but did you try these exact commands, and only the two of them?

Because the commands you gave in your first post for example are not the same. So I thought we could try this way, no harm done.

But if you did these exact commands, no need to repeat it.

For example in your commands for grub2 reinstall in your post, there was no --root-directory parameter.

---

### Post by mase83 on 2010-06-19
> **darkod said:**
> Sorry to be nitpicking, but did you try these exact commands, and only the two of them?


The exact commands that I tried after reading your post were:

```

$ sudo -i
# mount /dev/sda7 /mnt
# grub-install --root-directory=/mnt/ /dev/sda

```AFAIK the effect should be same.

It seems that GRUB gets installed properly, but for some reason it is ignored on boot. Is there any method to check if GRUB gets executed?

---

### Post by darkod on 2010-06-19
Unless they made some strange setup where BIOS loads win7 directly, I can't see how it would jump over grub2 on the MBR.

Take a look at the manual and in BIOS for anything along those lines.

---

### Post by oldfred on 2010-06-19
I found on another site this:

HyperSpace is a Linux-based OS which is designed to load quickly but to offer limited facilities. It is incompatible with GRUB (and also with WinBCD). 

It seems that hyperspace takes over.

---

### Post by mase83 on 2010-06-20
> **oldfred said:**
> I found on another site this:

HyperSpace is a Linux-based OS which is designed to load quickly but to offer limited facilities. It is incompatible with GRUB (and also with WinBCD). 

It seems that hyperspace takes over.

Yep, it seems that Hyperspace was causing this problem. I uninstalled it from Windows, booted into Ubuntu with USB stick, updated and reinstalled GRUB (because deletion of Hyperspace partition changed partition layout) and after reboot GRUB appeared.

Actually I suspected earlier that Hyperspace could be the cause. I just couldn't figure out how it could interfere boot process when GRUB is on MBR. I think there must be something special in this netbook's BIOS as darkod suggested.

Anyway, problem is now solved. Thanks to both of you!

---

