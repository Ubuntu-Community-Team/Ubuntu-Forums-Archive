---
title: "Windows boot error after ubuntu install"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by jungledude on 2011-02-04
Hello wonderful ubuntu community. I've been having fun messing with 10.10, but only until I couldn't get back into Windows.  I don't believe I did anything specific to screw up the Win 7 bootloader, but when I try to boot 7 from Grub2 I just get an error screen that says something like
"Windows can't find the necessary boot data file. 
file: \boot\BCD
error: 0xc000000e"
and a few other things basically just telling me that it isn't gonna boot. So, I figured I had messed up the MBR and was gonna boot with my OEM 7 DVD to do a simple bootrec /fixmbr and i would be good to go. Problem is that my DVD won't let me do anything. When I click on "repair your computer" i get another lovely error message saying that my recovery options version is not compatible with my installed version of windows. Well, that doesn't make any sense because it's the same DVD i used to install 7! I've looked all over the place trying to find something similar but I have no idea how I can correct this from within Ubuntu or even a live CD.
Windows is dev/sda3 Ubuntu root is dev/sda5 dev/sda4 is my swap area. partitions 1 + 2 are for hackintosh. Please help me get 7 back! (I have attached my Results.txt file from the boot info script I found in one of the other threads)
thanks so much for your help.
-JD

---

### Post by Quackers on 2011-02-04
Your boot script output in code tags
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 865175768 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
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
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640   205,209,599   204,799,960 HFS+
/dev/sda3     743,075,840   860,258,303   117,182,464 Linux or Data
/dev/sda4     860,258,304   864,258,047     3,999,744 Linux Swap
/dev/sda5     864,258,048   884,695,039    20,436,992 Linux or Data
/dev/sda6     884,695,040   976,771,071    92,076,032 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        70D6-1701                              vfat       EFI                           
/dev/sda2        335f5746-7b5d-3109-985d-d41ce30180b8   hfsplus    Snow Leopard                  
/dev/sda3        90D4F0EBD4F0D486                       ntfs                                     
/dev/sda4        052739ee-492f-4986-95e5-d14ea9d18959   swap                                     
/dev/sda5        83a57ff0-2d75-4819-b1f3-8b32e21efeaa   ext4                                     
/dev/sda6        5563fb60-b39f-4f3d-a776-6b818f2a6d3d   ext4                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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

insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set 83a57ff0-2d75-4819-b1f3-8b32e21efeaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set 83a57ff0-2d75-4819-b1f3-8b32e21efeaa
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 83a57ff0-2d75-4819-b1f3-8b32e21efeaa
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=83a57ff0-2d75-4819-b1f3-8b32e21efeaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 83a57ff0-2d75-4819-b1f3-8b32e21efeaa
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=83a57ff0-2d75-4819-b1f3-8b32e21efeaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 83a57ff0-2d75-4819-b1f3-8b32e21efeaa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 83a57ff0-2d75-4819-b1f3-8b32e21efeaa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 7b31b09e7e38cac4
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 7b31b09e7e38cac4 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod part_gpt
	insmod hfsplus
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 7b31b09e7e38cac4
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 7b31b09e7e38cac4 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_gpt
	insmod ntfs
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set 90d4f0ebd4f0d486
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
UUID=83a57ff0-2d75-4819-b1f3-8b32e21efeaa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=052739ee-492f-4986-95e5-d14ea9d18959 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 442.9GB: boot/grub/core.img
 449.5GB: boot/grub/grub.cfg
 449.7GB: boot/initrd.img-2.6.35-25-generic-pae
 443.2GB: boot/vmlinuz-2.6.35-25-generic-pae
 449.7GB: initrd.img
 443.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb 7f 03 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


```

---

### Post by Quackers on 2011-02-04
Firstly, you have a GUID partition table, which often doesn't play nicely.
You have grub2 installed in the mbr of the drive but it's looking at a sector for its boot files, which isn't the norm.
Windows appears to have all its boot files intact, and it is in sda3. However, sda3 is reported in the "Drive/Partition Info:" of the boot script as " Linux or Data", which is strange, as it's reported as NTFS later in the script.

I don't know enough about GPT to comment on what is best for you. Others on here know much more about it than me, and hopefully someone will pay a visit and offer advice. In the meantime it may be worth while for you to take a look at the Apple users section of the forum.

---

### Post by srs5694 on 2011-02-05
It looks to me like you had a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration, which is a common way to get both OS X and Windows installed on a single hard disk, but something -- probably the Ubuntu installer -- reverted the hybrid MBR to a conventional protective MBR, which wiped out Windows' ability to boot. (Hybrid MBRs are ugly and dangerous, and the Ubuntu installer probably had to resize partitions to do its work, so I'm reluctant to be critical of the Ubuntu installer if this is what it's doing. Trying to preserve the hybrid MBR could have been very dangerous.)

[Here's another recent thread](http://ubuntuforums.org/showthread.php?t=1681341&highlight=GPT) that may be about a similar problem.[/url] I recommend you follow it, but don't post your own problem there in case they're different; trying to resolve two peoples' problems in one thread can quickly become a nightmare.

My suggestion is to create a fresh hybrid MBR. Despite the fact that they're ugly and dangerous, they're the simplest way to get OS X and Windows dual-booted on a single disk. (If you wanted to add a new disk, though, splitting OS X and Windows across disks would be safer in the long run.) You can create hybrid MBRs with various tools, but the most flexible is my [GPT fdisk (gdisk).](http://www.rodsbooks.com/gdisk/) Download a copy for OS X or Linux from [its Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) (*do not* use the version in the Ubuntu repositories; it's hopelessly out of date and has known bugs). Then follow the instructions on my [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) page. Include the Windows partition (/dev/sda3) in the hybrid MBR. You might as well include your two ext4 partitions, too, just to minimize the risk of some GPT-unaware Windows tool wreakng havoc with your Linux installation. With any luck, Windows will then begin to boot again. If not, using a Windows repair disc will probably help, but I can't make any promises about that -- Windows can be very finicky about its boot partition, and its repair tools are inadequate, in my experience.

---

### Post by 3177 on 2011-02-05
> **jungledude said:**
> i get another lovely error message saying that my recovery options version is not compatible with my installed version of windows.

  just wondering, does windows 7 have a service pack yet? If so you might as well re install windows, because you probably have it.

---

### Post by jungledude on 2011-02-05
Thanks Quackers and srs,
I believe you were indeed right on. I don't know enough about partition tables or grub2 but I'm not sure I actually ever had a hybrid MBR before as the only OS I could boot was Ubuntu. Grub2 must have indeed killed Windows, but after going through a couple more forums I figured it wouldn't hurt to run** gptsync**, so I did and then I **updated grub** and now voila! I have a working triple boot. I realize that this hybrid-MBR isn't the safest way to do things, but since I only have one HDD and don't believe I could somehow fit another one in my laptop, it will have to do for now. Thanks for your help (and utility) srs. Now I just hope no dumb windoze program screws up Linux or OS X. Oh, and even though it works I'm sure it isn't the most efficient way of doing things seeing as Grub takes longer than it should to load, IMO. Oh well, what's 4 seconds? If anyone has any ideas of how to speed up grub without messing up my OSs, I would love to know. Thanks again.

---

