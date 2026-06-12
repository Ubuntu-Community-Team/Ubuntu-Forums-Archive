---
title: "Upgrade to 11.04 corrupted GRUB Loader"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by jecook on 2011-05-03
[FONT=Arial]I am a new LINUX user who had initially installed UNR 10.10 on a separate partition of my Acer One Netbook (Win XP) with a dual boot. An initial problem with the location of the Boot loader I had a setup which I was slowly getting used to. Last weekend I was given the option to update to the new 11.04 version.

I accepted the offer and let the update system do it's job overnight, final booting into UNR 11.04 after about 18 hours. The first job was to get into the basic desktop as I do not find Unity very helpful and on a netbook it takes up too much space. Once I the update was completed and my desktop was setup I needed to shutdown in order to do some work which required booting to Windows XP. I did not use Ubuntu again until this morning when I got to the office booted my computer up and was faced with the message, 

error: symbol not found: 'grub_env_export'
grub rescue>

As a new user the message meant very little to me although clearly there was a GRUB bootloader problem. I did think that perhaps the words 'grub rescue' implied there was some simple command which would restore the boot loader but a search of the internet and Ubunti Forums showed not only that the solution was less than trivial for a newbie like myself, but that I was also not alone in having problems with the 11.04 upgrade. That was a very disappointing discovery as I had been impressed with UNR 10.10 despite a few issues with networking, printers and one invisible partition!

I tried to follow some of the instructions at this URL which I obtained from another forum post 
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

I used a bootable USB version of 10.10 to have a look at the problems and I tried to follow the instructions but I find it very confusing to know which partitions are which and what is the 'normal' system disk or where the boot loader resides. With my working UNR 10.10 version the internal partitions were /dev/sdaX whereas with the Bootable USB system they are sdbX so which do I use sda or sdb? I could mount the partitions with the disk utility but then when it came to following the instructions to mount the critical virtual file systems I had errors saying no such mount point which completely flummoxed me.

I eventually solved the problem by using Paragon Rescue Kit to restore the WinXP boot loader, but that means I can not boot into LINUX of course. 

I appreciate how helpful the community is but I do find that LINUX does have a lot of 'hard to understand' command line instructions despite the fact that I started working with computers many years ago (IBM 360/44s!)   since then I have worked with numerous operating systems including CP/M, MS-DOS, VMS, UNIX before having my IT brain scrambled by numerous flavours of W-----s! I had hoped to slowly move over to LINUX but this episode has been very disappointing.

In order to get my UNR 11.04 system working again I guess I have two options,
1)
I could use the UNR10.10 Bootable USB key to re-install the GRUB Loader, or

2)
I can Download UNR 11.04 and make another bootable USB with 11.04 and then use that to install the latest 11.04 update. 

My concern is that I don't know why the original GRUB was corrupted so either of these two solutions could end up with a repeat of the same problem.

Canonical have done a good job to make LINUX more user friendly but I have found this episode very disappointing as it is just the sort of thing that will put off the average Windows user who will simply return to the environment they know.

I am still keen to persevere with UBUNTU but I could do with some hand-holding to get a workable 11.04 dual boot system working.

Jon 


[/FONT]

---

### Post by jecook on 2011-05-08
There seem to be quite a lot of problems with GRUB when upgrading from 10.10 to 11.04! In my case I Downloaded 11.04 iso and created a new USB from which I re-installed as a clean installation. I thought this had cured the problem but it then re-occurred. I then removed the external USB disk and rebooted with no problem - maybe this is the cause? I will see if it remains stable bit it is a bit annoying as 10.10 booted fine with or without the ext USB disk.

Results from Boot info script below:

