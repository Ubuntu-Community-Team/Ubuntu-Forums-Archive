---
title: "How to boot"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by Axman10 on 2010-11-03
This is my first experience with anything other than stock Windows. I just finished installing Ubuntu and it made me restart, but after I restarted I automatically went to Windows.

How do I get to Ubuntu?

---

### Post by wilee-nilee on 2010-11-03
> **Axman10 said:**
> This is my first experience with anything other than stock Windows. I just finished installing Ubuntu and it made me restart, but after I restarted I automatically went to Windows.

How do I get to Ubuntu?

Lets make this a easy as possible to get to the problem.

Click on the bootscript link in my signature download it and run it on a Live Ubuntu cd. Come back to the forum and hit reply to generate code tags [ code] [ /code] and put the text from the generated file in between.

---

### Post by Axman10 on 2010-11-03
> **wilee-nilee said:**
> Lets make this a easy as possible to get to the problem.

Click on the bootscript link in my signature download it and run it on a Live Ubuntu cd. Come back to the forum and hit reply to generate code tags [ code] [ /code] and put the text from the generated file in between.

I used a USB instead of a CD, so would I just plop it on there and run it? I'm not sure what you mean.

---

### Post by wilee-nilee on 2010-11-03
Yes any live Ubuntu or installed Linux environment will work.

You might see the problem in the script yourself it is a very useful tool.

---

### Post by Axman10 on 2010-11-04
Sorry about the wait, had an emergency.

So I don't think I'm doing what you asked. What I did was, I dragged the script into the USB, then restarted my comp and booted from the USB. It went to the Ubuntu installer, and nothing else happened.

---

### Post by lisati on 2010-11-04
> **Axman10 said:**
> Sorry about the wait, had an emergency.

So I don't think I'm doing what you asked. What I did was, I dragged the script into the USB, then restarted my comp and booted from the USB. It went to the Ubuntu installer, and nothing else happened.

You need to start Ubuntu using the "try Ubuntu" option then use the script.

---

### Post by wilee-nilee on 2010-11-04
> **Axman10 said:**
> Sorry about the wait, had an emergency.

So I don't think I'm doing what you asked. What I did was, I dragged the script into the USB, then restarted my comp and booted from the USB. It went to the Ubuntu installer, and nothing else happened.

Read the link carefully you boot a live Ubuntu environment, you then download the script put it on the desktop then run this command in the Ubuntu terminal....
```
sudo bash ~/Desktop/boot_info_script*.sh 
``` 

Which you will generate a text file come back and post the text in code tags as I described. It's a lot of text it is hard to read other wise.

Hey it took me a few tries the first time as well it is a little geeky, I guess.

---

### Post by Axman10 on 2010-11-04
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

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

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,004,102,902 1,004,102,840   7 HPFS/NTFS
/dev/sdb2       1,004,103,678 1,250,263,039   246,159,362   5 Extended
/dev/sdb5       1,004,103,680 1,244,123,135   240,019,456  83 Linux
/dev/sdb6       1,244,125,184 1,250,263,039     6,137,856  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2042 MB, 2042764800 bytes
32 heads, 63 sectors/track, 1979 cylinders, total 3989775 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,987,647     3,987,585   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        82A43ACBA43AC189                       ntfs       mybackup                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AC6431D36431A14E                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        131ff2cc-94a1-448f-8adf-95d07f0d0ba7   ext4                                     
/dev/sdb6        0acb5dc7-809b-4e1f-913b-c6c4c6d0c162   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9099-C596                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/AC6431D36431A14E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/131ff2cc-94a1-448f-8adf-95d07f0d0ba7 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/mybackup          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 131ff2cc-94a1-448f-8adf-95d07f0d0ba7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 131ff2cc-94a1-448f-8adf-95d07f0d0ba7
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 131ff2cc-94a1-448f-8adf-95d07f0d0ba7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=131ff2cc-94a1-448f-8adf-95d07f0d0ba7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 131ff2cc-94a1-448f-8adf-95d07f0d0ba7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=131ff2cc-94a1-448f-8adf-95d07f0d0ba7 ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 131ff2cc-94a1-448f-8adf-95d07f0d0ba7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 131ff2cc-94a1-448f-8adf-95d07f0d0ba7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ac6431d36431a14e
    drivemap -s (hd0) ${root}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=131ff2cc-94a1-448f-8adf-95d07f0d0ba7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0acb5dc7-809b-4e1f-913b-c6c4c6d0c162 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 608.7GB: boot/grub/core.img
 613.0GB: boot/grub/grub.cfg
 514.9GB: boot/initrd.img-2.6.35-22-generic
 608.7GB: boot/vmlinuz-2.6.35-22-generic
 514.9GB: initrd.img
 608.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 22 00  |.X.SYSLINUX...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  81 d8 3c 00 2f 0f 00 00  00 00 00 00 02 00 00 00  |..<./...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 96 c5 99 90 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 60 c6 15 00  66 ba 00 00 00 00 bb 00  |}.f.`...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Axman10 on 2010-11-04
So does that help at all?

---

### Post by oldfred on 2010-11-04
Grub goes off and installs to sda. The boot script or grub do not identify which drive it really used. So I think if in BIOS you change to boot the 80GB drive Ubuntu will boot. If not we will install grub to the 640GB drive.

In fact once booted you still should install grub2 to the 640GB drive. I recommend that each drive have the bootloader in the MBR of the same drive as the system install.

Let us know if booting 80GB drive works or not, then we can go from there.

---

### Post by Axman10 on 2010-11-04
Alright, when I booted from the 80 gig drive, it went to what I think was Grub, and I was able to choose linux. Looks like it worked :P 

Although, I wasn't able to use the arrow keys, it just chose linux after so many seconds.

---

### Post by oldfred on 2010-11-04
Grub uses the BIOS setting on USB keyboard and mouse. Windows & Ubuntu seem to ignore BIOS and just work. You probably have a setting in BIOS to use USB mouse & keyboard.

If booted you can install grub to the 640GB drive. You can leave it as is if you want but if your 80GB drive ever dies you then will have to use the liveCD to reinstall grub.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Using liveCD
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Axman10 on 2010-11-04
I did all that up until sudo dpkg-reconfigure grub-pc where the terminal didn't do anything for 20 minutes so I closed it, and now it won't let me do it again.

---

### Post by Chad9942 on 2010-11-04
I too am new to this. I have downloaded the file and saved it to a cd to boot.

When I boot the cd is not recognized as a boot cd.  Any help would be greatly appreciated.:guitar:

---

### Post by oldfred on 2010-11-05
I just ran the sudo dpkg-reconfigure grub-pc. It looks like the alternative installer as it is text based. You just accept the first couple of screens and tell it where to reinstall grub. It only took a minute total.

Chad9942
Please do not hijack thread. If you have problem start a new thread.
Did you follow instructions here under #2 and click on show me how button?
[http://www.ubuntulinux.org/desktop/get-ubuntu/download](http://www.ubuntulinux.org/desktop/get-ubuntu/download)

---

