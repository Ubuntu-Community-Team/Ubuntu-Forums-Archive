---
title: "Windows 7 &amp; Ubuntu 10.10 Dual Boot (Windows fails to start)"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by ishwadeep on 2010-11-24
I installed Ubuntu 10.10 alongside my Windows 7 installation. The installation was successful, but, now when I try to boot Windows nothing happens (apart from an indefinitely blinking '_'). I tried to do **startup repair** from my Windows 7 DVD but it is not detecting the hard disk. When I tried to run **chkdisk /f **from the command prompt it said that the disk is write protected. Later, on using **diskpart** and **list volume** the only volume detected is the CD/DVD ROM. 

The initial GRUB window points to /dev/sda2 for Windows 7. The Volumes snapshot from Disk Utility is attached!

Any idea as to how I can recover Windows 7?

Thanks for your help
Ishwadeep

---

### Post by Quackers on 2010-11-24
If you can boot into Ubuntu (and if not please boot from the Live cd and select "try ubuntu") then go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply).
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by garvinrick4 on 2010-11-24
#Go into Ubuntu and open a terminal: applications to Accessories to terminal and copy and paste this:
```
sudo update-grub
``````
sudo reboot
```#IF that fails to work do this for me.
Put a Ubuntu Cd in and boot off of it and choose Try Ubuntu look into the "system" partition sda1 under places menu, it is a small partition just for /boot to be in. Open it up and see if their are 2 boot folders in there one that says Boot and one that says boot. One with capitol B and one with a lower case b is the difference. Let me know before you touch them.

---

### Post by ishwadeep on 2010-11-24
@Quackers: Following are the contents of Results.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   102,440,959   102,234,112  42 SFS
/dev/sda4         102,443,006   312,580,095   210,137,090   5 Extended
/dev/sda5         102,443,008   106,440,703     3,997,696  82 Linux swap / Solaris
/dev/sda6         106,442,752   166,440,959    59,998,208  83 Linux
/dev/sda7         166,443,008   312,580,095   146,137,088  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   655,355,609   655,355,547   7 HPFS/NTFS
/dev/sdb2         900,685,824 1,953,521,663 1,052,835,840   7 HPFS/NTFS
/dev/sdb3         655,355,610   900,684,224   245,328,615   f W95 Ext d (LBA)
/dev/sdb5         655,355,673   900,684,224   245,328,552   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        D4BCC5F3BCC5CFE2                       ntfs       System Reserved               
/dev/sda3        AC48D0AD48D07792                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f37174cf-a5c4-4655-a691-fdae39657156   swap                                     
/dev/sda6        c927d354-c898-46c9-af72-e599acc288ce   ext4                                     
/dev/sda7        0eec43ab-071b-425d-a7ca-770cda979487   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46A4446FA4446411                       ntfs                                     
/dev/sdb2        9060A49460A48298                       ntfs       New Volume                    
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        1BDD-3735                              vfat       PS3                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb5        /media/PS3               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/46A4446FA4446411  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c927d354-c898-46c9-af72-e599acc288ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c927d354-c898-46c9-af72-e599acc288ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c927d354-c898-46c9-af72-e599acc288ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c927d354-c898-46c9-af72-e599acc288ce ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c927d354-c898-46c9-af72-e599acc288ce
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d4bcc5f3bcc5cfe2
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=c927d354-c898-46c9-af72-e599acc288ce /               ext4    errors=remount-ro 0       1
/dev/sda7       /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f37174cf-a5c4-4655-a691-fdae39657156 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  72.0GB: boot/grub/core.img
  82.6GB: boot/grub/grub.cfg
  55.1GB: boot/initrd.img-2.6.35-22-generic
  55.6GB: boot/initrd.img-2.6.35-23-generic
  72.0GB: boot/vmlinuz-2.6.35-22-generic
  71.9GB: boot/vmlinuz-2.6.35-23-generic
  55.6GB: initrd.img
  55.1GB: initrd.img.old
  71.9GB: vmlinuz
  72.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  9c 29 3f 36 01 38 f5 c0  ab b5 5e f3 cd 30 b7 90  |.)?6.8....^..0..|