[QUOTE][                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for cadc4.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
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

/dev/sda1               2,048    16,779,263    16,777,216  12 Compaq diagnostics
/dev/sda2    *     16,779,264   148,344,209   131,564,946   7 HPFS/NTFS
/dev/sda3         148,344,210   271,434,239   123,090,030   7 HPFS/NTFS
/dev/sda4         271,435,774   312,580,095    41,144,322   5 Extended
/dev/sda5         308,389,888   312,580,095     4,190,208  82 Linux swap / Solaris
/dev/sda6         271,435,776   304,218,111    32,782,336  83 Linux
/dev/sda7         304,220,160   308,383,743     4,163,584  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   195,639,569   195,639,507   7 HPFS/NTFS
/dev/sdb2         195,639,570   976,768,064   781,128,495   f W95 Ext d (LBA)
/dev/sdb5         195,639,633   390,925,709   195,286,077   7 HPFS/NTFS
/dev/sdb6         390,925,773   586,211,849   195,286,077   7 HPFS/NTFS
/dev/sdb7         586,211,913   781,497,989   195,286,077   7 HPFS/NTFS
/dev/sdb8         781,498,053   976,768,064   195,270,012   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D8444E9A444E7B70                       ntfs       PQSERVICE                     
/dev/sda2        A47AC1277AC0F758                       ntfs       ACER                          
/dev/sda3        01CBE628E0814680                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2e6459fd-75d2-4fd2-9bcf-3ab4e9001715   swap                                     
/dev/sda6        16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf   ext4                                     
/dev/sda7        88dbd040-66ec-49fe-9aec-1a2920dcff7f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1C5C6AFB5C6ACF58                       ntfs       APOLLO                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4A22AB1422AB0453                       ntfs       APOLLO Music                  
/dev/sdb6        01CBF6C3DEF03190                       ntfs       APOLLO Seismic                
/dev/sdb7        7AF6DC35F6DBEEFF                       ntfs       APOLLO Reports                
/dev/sdb8        30DE0128DE00E7C4                       ntfs       APOLLO Backups                
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/APOLLO            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/APOLLO Music      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/APOLLO Reports    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/APOLLO Seismic    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/APOLLO Backups    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 16b44e0b-f9d6-4b19-9e0b-e6bbc5aa58cf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root D8444E9A444E7B70
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root A47AC1277AC0F758
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=88dbd040-66ec-49fe-9aec-1a2920dcff7f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 150.5GB: boot/grub/core.img
 150.6GB: boot/grub/grub.cfg
 142.2GB: boot/initrd.img-2.6.38-8-generic
 150.6GB: boot/vmlinuz-2.6.38-8-generic
 142.2GB: initrd.img
 150.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 61  |...............a|
000001c0  e6 fe 82 ca ef fe 02 e0  33 02 00 f0 3f 00 00 fe  |........3...?...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 38 f4 01 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

/QUOTE]

Jon

---

### Post by Quackers on 2011-05-08
I would suggest that you purge then re-install grub2 to the mbr of /dev/sda using the chroot section of drs305's guide below.
The live usb you should use is the 11.04 one.
The partition to be mounted is /dev/sda6 and grub should be installed to /dev/sda - not to a partition (like /dev/sda6)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

It will look a bit daunting, but it's not as bad as it looks. Most of the work is done already by drs305. Take your time and if there is something that you don't understand, just ask.

---

### Post by jecook on 2011-05-08
Having re-installed 11.04 from the Live USB, the basic problem seemed to have been fixed but then I had another Grub Rescue episode, which occurred when my external USB drive was installed. Removing the external drive and rebooting brought the GRUB menu back. This set me thinking and I then had a look at the BIOS boot order, which showed the external HD booting before the internal drive, by changing the order to get the internal drive to boot first I now get the GRUB menu again so maybe my problem is solved.

After reading Quackers response I had a look at the results from the Boot Sys Info script where it says:

>  =>Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for cadc4.

It seems that Grub 2 is installed twice one of which is in /dev/sda as recommended by Quackers and one in /dev/sdb which is the external USB drive.

Does this mean that I should try to remove the Grub 2 that is installed in /dev/sdb?

I just ask as I don't want to start following the instructions in

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

if it is not necessary.

Thanks

---

### Post by Quackers on 2011-05-08
Why would /dev/sdb be set to boot first? There is no operating system on sdb.
/dev/sda should be set to boot first and grub should be in its mbr.
Presumably at some time you have installed grub to the mbr of /dev/sdb - it didn't grow there :-)
It's not doing any harm there though.
It should be fine as it is now. No need to change grub now :-)

---

### Post by jecook on 2011-05-10
Thanks Quackers,
                          I think the grub in /dev/sdb may have been due to earlier attempts to fix Ubuntu 10.10 original installation, when /dev/sdb was the original live USB stick, a newbie mistake (or perhaps a wrinkly, having once been used to UNIX systems!!! :))

Having sorted out the boot order of the various drives on this netbook the installation seems to be fairly stable now so I can get back to [re]figuring out LINUX.

Cheers,
Jon

---

### Post by Quackers on 2011-05-10
Excellent! :-) Enjoy!

---

