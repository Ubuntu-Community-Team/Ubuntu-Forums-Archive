---
title: "Initial reboot after installation never happens?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by willdenham on 2011-02-27
I'm trying to install the latest release of Ubuntu from the official site, 10.10.

I downloaded the 64-bit edition first to install. After burning it to a CD, it launches in my PC just fine and lets me go through the install process. I'm letting Ubuntu use up the whole HDD, so no special options are being chosen during the install. At the end of the installation, it asks me to restart and I hit OK, it closes out of the box and leaves me looking at the default background... forever.

Thinking I did something wrong, I tried again, but this time left the box to download updates and install 3-rd party software unchecked. Same thing as above, it appeared to install just fine but hung after I tell it to reboot.

Lastly, I downloaded the 32 bit edition to try, and it gives me the same error.

If I hard restart my machine after waiting on the background image for a while, it will not boot when it comes back up. My PC just remains at a screen after the BIOS acting like it's searching for bootable media.

I'll be honest that I haven't waited for over 15 minutes for it to restart. But should it really take that long?

Any insight will be helpful.

---

### Post by Rubi1200 on 2011-02-27
Hi and welcome to the forums :-)

What are the full specifications for the computer?

From the LiveCD, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by willdenham on 2011-02-27
Thanks for the reply, here are the results. Please note it's drive sdf that I'm trying to install to.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 68. But according to the info from fdisk, 
                       sda7 starts at sector 1048610813.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       1250258943 sectors, but according to the info from 
                       fdisk, it has 1250261616 sectors.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *         16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sda5              16,128   629,169,659   629,153,532   7 HPFS/NTFS
/dev/sda6         629,169,723 1,048,610,744   419,441,022   7 HPFS/NTFS
/dev/sda7       1,048,610,813 1,953,520,064   904,909,252   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 3,907,024,895 3,907,022,848   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,250,261,679 1,250,261,617  42 SFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd2    *         16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdd5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048   281,063,423   281,061,376  83 Linux
/dev/sdf2         281,065,470   293,046,271    11,980,802   5 Extended
/dev/sdf5         281,065,472   293,046,271    11,980,800  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        FDF1961524B39619                       ntfs       Torrent Downloads             
/dev/sda6        07C39F09867639A9                       ntfs       Games & Programs              
/dev/sda7        AEF79549DBA78B9F                       ntfs       Full DVD Images               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C40C0D000C0CEEEC                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        82A2F8A9A2F8A339                       ntfs       Downloads                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        39C1202217A014B8                       ntfs       Blu Ray                       
/dev/sdd: PTTYPE="dos" 
/dev/sde1        42F04B62F04B5AF5                       ntfs                                     
/dev/sde                                                promise_fasttrack_raid_member                               
/dev/sdf1        c8f68fd7-2728-41a0-928e-1b43e855f91a   ext4                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        6af35934-7824-435e-a313-b379f85ef9af   swap                                     
/dev/sdf: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd5        /media/Blu Ray           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde1        /media/42F04B62F04B5AF5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/Torrent Downloads fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/Games & Programs  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/Full DVD Images   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdf1/boot/grub/grub.cfg: ===========================

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
set root='(hd6,msdos1)'
search --no-floppy --fs-uuid --set c8f68fd7-2728-41a0-928e-1b43e855f91a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd6,msdos1)'
search --no-floppy --fs-uuid --set c8f68fd7-2728-41a0-928e-1b43e855f91a
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
    set root='(hd6,msdos1)'
    search --no-floppy --fs-uuid --set c8f68fd7-2728-41a0-928e-1b43e855f91a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c8f68fd7-2728-41a0-928e-1b43e855f91a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd6,msdos1)'
    search --no-floppy --fs-uuid --set c8f68fd7-2728-41a0-928e-1b43e855f91a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c8f68fd7-2728-41a0-928e-1b43e855f91a ro single 
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
    set root='(hd6,msdos1)'
    search --no-floppy --fs-uuid --set c8f68fd7-2728-41a0-928e-1b43e855f91a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd6,msdos1)'
    search --no-floppy --fs-uuid --set c8f68fd7-2728-41a0-928e-1b43e855f91a
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

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdg1 during installation
UUID=c8f68fd7-2728-41a0-928e-1b43e855f91a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdg5 during installation
UUID=6af35934-7824-435e-a313-b379f85ef9af none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdf1: Location of files loaded by Grub: ===================


  90.3GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  30.3GB: boot/initrd.img-2.6.35-22-generic
  90.3GB: boot/vmlinuz-2.6.35-22-generic
  30.3GB: initrd.img
  90.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf2