00000010  50 4d 83 b0 c8 09 50 d8  38 ce 39 c6 68 11 c2 43  |PM....P.8.9.h..C|
00000020  e3 82 1a ce 35 b1 d1 de  7b d7 65 89 61 b9 93 0e  |....5...{.e.a...|
00000030  b8 3f 36 7c 9e e5 5f 20  e3 a7 52 4d 13 fc 41 8b  |.?6|.._ ..RM..A.|
00000040  c9 95 e4 b7 d2 a1 5d ca  22 17 32 ca 86 45 6c 9c  |......].".2..El.|
00000050  90 61 e0 ed e7 1c f7 1c  75 ae 82 2f f8 4a cd b3  |.a......u../.J..|
00000060  79 83 47 5b 80 e0 a8 53  31 42 bb 4e 41 cf 20 ee  |y.G[...S1B.NA. .|
00000070  c7 3c f1 9e 29 22 3e 2a  f2 e7 32 c7 a3 99 02 03  |.<..)">*..2.....|
00000080  08 46 97 ef e7 9d d9 1d  31 9e 9c e6 81 9c cd bf  |.F......1.......|
00000090  8f a7 8a de d6 4f ec ad  24 3c ea 8d 04 16 f7 12  |.....O..$<......|
000000a0  33 11 96 0c 72 21 e0 29  00 74 e7 27 a6 06 6e 68  |3...r!.).t.'..nh|
000000b0  ff 00 13 d6 f9 e3 fb 41  d3 a3 8f 73 19 0c 37 13  |.......A...s..7.|
000000c0  3b 04 0b b8 10 a6 11 93  d7 8e 3a 75 cf 15 d4 68  |;.........:u...h|
000000d0  c7 59 2f 3f f6 aa 58 aa  f1 e5 7d 8d a4 27 df 76  |.Y/?..X...}..'.v|
000000e0  e0 3d b9 15 a9 f9 d0 03  11 c4 85 1d 48 2a cb 90  |.=..........H*..|
000000f0  47 71 c5 4b 51 ff 00 cb  41 f4 3f cc 52 ed 3e bf  |Gq.KQ...A.?.R.>.|
00000100  a5 00 71 7f 11 b4 a6 d4  0d 94 91 c7 be 58 d6 45  |..q..........X.E|
00000110  52 35 99 34 f3 c9 5e 32  9f 78 71 df a6 3d eb 9b  |R5.4..^2.xq..=..|
00000120  1e 10 dd 6a 2d e2 8a 68  65 59 1c 41 24 5e 28 9b  |...j-..heY.A$^(.|
00000130  cd 62 fc bb 16 c6 5b 95  4c 29 07 a9 ae df c5 3a  |.b....[.L).....:|
00000140  f5 ae 8d 3d 9c 37 7a 45  fe a6 97 01 c7 99 67 a7  |...=.7zE......g.|
00000150  9b 94 88 2e 33 bf 19 23  39 18 e3 9c 1f 4a c9 4f  |....3..#9....J.O|
00000160  14 e9 3f 68 46 8f c3 1a  b1 78 62 69 a3 97 fb 15  |..?hF....xbi....|
00000170  93 69 0b bb 6a 92 06 18  81 c7 be 07 06 ba 23 ed  |.i..j.........#.|
00000180  6c b9 6f 63 37 c9 7d 4c  2b 0b 39 ac 92 df ed 2d  |l.oc7.}L+.9....-|
00000190  00 b9 85 a5 95 3c df 12  cb 23 ab 6c 50 aa e4 e3  |.....<...#.lP...|
000001a0  7a 96 52 30 00 0b 8c 8e  a6 a7 d1 f4 5f 2b 5a 82  |z.R0........_+Z.|
000001b0  e6 e5 44 70 b8 02 15 1e  20 96 56 9b b0 50 00 fe  |..Dp.... .V..P..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 3d 00 00 fe  |............=...|
000001d0  ff ff 05 fe ff ff 02 00  3d 00 00 88 93 03 00 00  |........=.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

@garvinrick4:
I updated grub and then rebooted, but still Windows 7 didn't boot.
The System Reserved partition contains only "Boot" folder apart from the directory "System Volume Information" and the three files "bootmgr", "grldr", "BOOTSECT.BAK".

Thanks

---

### Post by garvinrick4 on 2010-11-24
your mean grldr folder? What did you try to install before?

---

