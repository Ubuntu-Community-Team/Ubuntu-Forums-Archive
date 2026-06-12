---
title: "Ubuntu 11.04 beta over openSUSE beside windows"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by SuperDrive on 2011-04-02
Hi there!
Yesterday i tried to install ubuntu 11.04 beta over openSUSE 11.4 but after instalation, grub did not recognize my windows instalation. I tried to add the windows with the startup setup program and with the command sudo update-grub but nothing helped me. I tried to find a user friendly guide to add windows in grub but since im a linux noob, i did not manage it. In some guides i have to add hd0 or hd1 discs and in some guides i found sda, sda1, sdb.... so i dont know which guide is the right for me. The windows auto repair did not worked because the dvd version is not the same as the system (SP1) so i tried to reinstall openSUSE 11.4 over ubuntu and he recognized and added my windows instalation to grub. Is this a beta issue or is it normal that ubuntu can not recognize a windows instalation if there is another linux?

My hdd configuration: raid 0 with two hard drives and two partitions (both ntfs, the first with windows) and one phisical hdd in ext4

---

### Post by Quackers on 2011-04-02
If you booted into the new Ubuntu installation and ran sudo update-grub, and that did not find Windows, then something is wrong.
Please go to System > Admin > Synaptic Package Manager and in the search box enter "os-prober" but without the quotes. When os-prober appears in the main window, does it have a green box to its left? If not, it is not installed. Please install it and then run sudo update-grub again and see if the Windows loader is picked up.
If os-prober was already installed please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by SuperDrive on 2011-04-02
There was an error during the instalation and now grub can not boot ubuntu or windows. The os-prober is installed by default but when i run sudo update-grub in the live system, there is a error /usr/sbin/grub-probe: error: cannot stat `aufs'.  But here is the report and i go reinstall ubuntu:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/mapper/pdc_cfhbhacfej and looks 
    on boot drive #2 in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_cfhbhacfej1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

pdc_cfhbhacfej2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

pdc_cfhbhacfej3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   652,752,025   652,749,978   7 HPFS/NTFS
/dev/sdb2         652,754,944 1,250,258,943   597,504,000   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   304,209,919   304,207,872  83 Linux
/dev/sdc2         304,211,966   312,580,095     8,368,130   5 Extended
/dev/sdc5         304,211,968   312,580,095     8,368,128  82 Linux swap / Solaris


Drive: pdc_cfhbhacfej ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cfhbhacfej: 1280.0 GB, 1280000000000 bytes
255 heads, 63 sectors/track, 155617 cylinders, total 2500000000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cfhbhacfej1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_cfhbhacfej2            206,848 1,310,722,047 1,310,515,200   7 HPFS/NTFS
/dev/mapper/pdc_cfhbhacfej3      1,310,722,048 2,499,997,695 1,189,275,648   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cfhbhacfej1 7C14FF2614FEE1D6                       ntfs       System-reserviert             
/dev/mapper/pdc_cfhbhacfej2 F02C13A52C13663E                       ntfs                                     
/dev/mapper/pdc_cfhbhacfej3 3A08BC0408BBBD67                       ntfs                                     
/dev/mapper/pdc_cfhbhacfej: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        60244e65-24a9-41b7-8858-14a109bd95a5   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        95d6908a-937a-4186-95c2-4b2ba0339cad   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd         15DE-2345                              vfat       PENDRIVE                      
error: /dev/sdb1: No such file or directory
error: /dev/sdb2: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_cfhbhacfej
pdc_cfhbhacfej1
pdc_cfhbhacfej2
pdc_cfhbhacfej3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=60244e65-24a9-41b7-8858-14a109bd95a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=95d6908a-937a-4186-95c2-4b2ba0339cad none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .6GB: boot/initrd.img-2.6.38-7-generic
  96.7GB: boot/vmlinuz-2.6.38-7-generic
    .6GB: initrd.img
  96.7GB: vmlinuz

=========================== sdd/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

==================== sdd: Location of files loaded by Grub: ====================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdd

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 a0 3a 00 33 1d 00 00  00 00 00 00 02 00 00 00  |..:.3...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 45 23 de 15 4e  4f 20 4e 41 4d 45 20 20  |..)E#..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 8a  3a 00 00 66 ba 00 00 00  |..E}.f..:..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
```

---

### Post by Quackers on 2011-04-02
Is your raid 0 setup a bios-set raid? Unfortunately I had to give up on bios raid as I couldn't get it to work (but that may be due to a bios lock on my particular system). I reverted to non-raid and all my OSes now work ok.
Fortunately there are others on here who are better at getting raid 0 to work than I am! I shall have to leave you in their capable hands.

---

### Post by SuperDrive on 2011-04-02
Thanks. Yes, its a bios raid configuration. Now i have reinstalled it and here is what update grub says:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-7-generic
Found initrd image: /boot/initrd.img-2.6.38-7-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

and here again the boot info if there is some diference with the one from live system:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for gi.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       promise_fasttrack_raid_member
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'promise_fasttrack_raid_member'

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'promise_fasttrack_raid_member'
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'promise_fasttrack_raid_member'
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type 'promise_fasttrack_raid_member'
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,310,722,047 1,310,515,200   7 HPFS/NTFS
/dev/sda3       1,310,722,048 2,499,997,695 1,189,275,648   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   652,752,025   652,749,978   7 HPFS/NTFS
/dev/sdb2         652,754,944 1,250,258,943   597,504,000   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   304,209,919   304,207,872  83 Linux
/dev/sdc2         304,211,966   312,580,095     8,368,130   5 Extended
/dev/sdc5         304,211,968   312,580,095     8,368,128  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2                                               promise_fasttrack_raid_member                               
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        95d6908a-937a-4186-95c2-4b2ba0339cad   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sda3: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3
    echo    'Loading Linux 2.6.38-7-generic ...'
    linux    /boot/vmlinuz-2.6.38-7-generic root=UUID=f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=f7e59b7f-0f22-4bf5-8cc2-cba61f1e4ef3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=95d6908a-937a-4186-95c2-4b2ba0339cad none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
 124.9GB: boot/initrd.img-2.6.38-7-generic
  38.7GB: boot/vmlinuz-2.6.38-7-generic
 124.9GB: initrd.img
  38.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  01 88 00 06 01 de 00 0b  01 e3 00 14 01 e5 00 15  |................|
