---
title: "Windows Boot Loader to Load Linux"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by SneakPeak on 2011-10-15
Hi,

*Problem solved.  Please see my last post.*

I am trying to setup a windows Ubuntu dual boot (non-standard).  I am following some advice that said that Windows overwrites the boot section when a service pack is installed and creates a mission for you if you want to get your Linux to boot again.  Therefore, I did the following:

I shrank the Windows data partition to create space for Ubuntu

I created a 500 MB boot partition
I created a 20 GB root partition
I created a 300 GB home partition
I created a 20 GB swap partition

I "told" the installer to put grub in the boot partition.  I did the install and everything ran well.

I then rebooted and the machine booted into Windows as normal.  In Windows I have EasyBCD which I am trying to use to boot the Ubuntu OS but for the life of me I cannot figure it out.  When I choose Grub2 in EasyBCD it states that the configuration is done automatically.  When I choose grup I can change a few settings but not much.  I also tried SysLinux but no luck

Any help on getting my Ubuntu to boot?

Thanks

Adrian

---

### Post by SneakPeak on 2011-10-15
I got irritated not making any progress and I killed the Ubuntu installation and reinstalled bog standard.  Install alongside Windows 7.  Still no luck.  The machine boots Windows only!  

I love Linux but this sort of thing just drives me crazy.  I hate wasting time trying to get something to work which should work easily! Aghhhggghhhhgghghghghhg

---

### Post by oldfred on 2011-10-15
If you did the standard install, did you install grub2's boot loader to the MBR of your boot drive usually sda?

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

This also runs the boot script and often repairs the boot also.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

this will often let you boot Ubuntu without the MBR so then you can repair from inside Ubuntu.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by SneakPeak on 2011-10-15
Hi OldFred,

Thanks for the reply.  I tried the ISO boot fix disk.  It ran and said it had repaired things but my machine continues to boot to Windows only.  I ran the boot script and this is the result I got:
(sdb was just the flash drive I was using to boot to linux, I put the iso installation on a usb stick)

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943279 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 387148 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   205,211,647   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda3         205,213,694   945,829,887   740,616,194   f W95 Extended (LBA)
/dev/sda5         935,589,888   945,829,887    10,240,000   7 NTFS / exFAT / HPFS
/dev/sda6         205,213,696   206,188,543       974,848  83 Linux
/dev/sda7         206,190,592   229,625,855    23,435,264  82 Linux swap / Solaris
/dev/sda8         229,627,904   268,687,359    39,059,456  83 Linux
/dev/sda9         268,689,408   935,575,551   666,886,144  83 Linux
/dev/sda4         945,829,888   976,773,167    30,943,280  12 Compaq diagnostics


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        30BCDEC4BCDE83AE                       ntfs       
/dev/sda2        1868E05468E03264                       ntfs       
/dev/sda4        9884E5A384E583DA                       ntfs       LENOVO_PART
/dev/sda5        305AF2785AF239E4                       ntfs       LENOVO
/dev/sda6        9302284d-7e85-4e8e-a2d2-efcac848000a   ext2       
/dev/sda7        b027289c-5160-4701-b1ef-2e473d18ed8c   swap       
/dev/sda8        7c5e4603-90ec-481b-81d4-5fb0c50e9062   ext4       
/dev/sda9        5c2e3b99-f705-459c-9ae2-9e2a6fdc3cce   ext4       
/dev/sdb1        DED9-C74B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/30BCDEC4BCDE83AE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/1868E05468E03264  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/9302284d-7e85-4e8e-a2d2-efcac848000a ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda6/grub/grub.cfg: ==============================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 7c5e4603-90ec-481b-81d4-5fb0c50e9062
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 9302284d-7e85-4e8e-a2d2-efcac848000a
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9302284d-7e85-4e8e-a2d2-efcac848000a
	linux	/vmlinuz-3.0.0-12-generic root=UUID=7c5e4603-90ec-481b-81d4-5fb0c50e9062 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9302284d-7e85-4e8e-a2d2-efcac848000a
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/vmlinuz-3.0.0-12-generic root=UUID=7c5e4603-90ec-481b-81d4-5fb0c50e9062 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9302284d-7e85-4e8e-a2d2-efcac848000a
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9302284d-7e85-4e8e-a2d2-efcac848000a
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 30BCDEC4BCDE83AE
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9884E5A384E583DA
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
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                   57
               =                vmlinuz-3.0.0-12-generic                      20

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=7c5e4603-90ec-481b-81d4-5fb0c50e9062 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=9302284d-7e85-4e8e-a2d2-efcac848000a /boot           ext2    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=5c2e3b99-f705-459c-9ae2-9e2a6fdc3cce /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=b027289c-5160-4701-b1ef-2e473d18ed8c none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
boot_info_script.sh: line 1502: [: 3.96017e+09: integer expression expected


```

---

### Post by oldfred on 2011-10-15
When you ran boot repair did you tell it you had a separate /boot. I normally do not suggest the separate /boot for standard desktops except very old systems, or server type installs that use RAID or LVM.

If fixboot did not work, you can from liveCD or liveUSB install grub2's boot loader to the MBR. You have to be sure to follow directions to include the /boot partition in the mount. Some instructions leave that off (since it is uncommon) or just have a footnote later that you need to follow.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

#If separate /boot & Natty or later
sudo mount /dev/sda8 /mnt
sudo mount /dev/sda6 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by SneakPeak on 2011-10-15
Hi OldFred

Yes I did make a separate /boot partition.  I am trying to install 11.10.

Your last set of instructions, where should I execute that code or where should I copy that to.  Sorry I know this sounds really stupid but you have lost me a bit with your explanation.

Thanks

Adrian

Got to get some sleep.  Will try this tomorrow and update as to success or otherwise.

---

### Post by oldfred on 2011-10-15
Some things are easier with terminal to explain how to do via the forum.

In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal

---

### Post by SneakPeak on 2011-10-16
Thanks OldFred

This worked: 

> **oldfred said:**
> 
#If separate /boot & Natty or later
sudo mount /dev/sda8 /mnt
sudo mount /dev/sda6 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda

If I understand correctly Grug is now in the MBR which means there is a chance it will be overwritten by Windows at some stage?  This is what I was trying to avoid by getting windows to "chainload" grub on a different boot partition.  Nevertheless I am just grateful to be able to boot Linux.  Now onto my next problem.  For whatever reason my wireless won't turn on under Linux.  I am gonig to start searching the forum to solve the new problem.  

Thanks for your help.

SneakPeak

---

### Post by oldfred on 2011-10-16
Glad you got it working.

I think only if Windows does a service pack upgrade or you do a reinstall will it overwrite boot loader.

Make a Windows repairCD and you can then reinstall Windows boot loader, run chkdsk, or make other repairs if you have major Windows issues.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Do not know much about wireless. My portable just works.
Did you install with hard wired Ethernet connect. It usually then offers to download additional drivers.

---