### Post by Quackers on 2010-11-24
Try running the startup repair with the Windows cd 3 times. Sometimes nothing is found until the third run.
Your Windows boot files are all there, but I don't like the look of sda1. Unknown file system is not a good sign.
Your first 3 partitions on sda show as SFS. This is a Windows thing (dynamic discs) as opposed to primary/logical etc. This has been known to cause problems for Linux.
It also looks like you have tried to install grub (not grub2) at some time.
See how the 3rd startup repair goes.

---

### Post by garvinrick4 on 2010-11-24
#Any which way you have to get rid of it for sure. grldr you do not need.
run the: In ubuntu and see if you can see windows in grub update: 
```
sudo update-grub 
```#There is no /bootmanager /boot/BCD in sda3 your Windows file system
worst that happens is you have to install that and then reinstall grub2, not
a big deal, let us know if boots into Windows after getting rid of grldr folder 
and updateing grub in ubuntu.

---

### Post by garvinrick4 on 2010-11-24
Ok quackers I am hitting the hay 4 am here, we keep typing at same time.
Have a good morning.

---

### Post by Quackers on 2010-11-24
Yep, sleep well sir :-)

---

### Post by ishwadeep on 2010-11-24
Removed **grldr** and updated grub. Following was seen on doing so.

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
```

On selecting to boot from Windows it actually booted from it but ended with the blue screen of death! Since then it gives me 2 options on booting windows **to startup repair** or to **load windows normally**. The latter always ends in the BSOD. The former still doesn't show any operating systems when it asks to "select an operating system to repair". Although, on clicking install Windows 7, it is now giving that option, i.e. it is detecting the hard disk now, but, I wanted to try other possibilities before taking that drastic step.

---

### Post by garvinrick4 on 2010-11-24
#This below is a working system with Windows 7 below and a /boot partition: notice now that you have gotten rid of the 
offending folder in your /boot partition you will be like sda1 below now as for the sda2 notice your file system 
in your script Windows is missing /boot manager /BCD in your sda3, this one has them.
#First step was to get rid of grldr in your /boot partition now I believe you have to put your boot files back into
windows 7 which will overwrite the grub2 so you will have to reinstall grub2.
This link below tells you how to do this: It is not hard nor  a long process. Any questions
ask. edit;(check next post I gave you commands )
#Your boot partition is sda2 and your / is sda6 both must be mounted when you install grub2.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

                          THIS BELOW IS A WORKING SYSTEMS NOT THE OP'S
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

```

---

### Post by garvinrick4 on 2010-11-24
#Use the link below to give the 2 commands to replace windows 7 boot files:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
#Below copy and paste these commands to put grub2 back into mbr looking for grub files in sda6

```

[CODE]sudo mkdir /media/boot
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda2 /media/boot
``````
sudo mount /dev/sda6 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/boot
``````
sudo umount /media/root
``````
sudo reboot
```Now go into ubuntu install on HDD and
```
sudo update-grub
```[/code]Now hopefully you have a working system, (never worked with sfs format), its all I got partner(should work): If any trouble post another boot script:

---

### Post by garvinrick4 on 2010-11-24
#If previous post fails read post 14-15-16 about sfs format.

[http://ubuntuforums.org/showthread.php?t=1629586&page=2](http://ubuntuforums.org/showthread.php?t=1629586&page=2)

#Edit: Just saw this poor guys boot script makes yours look like a jewel:
#Post how code worked interested in the sfs format, thanks:

---

### Post by ishwadeep on 2010-11-26
# sda1 was still showing unknown filesystem. 
# On running the 2 commands the /fixboot one gave an error that the volume file system was unrecognized. 
# /fixmbr completed successfully. 
# On rebooting, grub was gone, and windows was still not working. Both startup repair and the new installation option were not being able to detect the hard disk. 
# I used gparted and formatted the whole hard disk as I had already backed up everything and this was becoming unbearable. 
# On formatting windows was able to detect the hard disk and install.

It's winter vacations. Will install 10.04 when I come back next semester, thanks a lot for your help though. :)

---

### Post by garvinrick4 on 2010-11-26
Thanks for reply have been reading up on sfs format and seems to be a format that
Linux does not agree with at all and seems beyond my skill sets. Glad you
reformatted to NTFS and became a recognizable disk and got back on right track.
Again thanks for final reply so as to finish thread up. See you on next Semester have
a nice Holiday Season.

---