00000000  fe 26 4b 05 88 08 00 00  33 41 50 f2 32 00 00 00  |.&K.....3AP.2...|
00000010  83 cf 45 42 01 00 00 00  30 f3 41 c1 00 00 00 00  |..EB....0.A.....|
00000020  41 a8 e0 5c 00 00 00 00  b5 56 8d 87 b1 08 00 00  |A..\.....V......|
00000030  84 64 a8 a0 b4 08 00 00  a5 f8 df 56 06 00 00 00  |.d.........V....|
00000040  51 6b 08 4c 00 00 00 00  9c 93 34 1f 00 00 00 00  |Qk.L......4.....|
00000050  29 a9 9e 5a 00 00 00 00  1d 40 01 d6 79 08 00 00  |)..Z.....@..y...|
00000060  87 58 c4 f9 9d 08 00 00  9a f9 b0 fd 1c 00 00 00  |.X..............|
00000070  c7 d5 5c 00 00 00 00 00  e0 d0 bb 44 00 00 00 00  |..\........D....|
00000080  c7 29 ec 5d 00 00 00 00  d4 92 d0 cb b8 08 00 00  |.).]............|
00000090  42 69 da 7f ba 08 00 00  d7 dd 87 77 00 00 00 00  |Bi.........w....|
000000a0  5a 58 4c a3 00 00 00 00  66 4e 3e 3e 00 00 00 00  |ZXL.....fN>>....|
000000b0  50 b4 37 5b 00 00 00 00  e3 b5 0b 5b 5c 08 00 00  |P.7[.......[\...|
000000c0  28 6e 29 1f 94 08 00 00  e9 cd 25 d8 26 00 00 00  |(n).......%.&...|
000000d0  bf 7d 5f 8d 1b 00 00 00  b4 3c 4c 87 08 00 00 00  |.}_......<L.....|
000000e0  12 6f 2a 6d 00 00 00 00  07 41 0c 4e b6 08 00 00  |.o*m.....A.N....|
000000f0  cc ab be f0 b7 08 00 00  dc 23 7b 06 03 00 00 00  |.........#{.....|
00000100  07 8f 56 03 00 00 00 00  8b 75 c1 05 00 00 00 00  |..V......u......|
00000110  33 ee 33 5b 00 00 00 00  52 4e 6b 7a 00 00 00 88  |3.3[....RNkz....|
00000120  8f 1a fb 89 5b 08 00 00  4d f0 fa 4e 8d 08 00 00  |....[...M..N....|
00000130  33 09 41 aa 2d 00 00 00  b4 d8 15 ee 0f 00 00 00  |3.A.-...........|
00000140  14 a8 f4 f3 0d 00 00 00  71 f5 5d 70 00 00 00 00  |........q.]p....|
00000150  90 65 5f cc b8 08 00 00  e1 28 e1 e9 b9 08 00 00  |.e_......(......|
00000160  39 5c 00 0f 01 00 00 00  c3 e5 6a 0d 00 00 00 00  |9\........j.....|
00000170  05 36 7c 07 00 00 00 00  07 9b aa 5a 00 00 00 00  |.6|........Z....|
00000180  b7 d0 12 84 69 08 00 00  df 38 7e 06 88 08 00 00  |....i....8~.....|
00000190  33 41 50 f2 32 00 00 00  83 cf 45 42 01 00 00 00  |3AP.2.....EB....|
000001a0  30 f3 41 c1 00 00 00 00  c1 b1 e0 5c 00 00 00 00  |0.A........\....|
000001b0  96 68 c0 88 b1 08 00 00  65 76 db a1 b4 08 00 fe  |.h......ev......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 b6 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Rubi1200 on 2011-02-27
Which drive is currently set as first boot device?

What happens if you choose sda as first device?

---

### Post by willdenham on 2011-02-27
sdf is set as the primary boot device in the BIOS, I've even tried removing all the other HDD's off my boot order. 

It will run through the initial BIOS loading screen, check through my drives and then just halt after that, as if it's hunting for something to boot to. 

I'll go set SDA to my primary and try to boot that. Not sure why the bootloader installed to SDA when I wanted everything on SDF. I can try that though. I'll post back if it doesn't work. 

Thanks again.

---

### Post by kansasnoob on 2011-02-27
By default grub installs to the MBR of "sda" as it did here:

> => [B]Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.[/B]
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf

Which drive is set to boot first in BIOS?

---

### Post by YesWeCan on 2011-02-27
Your linux bootloader, Grub, is installed at the master boot record of sda instead of sdf and looks for Ubuntu on sda.

My advice - disconnect all drives except sdf.
Reinstall Ubuntu 10.10 64 bit from scratch.
After it reboots ok, shut down and reconnect all the other drives.
Then reboot from sdf (or whatever it is now called) back into Ubuntu.
at a console type 'sudo update-grub'
Then reboot off sdf.
You should now get a boot menu listing all your OS'es and you can select which one to boot.

---

### Post by kansasnoob on 2011-02-27
> Not sure why the bootloader installed to SDA when I wanted everything on SDF

Ubuntu has always assumed that sda is the boot device. The ability to do otherwise changed between 10.04 and 10.10. In 10.04 you'd wait until the end of the installation and click on the advanced button here:

[ATTACH]184658[/ATTACH]

With 10.10 you'd only see that option if you chose the manual/advanced partitioning option as I explained here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by kansasnoob on 2011-02-27
> **YesWeCan said:**
> Your linux bootloader, Grub, is installed at the master boot record of sda instead of sdf and looks for Ubuntu on sda.

My advice - disconnect all drives except sdf.
**[COLOR="Red"]Reinstall Ubuntu 10.10 64 bit from scratch.[/COLOR]**
After it reboots ok, shut down and reconnect all the other drives.
Then reboot from sdf (or whatever it is now called) back into Ubuntu.
at a console type 'sudo update-grub'
Then reboot off sdf.
You should now get a boot menu listing all your OS'es and you can select which one to boot.

Reinstalling the OS is total insanity!

This can be fixed with a few very simple commands.

EDIT: It may also be fixed by changing hard drive boot priority!

---

### Post by Rubi1200 on 2011-02-27
@willdenham: I suggest you first try what kansasnoob and I suggested which is to check the boot device priority.

@YesWeCan: no disrespect intended, but kansasnoob is right. In a situation like this the solution is to simply reinstall the bootloader to the MBR of the correct drive. There is no need for a total reinstall of the whole system.

---

### Post by YesWeCan on 2011-02-27
It appears to me that the OP now has the wrong OS installed: 32 bit rather than 10.10 64 bit which is what was originally wanted.

I believe my advice gives a very simple and bomb-proof method of achieving what the OP originally wanted. No messing about. :)

---