00000010  01 ea 00 17 01 2d 01 18  01 70 01 1b 01 79 01 3f  |.....-...p...y.?|
00000020  01 f1 01 53 01 f7 01 b3  01 00 02 bc 01 02 02 db  |...S............|
00000030  01 0b 02 fd 01 15 02 12  02 58 02 14 02 9b 02 57  |.........X.....W|
00000040  02 de 02 6e 02 21 03 6f  02 26 03 71 02 69 03 03  |...n.!.o.&.q.i..|
00000050  16 2f b8 fc 4d ae 8f e9  df b4 db fc 76 c1 d1 f0  |./..M.......v...|
00000060  df 18 1a a6 a3 7b b2 1a  ee 2b 8b dd be b4 2f 8e  |.....{...+..../.|
00000070  f6 95 c9 70 26 b8 fc 4d  ae 8f e9 f3 6f 9a dc cb  |...p&..M....o...|
00000080  c5 62 32 03 10 c7 f4 39  2c ce d3 cb a0 23 15 0b  |.b2....9,....#..|
00000090  a2 d9 60 a0 9b 0d d7 14  82 8e 44 a2 b4 06 8a e5  |..`.......D.....|
000000a0  64 e2 34 9d 05 22 5a 93  2b eb 31 b8 42 12 9b 49  |d.4.."Z.+.1.B..I|
000000b0  16 08 3a 4c b6 b0 20 99  0b c6 02 dd cb 62 d0 1c  |..:L.. ......b..|
000000c0  fd 86 83 82 e3 78 3d 3d  4f d3 eb 6d 50 33 7c 76  |.....x==O..mP3|v|
000000d0  d7 db 20 b2 eb ed 7a bb  00 00 02 00 00 00 00 00  |.. ...z.........|
000000e0  00 00 00 00 00 03 15 68  3a 1d ae 7b bd ee f7 bb  |.......h:..{....|
000000f0  2b 4c 6e bb d0 f2 17 5c  fe 26 d7 c7 f4 6f da 6d  |+Ln....\.&...o.m|
00000100  7e bb e0 68 f8 6f 0c 0d  d3 d1 3d 59 0d f7 95 c5  |~..h.o....=Y....|
00000110  6e 5f da 17 47 fb ca 64  38 13 5c fe 26 d7 c7 f4  |n_..G..d8.\.&...|
00000120  f9 37 4d ee e5 62 31 19  03 15 68 3a 1d ae 7b bd  |.7M..b1...h:..{.|
00000130  ee f7 bb 2b 4c 6e bb d0  f2 17 5c fe 26 d7 c7 f4  |...+Ln....\.&...|
00000140  6f da 6d 7e bb e0 68 f8  6f 0c 0d d3 d1 3d 59 0d  |o.m~..h.o....=Y.|
00000150  f7 95 c5 6e 5f da 17 47  fb ca 64 38 13 5c fe 26  |...n_..G..d8.\.&|
00000160  d7 c7 f4 f9 37 4d ee e5  62 31 19 00 00 00 00 00  |....7M..b1......|
00000170  00 00 00 00 03 11 e9 32  3a 3d a7 bf e5 79 dd eb  |.......2:=...y..|
00000180  b5 9f b6 62 ad 5a 4b 16  6b c9 62 38 9a 2c 17 9b  |...b.ZK.k.b8.,..|
00000190  c5 68 2d 59 0d 06 93 d9  64 36 58 ad 45 9b d5 6c  |.h-Y....d6X.E..l|
000001a0  38 99 cd 16 6b c5 60 b0  58 ff 85 a6 d3 e1 ba d7  |8...k.`.X.......|
000001b0  eb 7e bf bb c2 e4 b6 0b  2d 7f c1 e5 6f 72 7d 4c  |.~......-...or}L|
000001c0  ff a6 dd e6 b7 0b 8e 86  ff c6 d0 30 1d dd 93 d5  |...........0....|
000001d0  70 5f 59 ec f6 a5 7d 71  b4 af 4c 86 33 c1 e5 6f  |p_Y...}q..L.3..o|
000001e0  72 7d 4c 9f 7f d3 e4 5e  2e 16 93 01 03 13 54 79  |r}L....^......Ty|
000001f0  bd 0c 00 01 cb ed 6b 90  fd 64 00 00 00 00 01 cb  |......k..d......|
00000200

Unknown BootLoader  on sda3



=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
```

---

### Post by SuperDrive on 2011-04-02
I repaired windows boot with bootsect.exe and than i was able to load windows and delete all ext4 partitions on the third drive so there was no linux destro anymore but after the 11.04 setup was loaded, he could not recognize any other operating system. I hope this raid problem will be fixed until the final version.

You can lock the thread and thank you for helping me!

---

### Post by ronparent on 2011-04-02
Me too. The raid problem I reported as a bug is that dmraid does not get automatically installed with natty. The workaround until the problem is fixed is to chroot install dmraid to your mounted natty filesystem from the live cd. Post if you need help.

---

