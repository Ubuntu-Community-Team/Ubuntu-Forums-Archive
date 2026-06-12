---
title: "Installed but doesn't boot. How to?"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by amol7 on 2016-03-05
Ya, so I bought anew HP Laptop, and obviously, with no OS on board.
Comes with Free DOS.
Now I stalled Ubuntu 12.04.5 LTS using a Live CD and after that I cannot seem to get the option to choose Ubuntu to boot.
Of course after this I searched this forum and the internet, for solutions and everyone tells that just load Ubuntu over FreeDOS. (Too late right, yeah)
So now I have Ubuntu installed and it doesn't boot. It always goes to FreeDOS and HP Documents option.
Unfortunately, I cannot connect to the internet via the Wifi option as some how it cannot detect the wifi, and because of this I cannot install boot-repair as suggested here [http://askubuntu.com/questions/190252/installed-ubuntu-on-partition-of-hd-with-vista-but-doesnt-boot/190301#190301](http://askubuntu.com/questions/190252/installed-ubuntu-on-partition-of-hd-with-vista-but-doesnt-boot/190301#190301)

Basically, I know I should have installed Ubuntu over FreeDOS but now that I haven't done that, and installed Ubuntu, what should I so to get that installed Ubuntu to work for me?
So anyone here can tell me how to get through to the installation or I dunno what esle I can ask here.
Please help.

Thank You for your time.

~a

---

### Post by vidtek on 2016-03-05
> **amol7 said:**
> Ya, so I bought anew HP Laptop, and obviously, with no OS on board.
Comes with Free DOS.
Now I stalled Ubuntu 12.04.5 LTS using a Live CD and after that I cannot seem to get the option to choose Ubuntu to boot.
Of course after this I searched this forum and the internet, for solutions and everyone tells that just load Ubuntu over FreeDOS. (Too late right, yeah)
So now I have Ubuntu installed and it doesn't boot. It always goes to FreeDOS and HP Documents option.
Unfortunately, I cannot connect to the internet via the Wifi option as some how it cannot detect the wifi, and because of this I cannot install boot-repair as suggested here [http://askubuntu.com/questions/190252/installed-ubuntu-on-partition-of-hd-with-vista-but-doesnt-boot/190301#190301](http://askubuntu.com/questions/190252/installed-ubuntu-on-partition-of-hd-with-vista-but-doesnt-boot/190301#190301)

Basically, I know I should have installed Ubuntu over FreeDOS but now that I haven't done that, and installed Ubuntu, what should I so to get that installed Ubuntu to work for me?
So anyone here can tell me how to get through to the installation or I dunno what esle I can ask here.
Please help.

Thank You for your time.

~a

So looks like your new laptop has a dvd drive, if it also has a network lan socket you could connect directly to your router via a lan cable to get on the internet.  Otherwise, go to a friend's place and download the boot repair disc, then burn it to a cd/dvd.
Tony.

---

### Post by amol7 on 2016-03-05
> **vidtek said:**
> So looks like your new laptop has a dvd drive, if it also has a network lan socket you could connect directly to your router via a lan cable to get on the internet.  Otherwise, go to a friend's place and download the boot repair disc, then burn it to a cd/dvd.
Tony.

So just doing that would solve the problem? Or is other any other problem. Like has this problem (no booting Ubuntu) got anything to do with UEFI / Legacy mode?

Thanks

~a

---

### Post by amol7 on 2016-03-05
> **vidtek said:**
> So looks like your new laptop has a dvd drive, if it also has a network lan socket you could connect directly to your router via a lan cable to get on the internet.  Otherwise, go to a friend's place and download the boot repair disc, then burn it to a cd/dvd.
Tony.


Nope I tried that method, still doesn't boot to Ubuntu. Same problem.

Any other ideas?

Thanks

~a

---

### Post by grahammechanical on 2016-03-05
Before installing did you run the Ubuntu Try/Live session?

When you installed what option did you chose? Install Ubuntu alongside [other operating systems] or Erase disk & install Ubuntu? In either case the installer would have installed a Linux boot loader (Grub) onto the first (only?) hard disk. And it would have over-written any freedos boot loader.

Were you connected to the internet during the installation of Ubuntu?

Yes, if we have a motherboard that has a UEFI boot system it makes a difference if we install Ubuntu in EFI mode or BIOS/CSM/Legacy mode. If Ubuntu is the only OS then we can install it in EFI mode or BIOS mode. It is our choice. But,

If freedos is installed in EFI mode then Ubuntu must be installed in EFI mode. If freedos is installed in BIOS mode then Ubuntu must be installed in BIOS mode. Think of it as a law of the universe.

Here you are with a new computer and it has on it an OS that you did not pay for and do not want to use. So, what is stopping you from re-installing and choosing the Erase disk & install Ubuntu option? 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by yancek on 2016-03-05
You didn't post the output from running boot repair.   There is an option to Create BootInfo Summary you should have selected and posted it or a link to it.

---

### Post by amol7 on 2016-03-05
> **grahammechanical said:**
> Before installing did you run the Ubuntu Try/Live session?

When you installed what option did you chose? Install Ubuntu alongside [other operating systems] or Erase disk & install Ubuntu? In either case the installer would have installed a Linux boot loader (Grub) onto the first (only?) hard disk. And it would have over-written any freedos boot loader.

Were you connected to the internet during the installation of Ubuntu?

Yes, if we have a motherboard that has a UEFI boot system it makes a difference if we install Ubuntu in EFI mode or BIOS/CSM/Legacy mode. If Ubuntu is the only OS then we can install it in EFI mode or BIOS mode. It is our choice. But,

If freedos is installed in EFI mode then Ubuntu must be installed in EFI mode. If freedos is installed in BIOS mode then Ubuntu must be installed in BIOS mode. Think of it as a law of the universe.

Here you are with a new computer and it has on it an OS that you did not pay for and do not want to use. So, what is stopping you from re-installing and choosing the Erase disk & install Ubuntu option? 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

Yes I did run the Live DVD Session Actually a friend of mine did, I saw it)
I connected to internet via the LAN option, connected to the Router directly using the cable. i ran the Boot-repair utility and yet nothing worked.
I'm running it again as we speak.

And yes I did use the "Install Ubuntu alongside" option. (Well the FreeDOS option is coming so I'm pretty sure of the option)
from the BIOS Settings, it was always set to EFI mode and not Legacy mode.

Well Ya I can always, reinstall Ubuntu, but I wanted to Preserve the Data of the HP Documents that is an option alongside the FreeDOS option at startup (boot)
Besides I also wanted to have a separate Swap space. As I'm a noob, I thought go for manual partition.

Thanks

~a

---

### Post by amol7 on 2016-03-05
> **yancek said:**
> You didn't post the output from running boot repair.   There is an option to Create BootInfo Summary you should have selected and posted it or a link to it.

I couldn't attach.
Here's the full text.

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


```


============================= Boot Info Summary: ===============================


 => Windows 7/8/2012 is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /KERNEL.SYS /COMMAND.COM


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 33728 of /dev/sda2 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi /ldlinux.sys /KERNEL.SYS 
                       /COMMAND.COM


sda3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda7: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1               2,048    16,371,711    16,369,664   b W95 FAT32
/dev/sda2    *     16,371,712    32,741,375    16,369,664   c W95 FAT32 (LBA)
/dev/sda3          32,743,422   976,771,071   944,027,650   5 Extended
/dev/sda5          32,743,424    92,741,631    59,998,208  83 Linux
/dev/sda6          92,743,680   108,742,655    15,998,976  82 Linux swap / Solaris
/dev/sda7         108,744,704   976,771,071   868,026,368  83 Linux




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        82F0-C44A                              vfat       HPDOCS
/dev/sda2        62F1-4C5A                              vfat       
/dev/sda5        d28f122d-a528-49bf-bf66-d65e05d327e5   ext4       
/dev/sda6        38719cfe-d2b5-4449-bf40-0e865bb2d96d   swap       
/dev/sda7        3bd5c165-54e3-4338-9fd3-6b100dd1a5b7   ext4       
/dev/sr0                                                iso9660    Ubuntu 12.04.5 LTS amd64


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Mar  5 13:40 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  6  2016 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  6  2016 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  6  2016 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar  6  2016 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar  6  2016 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar  6  2016 ata-TOSHIBA_MQ01ABF050_Y5GJCX2VT-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Mar  6  2016 ata-hp_DVDRW_GUD1N_KVTFBGG1653 -> ../../sr0
lrwxrwxrwx 1 root root  9 Mar  5 13:40 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  6  2016 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  6  2016 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  6  2016 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar  6  2016 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar  6  2016 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar  6  2016 scsi-SATA_TOSHIBA_MQ01ABF_Y5GJCX2VT-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Mar  5 13:40 wwn-0x50000396a3c043de -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  6  2016 wwn-0x50000396a3c043de-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  6  2016 wwn-0x50000396a3c043de-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  6  2016 wwn-0x50000396a3c043de-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar  6  2016 wwn-0x50000396a3c043de-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar  6  2016 wwn-0x50000396a3c043de-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar  6  2016 wwn-0x50000396a3c043de-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Mar  6  2016 wwn-0x5001480000000000 -> ../../sr0


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




============================== sda2/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
menu hshift 11
menu vshift 3
menu width 55
menu rows 15
menu margin 4


menu title Boot Menu
include live.cfg


menu background splash.png


default vesamenu.c32
menu color border 0 #ffffffff #ee000000 std
menu color title 0 #ffffffff #ee000000 std
menu color sel 0 #ff000000 #99ffffff rev
#menu color sel 0 #ffffffff #85000000 std
#menu color unsel 0 #ffffffff #ee000000 std
menu color pwdheader 0 #ff000000 #99ffffff rev
menu color pwdborder 0 #ff000000 #99ffffff rev
menu color pwdentry 0 #ff000000 #99ffffff rev
#menu color hotkey 0 #ffffffff #ee000000 std
#menu color hotsel 0 #ffffffff #85000000 std
menu color hotsel 0 #ff000000 #99ffffff rev


prompt 0
timeout 100
noescape 1
nocomplete 1
allowoptions 0
--------------------------------------------------------------------------------


================= sda2: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    2
            ?? = ??             chain.c32                                      1
            ?? = ??             libcom32.c32                                   1
            ?? = ??             libutil.c32                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             vesamenu.c32                                   1


============== sda2: Version of COM32(R) files used by Syslinux: ===============


 chain.c32                          :  not a COM32/COM32R module
 libcom32.c32                       :  not a COM32/COM32R module
 libutil.c32                        :  not a COM32/COM32R module
 menu.c32                           :  not a COM32/COM32R module
 vesamenu.c32                       :  not a COM32/COM32R module


=========================== sda5/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}


insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root d28f122d-a528-49bf-bf66-d65e05d327e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root d28f122d-a528-49bf-bf66-d65e05d327e5
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d28f122d-a528-49bf-bf66-d65e05d327e5
	linux	/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=d28f122d-a528-49bf-bf66-d65e05d327e5 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d28f122d-a528-49bf-bf66-d65e05d327e5
	echo	'Loading Linux 3.13.0-32-generic ...'
	linux	/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=d28f122d-a528-49bf-bf66-d65e05d327e5 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.13.0-32-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d28f122d-a528-49bf-bf66-d65e05d327e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root d28f122d-a528-49bf-bf66-d65e05d327e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "FreeDOS (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 82F0-C44A
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "FreeDOS (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 62F1-4C5A
	drivemap -s (hd0) ${root}
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


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
--------------------------------------------------------------------------------


=============================== sda5/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d28f122d-a528-49bf-bf66-d65e05d327e5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=3bd5c165-54e3-4338-9fd3-6b100dd1a5b7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=38719cfe-d2b5-4449-bf40-0e865bb2d96d none            swap    sw              0       0
UUID=62F1-4C5A	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------


=================== sda5: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


  37.777854919 = 40.563662848   boot/grub/grub.cfg                             1
  16.079700470 = 17.265446912   boot/vmlinuz-3.13.0-32-generic                 1
  37.776832581 = 40.562565120   boot/vmlinuz-3.13.0-32-generic.efi.signed      1
  16.079700470 = 17.265446912   vmlinuz                                        1
  16.279315948 = 17.479782400   boot/initrd.img-3.13.0-32-generic              1
  16.279315948 = 17.479782400   initrd.img                                     1


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda1


00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 08 5a 03  |.X.FRDOS4.1...Z.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 c8 f9 00 53 3e 00 00  00 00 00 00 02 00 00 00  |....S>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 4a c4 f0 82 4e  4f 20 4e 41 4d 45 20 20  |..)J...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 5e 5a  |@.^.s........_^Z|
000001c0  c3 4c 6f 61 64 69 6e 67  20 46 72 65 65 44 4f 53  |.Loading FreeDOS|
000001d0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4e 6f  |..............No|
000001f0  20 4b 45 52 4e 45 4c 20  20 53 59 53 00 00 55 aa  | KERNEL  SYS..U.|
00000200




=============================== StdErr Messages: ===============================


umount: /mnt/BootInfo/sda5: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-03-05__13h39 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 4ppa35
boot-repair is executed in live-session (Ubuntu 12.04.5 LTS, precise, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory


=================== os-prober:
/dev/sda1:FreeDOS:FreeDOS:chain
/dev/sda2:FreeDOS:FreeDOS1:chain
/dev/sda5:Ubuntu 12.04.5 LTS (12.04):Ubuntu:linux


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="HPDOCS" UUID="82F0-C44A" TYPE="vfat"
/dev/sda2: UUID="62F1-4C5A" TYPE="vfat"
/dev/sda5: UUID="d28f122d-a528-49bf-bf66-d65e05d327e5" TYPE="ext4"
/dev/sda6: UUID="38719cfe-d2b5-4449-bf40-0e865bb2d96d" TYPE="swap"
/dev/sda7: UUID="3bd5c165-54e3-4338-9fd3-6b100dd1a5b7" TYPE="ext4"
/dev/sr0: LABEL="Ubuntu 12.04.5 LTS amd64" TYPE="iso9660"




1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 0 Windows, 2 unknown type OS.


Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug  7  2014 grub.d
total 60
-rwxr-xr-x 1 root root 7806 Jul 25  2014 00_header
-rwxr-xr-x 1 root root 5522 Jul 25  2014 05_debian_theme
-rwxr-xr-x 1 root root 7877 Jul 25  2014 10_linux
-rwxr-xr-x 1 root root 6449 Jul 25  2014 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 6675 Jul 25  2014 30_os-prober
-rwxr-xr-x 1 root root 1388 Jul 25  2014 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Jul 25  2014 40_custom
-rwxr-xr-x 1 root root   95 Jul 25  2014 41_custom
-rw-r--r-- 1 root root  483 Jul 25  2014 README








=================== sda5/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






/boot/efi detected in the fstab of sda5: UUID=62F1-4C5A	 (sda2)


=================== efibootmgr -v
BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 2002,0000,2001,2004
Boot0000* ubuntu	HD(2,f9d000,f9c800,23a60800)File(EFIubuntushimx64.efi)RC
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050	BIOS(2,500,11)................-.N.......N.A.N.............................................A.........................
Boot0002* Internal CD/DVD ROM Drive	BIOS(3,500,496e7465726e616c2043442f44564420524f4d20447269766500)................-.U.......U.A.U.............................................A.........................
Boot0003* Internal CD/DVD ROM Drive (UEFI)	ACPI(a0341d0,0)PCI(1f,2)03120a00010000000000CD-ROM(1,5dfd3,1100)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3000* Internal Hard Disk or Solid State Disk	RC


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda5	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda5.
sda7	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda7.


sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	liveusb,	has-os,	2048 sectors * 512 bytes




=================== parted -l:


Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
1      1049kB  8382MB  8381MB  primary   fat32
2      8382MB  16.8GB  8381MB  primary   fat32           boot, lba
3      16.8GB  500GB   483GB   extended
5      16.8GB  47.5GB  30.7GB  logical   ext4
6      47.5GB  55.7GB  8191MB  logical   linux-swap(v1)
7      55.7GB  500GB   444GB   logical   ext4




Model: hp DVDRW GUD1N (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac


Number  Start   End     Size    File system  Name   Flags
1      8192B   24.6kB  16.4kB               Apple
2      3154MB  3163MB  8913kB               EFI


=================== parted -lm:


BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA TOSHIBA MQ01ABF0;
1:1049kB:8382MB:8381MB:fat32::;
2:8382MB:16.8GB:8381MB:fat32::boot, lba;
3:16.8GB:500GB:483GB:::;
5:16.8GB:47.5GB:30.7GB:ext4::;
6:47.5GB:55.7GB:8191MB:linux-swap(v1)::;
7:55.7GB:500GB:444GB:ext4::;


BYT;
/dev/sr0:4700MB:scsi:2048:2048:mac:hp DVDRW GUD1N;
1:8192B:24.6kB:16.4kB::Apple:;
2:3154MB:3163MB:8913kB::EFI:;


=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          465.8G
sda1  part vfat       7.8G HPDOCS
sda2  part vfat       7.8G
sda3  part              1K
sda5  part ext4      28.6G
sda6  part swap       7.6G
sda7  part ext4     413.9G
sr0   rom  iso9660    4.4G Ubuntu 12.04.5 LTS amd64
loop0 loop squashfs 712.6M


KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         [SWAP]
sda7     1  0  0         /mnt/boot-sav/sda7
sr0      1  0  1 running /cdrom
loop0    1  1  0         /rofs




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 08 5a 03  |.X.FRDOS4.1...Z.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 c8 f9 00 53 3e 00 00  00 00 00 00 02 00 00 00  |....S>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 4a c4 f0 82 4e  4f 20 4e 41 4d 45 20 20  |..)J...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 5e 5a  |@.^.s........_^Z|
000001c0  c3 4c 6f 61 64 69 6e 67  20 46 72 65 65 44 4f 53  |.Loading FreeDOS|
000001d0  20 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  | ...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4e 6f  |..............No|
000001f0  20 4b 45 52 4e 45 4c 20  20 53 59 53 00 00 55 aa  | KERNEL  SYS..U.|
00000200


=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 5a 03  |.X.SYSLINUX...Z.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 d0 f9 00  |........?.......|
00000020  00 c8 f9 00 53 3e 00 00  00 00 00 00 02 00 00 00  |....S>..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 5a 4c f1 62 4e  4f 20 4e 41 4d 45 20 20  |..)ZL.bNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d f8 50 50 50 50 cd  13 eb 62 8b 55 aa 8b 75  |.M.PPPP...b.U..u|
000000a0  a8 c1 ee 04 01 f2 83 fa  4f 76 31 81 fa b2 07 73  |........Ov1....s|
000000b0  2b f6 45 b4 7f 75 25 38  4d b8 74 20 66 3d 21 47  |+.E..u%8M.t f=!G|
000000c0  50 54 75 10 80 7d b8 ed  75 0a 66 ff 75 ec 66 ff  |PTu..}..u.f.u.f.|
000000d0  75 e8 eb 0f 51 51 66 ff  75 bc eb 07 51 51 66 ff  |u...QQf.u...QQf.|
000000e0  36 1c 7c b4 08 e8 e9 00  72 13 20 e4 75 0f c1 ea  |6.|.....r. .u...|
000000f0  08 42 89 16 1a 7c 83 e1  3f 89 0e 18 7c fb bb aa  |.B...|..?...|...|
00000100  55 b4 41 e8 cb 00 72 10  81 fb 55 aa 75 0a f6 c1  |U.A...r...U.u...|
00000110  01 74 05 c6 06 46 7d 00  66 b8 c0 83 00 00 66 ba  |.t...F}.f.....f.|
00000120  00 00 00 00 bb 00 80 e8  0e 00 66 81 3e 1c 80 8e  |..........f.>...|
00000130  c1 80 6a 75 74 e9 f8 02  66 03 06 60 7b 66 13 16  |..jut...f..`{f..|
00000140  64 7b b9 10 00 eb 2b 66  52 66 50 06 53 6a 01 6a  |d{....+fRfP.Sj.j|
00000150  10 89 e6 66 60 b4 42 e8  77 00 66 61 8d 64 10 72  |...f`.B.w.fa.d.r|
00000160  01 c3 66 60 31 c0 e8 68  00 66 61 e2 da c6 06 46  |..f`1..h.fa....F|
00000170  7d 2b 66 60 66 0f b7 36  18 7c 66 0f b7 3e 1a 7c  |}+f`f..6.|f..>.||
00000180  66 f7 f6 31 c9 87 ca 66  f7 f7 66 3d ff 03 00 00  |f..1...f..f=....|
00000190  77 17 c0 e4 06 41 08 e1  88 c5 88 d6 b8 01 02 e8  |w....A..........|
000001a0  2f 00 66 61 72 01 c3 e2  c9 31 f6 8e d6 bc 68 7b  |/.far....1....h{|
000001b0  8e de 66 8f 06 78 00 be  da 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001c0  0e bb 07 00 cd 10 eb f2  31 c0 cd 16 cd 19 f4 eb  |........1.......|
000001d0  fd 8a 16 74 7b 06 cd 13  07 c3 42 6f 6f 74 20 65  |...t{.....Boot e|
000001e0  72 72 6f 72 0d 0a 00 00  00 00 00 00 00 00 00 00  |rror............|
000001f0  00 00 00 00 00 00 00 00  fe 02 b2 3e 18 37 55 aa  |...........>.7U.|
00000200


=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G  114M  1.8G   6% /
udev           devtmpfs   1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs      387M  828K  387M   1% /run
/dev/sr0       iso9660    758M  758M     0 100% /cdrom
/dev/loop0     squashfs   713M  713M     0 100% /rofs
tmpfs          tmpfs      1.9G   28K  1.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.9G   76K  1.9G   1% /run/shm
/dev/sda1      vfat       7.8G  203M  7.6G   3% /mnt/boot-sav/sda1
/dev/sda2      vfat       7.8G  280M  7.6G   4% /mnt/boot-sav/sda2
/dev/sda5      ext4        29G  2.3G   25G   9% /mnt/boot-sav/sda5
/dev/sda7      ext4       408G   71M  387G   1% /mnt/boot-sav/sda7


=================== fdisk -l:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x23a60800


Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    16371711     8184832    b  W95 FAT32
/dev/sda2   *    16371712    32741375     8184832    c  W95 FAT32 (LBA)
/dev/sda3        32743422   976771071   472013825    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5        32743424    92741631    29999104   83  Linux
/dev/sda6        92743680   108742655     7999488   82  Linux swap / Solaris
/dev/sda7       108744704   976771071   434013184   83  Linux






=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda5, using the following options:        sda2/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi




Mount sda2 on /mnt/boot-sav/sda5/boot/efi
ls sda2/efi: /ubuntu/shimx64.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg
ls sda2: autoexec.bat
bootfix
boot-sav
chain.c32
command.com
EFI
fdconfig.sys
fdos
kernel.sys
LDLINUX.C32
LDLINUX.SYS
libcom32.c32
libutil.c32
live
live.cfg
menu.c32
P00KFVB2.CVA
splash.png
swsetup
syslinux.cfg
Thumbs.db
vesamenu.c32  . Please report this message to [email]boot.repair@gmail.com[/email]


*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:1616] (rev 09)
Subsystem: Hewlett-Packard Company Device [103c:80c1]
Kernel driver in use: i915
Kernel modules: i915_bdw
*******


grub-install --version
grub-install (GRUB) 1.99-21ubuntu3.16,grub-install (GRUB) 1.
GRUB too old for SecureBoot. Please report this message to [email]boot.repair@gmail.com[/email]


chroot /mnt/boot-sav/sda5 efibootmgr -v
BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 2002,0000,2001,2004
Boot0000* ubuntu	HD(2,f9d000,f9c800,23a60800)File(EFIubuntushimx64.efi)RC
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050	BIOS(2,500,11)................-.N.......N.A.N.............................................A.........................
Boot0002* Internal CD/DVD ROM Drive	BIOS(3,500,496e7465726e616c2043442f44564420524f4d20447269766500)................-.U.......U.A.U.............................................A.........................
Boot0003* Internal CD/DVD ROM Drive (UEFI)	ACPI(a0341d0,0)PCI(1f,2)03120a00010000000000CD-ROM(1,5dfd3,1100)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3000* Internal Hard Disk or Solid State Disk	RC


chroot /mnt/boot-sav/sda5 uname -r
Kernel: 3.13.0-32-generic


Reinstall the grub-efi of sda5
grub-install : BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 2002,2001,2004
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050
Boot0002* Internal CD/DVD ROM Drive
Boot0003* Internal CD/DVD ROM Drive (UEFI)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot3000* Internal Hard Disk or Solid State Disk
BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 0000,2002,2001,2004
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050
Boot0002* Internal CD/DVD ROM Drive
Boot0003* Internal CD/DVD ROM Drive (UEFI)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot3000* Internal Hard Disk or Solid State Disk
Boot0000* ubuntu
Installation finished. No error reported.
exit code of grub-install :0


chroot /mnt/boot-sav/sda5 efibootmgr -v
BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 0000,2002,2001,2004
Boot0000* ubuntu	HD(2,f9d000,f9c800,fd500800)File(EFIubuntushimx64.efi)
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050	BIOS(2,500,11)................-.N.......N.A.N.............................................A.........................
Boot0002* Internal CD/DVD ROM Drive	BIOS(3,500,496e7465726e616c2043442f44564420524f4d20447269766500)................-.U.......U.A.U.............................................A.........................
Boot0003* Internal CD/DVD ROM Drive (UEFI)	ACPI(a0341d0,0)PCI(1f,2)03120a00010000000000CD-ROM(1,5dfd3,1100)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3000* Internal Hard Disk or Solid State Disk	RC


chroot /mnt/boot-sav/sda5 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.bin
Found FreeDOS on /dev/sda1
Found FreeDOS on /dev/sda2
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.


pastebinit  packages needed
W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)


E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.5 LTS _Precise Pangolin_ - Release amd64 (20140807.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.5%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140807.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.5 LTS _Precise Pangolin_ - Release amd64 (20140807.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.5%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20140807.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/configobj/python-configobj_4.7.2+ds-3build1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/configobj/python-configobj_4.7.2+ds-3build1_all.deb)  Something wicked happened resolving 'id.domain-error.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/p/pastebinit/pastebinit_1.3-2ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/p/pastebinit/pastebinit_1.3-2ubuntu2_all.deb)  Something wicked happened resolving ':http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Could not install pastebinit
Please install the [pastebinit ] packages.  Then try again.
```


Thanks

~a

---

### Post by oldfred on 2016-03-05
It looks like you installed in UEFI boot mode on MBR partitioned drive. That may work, but gpt is the UEFI standard. 

But HP is not friendly with any system other than Windows for UEFI boot. They violate UEFI spec that says not to use description in UEFI to boot and they only allow "Windows" to boot. Threre are multiple work arounds depending on whether dual booting or just using Ubuntu.

If just Ubuntu, we change description in UEFI of ubuntu to Windows and it then works as it sees description it wants, but boots grub/shim into Ubuntu which we want.

       
 **d1**:  If Description has to be Windows then change UEFI description. 
 	sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

If dual booting we create the fallback or hard drive boot entry that all systems must allow. That is /EFI/Boot/bootx64.efi and we make it really be shimx64.efi renamed to bootx64.efi. I normally create this anyway just to have another entry in UEFI. Details in link below in my signature.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file"]http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file"]
[/URL]

---

### Post by vidtek on 2016-03-05
> **amol7 said:**
> So just doing that would solve the problem? Or is other any other problem. Like has this problem (no booting Ubuntu) got anything to do with UEFI / Legacy mode?

Thanks

~a
You'll find that boot-rescue will sort out those problems, it really is an excellent tool.  You will need to ensure your bios is set to non-secure boot.  It'll be somewhere in the bios settings, every damn one is different, you'll need to hunt for that setting.
Tony

---

### Post by amol7 on 2016-03-05
> **oldfred said:**
> It looks like you installed in UEFI boot mode on MBR partitioned drive. That may work, but gpt is the UEFI standard. 

But HP is not friendly with any system other than Windows for UEFI boot. They violate UEFI spec that says not to use description in UEFI to boot and they only allow "Windows" to boot. Threre are multiple work arounds depending on whether dual booting or just using Ubuntu.

If just Ubuntu, we change description in UEFI of ubuntu to Windows and it then works as it sees description it wants, but boots grub/shim into Ubuntu which we want.

       
 **d1**:  If Description has to be Windows then change UEFI description. 
     sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

If dual booting we create the fallback or hard drive boot entry that all systems must allow. That is /EFI/Boot/bootx64.efi and we make it really be shimx64.efi renamed to bootx64.efi. I normally create this anyway just to have another entry in UEFI. Details in link below in my signature.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file"]http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file"]
[/URL]


Sorry I really don't understand what you said:(:confused:

Can you please tell ,me what to do?

Thanks
~ a

---

### Post by ajgreeny on 2016-03-05
Is this really Ubuntu 12.04.5 that you installed?  You might have done better with 14.04, which my understanding of is that it handles UEFI better then the previous versions of Ubuntu.

However, as oldfred has already answered I will defer to him and leave you in his capable care; he knows a great deal more than I do about UEFI vs MBR, and will, think, help you better than anyone else can.

---

### Post by vidtek on 2016-03-05
> **amol7 said:**
> Sorry I really don't understand what you said:(:confused:

Can you please tell ,me what to do?

Thanks
~ a

A-

I must admit the posting from oldfred looks pretty daunting to me too.
Anyway, you have secure boot switched off in your bios, so that's one problem sorted.
```
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)
```

From your boot-repair printout.

It seems you have an EFI partition created by the original Windaz install at                      
/dev/sda1
You have the protected windows partition at
/dev/sda2        these are both very small about 100mb

You have your Windows installation at
/dev/sda3

You have your linux root (all operating system files)partition / at                                     
/dev/sda5

You have your linux swap partition at                                                                            
/dev/sda6

You have your /home partition at                                                                                  
/dev/sda7

There is no /dev/sda4  probably because your windaz is on an extended partition.

If you can get your head around these locations, you are well on your way to understanding the layout of your hdd.

The mix with UEFI and the old MBR is where your problem lies.  OldFred is better qualified than I to guide you through that.
Carefully go through his post and go to and read all the links he's posted. 
It's pretty heavy going, take your time, give yourself a couple of days to get a handle on it and you will eventually understand it.

The thing is, everyone here has different levels of knowledge and expertise, but all are willing to assist newbies, but only if they show they are prepared to help themselves.  Don't expect someone to talk you dumbly through the way to get it working, you will never learn anything that way, and you will pretty much alienate everyone if you don't try and work stuff out for yourself too.   There is no such thing as a dumb question, don't be embarrassed to ask.

Cheers, Tony.

---

### Post by oldfred on 2016-03-05
If it were me, I would back up all data you want to save, which you should have already done as backups are always required.
And erase drive, convert to gpt with ESP - efi system partition which is FAT32 with boot flag, / (root), /home & swap partitions and install 14.04.4. Newer hardware needs newer UEFI. 
And check that you have latest UEFI/BIOS from HP as vendors also are updating to fix UEFI issues.

But if you just want to get system working, this may work. Only issue I do not know about is UEFI on MBR. The installer often is on a single FAT32 ESP with MBR. But some UEFI have to have gpt as that is the real standard.

Did you try this from live installer and see if 'Windows' entry boots Ubuntu?
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You may have to press escape right after or end of UEFI screen to get grub menu. With one install, grub menu is not normally shown.

---

### Post by amol7 on 2016-03-05
> **oldfred said:**
> If it were me, I would back up all data you want to save, which you should have already done as backups are always required.
And erase drive, convert to gpt with ESP - efi system partition which is FAT32 with boot flag, / (root), /home & swap partitions and install 14.04.4. Newer hardware needs newer UEFI. 
And check that you have latest UEFI/BIOS from HP as vendors also are updating to fix UEFI issues.

But if you just want to get system working, this may work. Only issue I do not know about is UEFI on MBR. The installer often is on a single FAT32 ESP with MBR. But some UEFI have to have gpt as that is the real standard.

Did you try this from live installer and see if 'Windows' entry boots Ubuntu?
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You may have to press escape right after or end of UEFI screen to get grub menu. With one install, grub menu is not normally shown.

Oldfred, you have been truely forthcoming. Although I don't think I'm worth this much knowledge.
Thank You though

Ok I just want the system working. Sorry, but I'm just an End User.
So for that will " sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" work?

Or what else can I do? To get it do just start working?

Thanks
~a

---

### Post by amol7 on 2016-03-05
> **oldfred said:**
> If it were me, I would back up all data you want to save, which you should have already done as backups are always required.
And erase drive, convert to gpt with ESP - efi system partition which is FAT32 with boot flag, / (root), /home & swap partitions and install 14.04.4. Newer hardware needs newer UEFI. 
And check that you have latest UEFI/BIOS from HP as vendors also are updating to fix UEFI issues.

But if you just want to get system working, this may work. Only issue I do not know about is UEFI on MBR. The installer often is on a single FAT32 ESP with MBR. But some UEFI have to have gpt as that is the real standard.

Did you try this from live installer and see if 'Windows' entry boots Ubuntu?
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You may have to press escape right after or end of UEFI screen to get grub menu. With one install, grub menu is not normally shown.

OK I tried this code, sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

So i restarted the system and yet nothing.
Of course I'm not sure what I should do next.....

Please guide me

Thank You

~a

**EDIT1**: I do not get  a UEFI screen. All I get is 'Press Esc to get Startup options" and they if the CD is in then, it boots from the Live CD or if there's isn't one, goes to 'FreeDOS and HP Documents option.
[B]
EDIT2[/B]: I do not have any OS installed. Fresh NEW machine with FreeDOS. _**No**_ Windows at all

---

### Post by oldfred on 2016-03-05
In UEFI do you now have a "Windows" entry?
And are you now choosing that to boot in UEFI mode. You must have UEFI on, and CSM/BIOS/Legacy off.

Or from live installer post this to see if new "Windows" entry is there.
sudo efibootmgr -v

---

### Post by amol7 on 2016-03-05
> **oldfred said:**
> In UEFI do you now have a "Windows" entry?
And are you now choosing that to boot in UEFI mode. You must have UEFI on, and CSM/BIOS/Legacy off.

Or from live installer post this to see if new "Windows" entry is there.
sudo efibootmgr -v


Here are a few screen shots of whats happening.

The commands don't exist as per the Live CD terminal session (Live DVD of 12.04.5)
And UEFI Mode is always ON I think (No feature to disable it) I can only turn off Legacy mode (Disable it)
Gonna try with 14.04.03 now.

Thanks

~a

---

### Post by amol7 on 2016-03-06
> **oldfred said:**
> In UEFI do you now have a "Windows" entry?
And are you now choosing that to boot in UEFI mode. You must have UEFI on, and CSM/BIOS/Legacy off.

Or from live installer post this to see if new "Windows" entry is there.
sudo efibootmgr -v


OK Live DVD of 14.04 also doesn't work. It gives the same reply as the one above.
Ok now please find attached the folder structure of the Installation and what was already existing. Also, the partitions. Don;t know how this could help.

Thanks

~a

---

### Post by amol7 on 2016-03-06
> **oldfred said:**
> In UEFI do you now have a "Windows" entry?
And are you now choosing that to boot in UEFI mode. You must have UEFI on, and CSM/BIOS/Legacy off.

Or from live installer post this to see if new "Windows" entry is there.
sudo efibootmgr -v

Ok Oldfred, now I got what you told, I guess you meant running the code to check "Windows Entry" was when I had installed Boot-Repair after the download.
Ok!

So I reinstalled Boot-repair, and the first thing I did was to run the code"sudo efibootmgr -v" and the result of that is the first screen shot.
I then ran the other code "sudo efibootmgr -c -L "Windows Boot Manger" -l "\EFI\ubuntu\shimx64.efi" and the result of that is the that is the second screen shot.
I then restarted the system and no, back to booting the FreeDOS and HP Documents screen :confused:

[B]EDIT : I then switched off Legacy in the BIOS settings and restarted the system and the result is as in the third screen shot (or which ever has the black screen that says "Boot Device not found"


[/B]How should I proceed?

Thanks

~a

PS: I did refer "https://help.ubuntu.com/community/UEFI" and the settings are spot on as described in the link. I've made no changes.

---

### Post by oldfred on 2016-03-06
Is ESP - efi system partition not sda1? The command to add Windows entry defaults to sda1 and you have to add extra parameters to tell it a different partition (or different drive).
 Best to see all details on where you are at now.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by amol7 on 2016-03-06
> **oldfred said:**
> Is ESP - efi system partition not sda1? The command to add Windows entry defaults to sda1 and you have to add extra parameters to tell it a different partition (or different drive).
 Best to see all details on where you are at now.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


Here's the link
[http://paste.ubuntu.com/15308964/](http://paste.ubuntu.com/15308964/)

Thanks

~a

---

### Post by oldfred on 2016-03-06
Your ESP is sda2. So you need the extra  -p 2 for second partition.

       	sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\ubuntu\shimx64.efi"

---

### Post by amol7 on 2016-03-06
> **oldfred said:**
> Your ESP is sda2. So you need the extra  -p 2 for second partition.

           sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\ubuntu\shimx64.efi"

Ok I've done that.
Then what ? Do I restart it or do I do something else?

Thanks

~a
**EDIT: [http://paste.ubuntu.com/15310280/](http://paste.ubuntu.com/15310280/)**

---

### Post by oldfred on 2016-03-06
Did entry show up?
sudo efibootmgr -v

And does it look like the default Ubuntu entry but with "Windows Boot Manager" description?

Then you should be able to reboot and in UEFI or one time boot key boot Windows entry. Be sure UEFI is on.

---

### Post by amol7 on 2016-03-06
> **oldfred said:**
> Did entry show up?
sudo efibootmgr -v

And does it look like the default Ubuntu entry but with "Windows Boot Manager" description?

Then you should be able to reboot and in UEFI or one time boot key boot Windows entry. Be sure UEFI is on.


Well did you take a look at the "Create BootInfo summary report" ?
I did a restart but it doesn't work. Still boots to FreeDOS.

I do not get any other screen after re-starting.

Thanks

~a

**EDIT: I ran the code "sudo efibootmgr -v" and no it doesn't show up anywhere as Windows Boot Manager**

---

### Post by oldfred on 2016-03-07
I need to see commands you ran.
Be sure to boot live installer in UEFI mode.

Rerun these, copy terminal commands and post here in code tags.
Code tags are easy to add with forum advanced editor and # icon.
```
sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\ubuntu\shimx64.efi"
sudo efibootmgr -v


```

---

### Post by amol7 on 2016-03-07
> **oldfred said:**
> I need to see commands you ran.
Be sure to boot live installer in UEFI mode.

Rerun these, copy terminal commands and post here in code tags.
Code tags are easy to add with forum advanced editor and # icon.
```
sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\ubuntu\shimx64.efi"
sudo efibootmgr -v


```

Oldfred. my machine runs on UEFI mode by default. And there is no option to disable it.

Here's the code I ran...

```
ubuntu@ubuntu:~$ sudo efibootmgr -c -L "Windows Boot Manager" -p 2 -l "\EFI\ubuntu\shimx64.efi"
BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 0004,0000,2002,2001,2004
Boot0000* ubuntu
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050
Boot0002* Internal CD/DVD ROM Drive
Boot0003* Internal CD/DVD ROM Drive (UEFI)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot3000* Internal Hard Disk or Solid State Disk
Boot0004* Windows Boot Manager
ubuntu@ubuntu:~$ sudo efibootmgr -v
4BootCurrent: 0003
Timeout: 10 seconds
BootOrder: 0004,0000,2002,2001,2004
Boot0000* ubuntu    HD(2,f9d000,f9c800,d2db0800)File(\EFI\ubuntu\shimx64.efi)RC
Boot0001* Notebook Hard Drive - TOSHIBA MQ01ABF050    BIOS(2,500,4e6f7465626f6f6b2048617264204472697665202d20544f5348494241204d51303141424630353000)................-.N.......N.A.N...................................v.........A.........................
Boot0002* Internal CD/DVD ROM Drive    BIOS(3,500,496e7465726e616c2043442f44564420524f4d20447269766500)................-.U.......U.A.U.............................................A.........................
Boot0003* Internal CD/DVD ROM Drive (UEFI)    ACPI(a0341d0,0)PCI(1f,2)03120a00010000000000CD-ROM(1,5dfd3,1100)RC
Boot0004* Windows Boot Manager    HD(2,f9d000,f9c800,d2db0800)File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC


```

here's info from Boot-info after the above code
[http://paste.ubuntu.com/15325408/](http://paste.ubuntu.com/15325408/)

---

### Post by oldfred on 2016-03-08
If this entry does not work from UEFI or one time boot key then something about using MBR with UEFI must be issue.

Boot0004* Windows Boot Manager    HD(2,f9d000,f9c800,d2db0800)File(\EFI\ubuntu\shimx64.efi)

Converting to or from GPT[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
http://www.rodsbooks.com/gdisk/mbr2gpt.html[/URL]
gdisk to convert from gpt to MBR[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr"]
http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr[/URL]

---

### Post by amol7 on 2016-03-08
> **oldfred said:**
> If this entry does not work from UEFI or one time boot key then something about using MBR with UEFI must be issue.

Boot0004* Windows Boot Manager    HD(2,f9d000,f9c800,d2db0800)File(\EFI\ubuntu\shimx64.efi)

Converting to or from GPT[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
http://www.rodsbooks.com/gdisk/mbr2gpt.html[/URL]
gdisk to convert from gpt to MBR[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr"]
http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr[/URL]


oh ok.
I think I will just go ahead and remove FreeDOS. 
So if I reinstall Ubuntu, 14.04 this time, will it solve the issue?
Or how am I supposed to go ahead with that?

Thanks

~a

---

### Post by oldfred on 2016-03-09
Since install looks ok, I might first just try converting partitions to gpt with gdisk.

And backup all your data.

If installing in UEFI mode, best to review link below in my signature. But it is a lot and we can help you.
Just be sure to boot live installer flash drive in UEFI mode. How you boot installer UEFI or BIOS is then how it installs.

You can just install from an UEFI boot of installer and get gpt partitioning with ESP (FAT32), / (root -ext4) and swap.
But often better to add /home or /mnt/data or other partitions, but that depends on each user and what he wants.

I do prefer to partition in advance with gparted.
        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 


 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by amol7 on 2016-03-10
> **oldfred said:**
> Since install looks ok, I might first just try converting partitions to gpt with gdisk.

And backup all your data.

If installing in UEFI mode, best to review link below in my signature. But it is a lot and we can help you.
Just be sure to boot live installer flash drive in UEFI mode. How you boot installer UEFI or BIOS is then how it installs.

You can just install from an UEFI boot of installer and get gpt partitioning with ESP (FAT32), / (root -ext4) and swap.
But often better to add /home or /mnt/data or other partitions, but that depends on each user and what he wants.

I do prefer to partition in advance with gparted.
        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 


 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

that's just about it for me Oldfred.
I went ahead and installed 14.04.03 using the option "Erase entire disk"
Now it runs.

I know I could have gone ahead wit your guidelines and your support but I kinda needed a system immeadiately. So had to take a final call.

Oldfred, thanks so much for your support and time.

Best Regards,

~a

---

### Post by oldfred on 2016-03-10
Whatever works best for you. Glad its working. :)

---

