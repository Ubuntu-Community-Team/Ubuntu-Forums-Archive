---
title: "Unable to boot after upgrade"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by shubham.joy on 2011-05-06
Today morning I was upgrading ubuntu 10.10 to 11.04. When the packages were downloading it was showing 20m left to download. At that time I had a battery of 2 hrs. As I had to go so I left my laptop on and went( the charger unplugged ). When I came back I get the following message:

```
init:udevtrigger main process (546) terminated with status 1
init:udevtrigger post-stop process(549) terminated with status 1
The disk drive for / is not ready yet or not present
Continue to wait; or press S to skip mounting or M for manual recovery
init: udev monitor main process (545) killed by term signal.
```I know this is coming because of improper shutdown. Also I think that the new ubuntu was not yet installed as in the boot menu it was showing old images only..

I had Widows 7 also. Thank god its fine so that I am able to ask question.

I am not a newbie but a little far from intermediate.
Thankyou

---

### Post by shubham.joy on 2011-05-06
I have booted from Live CD but not getting how to check my / filesystem using fsck.
Also how to access my home folder ? I have Importatnt data in it.

---

### Post by Hedgehog1 on 2011-05-06
If you are able to run in Windows, please download the ISO and make either a LiveCD or LiveUSB of 11.04

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

p.s. To copy your documents from the Ubuntu partitions to the Windows partition, you can use this: **_[ext2-ext3-ext4-filesystem-from-windows]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-filesystem-from-windows-7/")_**

---

### Post by shubham.joy on 2011-05-06
Thanks. ran the script and following is the result.txt file.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   136,314,879   136,108,032   7 HPFS/NTFS
/dev/sda3         136,314,880   346,028,031   209,713,152   7 HPFS/NTFS
/dev/sda4         346,032,126   976,771,071   630,738,946   f W95 Ext d (LBA)
/dev/sda5         346,032,128   555,747,327   209,715,200   7 HPFS/NTFS
/dev/sda6         555,749,376   891,293,695   335,544,320   7 HPFS/NTFS
/dev/sda7         891,295,744   976,771,071    85,475,328  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,183     7,818,121   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        14F84EEFF84ECF24                       ntfs       System Reserved               
/dev/sda2        4AE25127E2511891                       ntfs                                     
/dev/sda3        6A3459E43459B433                       ntfs       softwares                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        36C617DDC6179BE5                       ntfs       padh le mere baap             
/dev/sda6        EA3A38D73A38A28D                       ntfs       entertainment                 
/dev/sda7        82f91092-e522-45d3-84af-32a0c957459b   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B43F-DED3                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/entertainment     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 82f91092-e522-45d3-84af-32a0c957459b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 82f91092-e522-45d3-84af-32a0c957459b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=25
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 82f91092-e522-45d3-84af-32a0c957459b
    linux    /boot/vmlinuz-2.6.35-29-generic root=UUID=82f91092-e522-45d3-84af-32a0c957459b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-29-generic
}
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 14F84EEFF84ECF24
    chainloader +1
}

menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 82f91092-e522-45d3-84af-32a0c957459b
    echo    'Loading Linux 2.6.35-29-generic ...'
    linux    /boot/vmlinuz-2.6.35-29-generic root=UUID=82f91092-e522-45d3-84af-32a0c957459b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 82f91092-e522-45d3-84af-32a0c957459b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 82f91092-e522-45d3-84af-32a0c957459b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=82f91092-e522-45d3-84af-32a0c957459b /               ext4    errors=remount-ro 0       1

=================== sda7: Location of files loaded by Grub: ===================


 467.2GB: boot/grub/core.img
 476.6GB: boot/grub/grub.cfg
 457.9GB: boot/initrd.img-2.6.35-22-generic
 457.9GB: boot/initrd.img-2.6.35-23-generic
 458.7GB: boot/initrd.img-2.6.35-24-generic
 469.1GB: boot/initrd.img-2.6.35-25-generic
 471.9GB: boot/initrd.img-2.6.35-26-generic
 458.2GB: boot/initrd.img-2.6.35-27-generic
 476.3GB: boot/initrd.img-2.6.35-28-generic
 471.4GB: boot/initrd.img-2.6.35-29-generic
 467.2GB: boot/vmlinuz-2.6.35-22-generic
 467.3GB: boot/vmlinuz-2.6.35-23-generic
 458.3GB: boot/vmlinuz-2.6.35-24-generic
 469.0GB: boot/vmlinuz-2.6.35-25-generic
 469.0GB: boot/vmlinuz-2.6.35-26-generic
 468.9GB: boot/vmlinuz-2.6.35-27-generic
 469.2GB: boot/vmlinuz-2.6.35-28-generic
 469.2GB: boot/vmlinuz-2.6.35-29-generic
 478.8GB: boot/vmlinuz-2.6.38-9-generic
 471.4GB: initrd.img
 476.3GB: initrd.img.old
 469.2GB: vmlinuz
 469.2GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================


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

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 7a 04  |.X.SYSLINUX...z.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  89 4b 77 00 c3 1d 00 00  00 00 00 00 02 00 00 00  |.Kw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 d3 de 3f b4 4e  4f 20 4e 41 4d 45 20 20  |..)..?.NO NAME  |
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
00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
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



```

---

### Post by Hedgehog1 on 2011-05-07
shubham.joy,

Thanks for posting the script.

Your main drive appears to have a single Linux partition, with no swap space.

I would suggest the following plan of attack to save your data and do a clean Ubuntu install:

From your LiveCD/LiveUSB, use the GUI to move files from /dev/sda7 (you Linux Partition) to an NTFS partition for safe keeping.

The GUI is called nautilus.  If you find you don't have access rights to your documents, you can run nautilus in root (God Jr.) mode:

```
gksudo nautilus
```

Once you have your data saved from the Linux Partition, you then can reinstall Natty (or reinstall 10.10 id you prefer).  If you are going to do a clean install of Natty - the option for the manual install is now called 'Something Else'.

Set /dev/sda7 to be 'ext4', '/' and set the format flag.

***The Hedge***

:KS

---

### Post by shubham.joy on 2011-05-07
> **Hedgehog1 said:**
> shubham.joy,

Thanks for posting the script.

Your main drive appears to have a single Linux partition, with no swap space.

I would suggest the following plan of attack to save your data and do a clean Ubuntu install:

From your LiveCD/LiveUSB, use the GUI to move files from /dev/sda7 (you Linux Partition) to an NTFS partition for safe keeping.

The GUI is called nautilus.  If you find you don't have access rights to your documents, you can run nautilus in root (God Jr.) mode:

```
gksudo nautilus
```Once you have your data saved from the Linux Partition, you then can reinstall Natty (or reinstall 10.10 id you prefer).  If you are going to do a clean install of Natty - the option for the manual install is now called 'Something Else'.

Set /dev/sda7 to be 'ext4', '/' and set the format flag.

***The Hedge***

:KS

Thankyou The Hedge.
Yeah I will do a fresh installation but actually my main motive for  posting was to learn about this as I am a Btech student and a lot of  stress is given on Linux. 
So still if there is something I can do to save or learn or even can know How and why this problem came, I would love to. So for now I have kept my ubuntu as it is ( in the error situation ) and am using windows. I am waiting for more things to experiment. 
The script part was also very very informative. Also I got a very crucial piece of information about accessing ubuntu's home folder from windows which I was searching for quite sometime.

Thankyou once again.

---

