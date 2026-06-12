---
title: "Vista loader mangled my MBR"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by anypundit on 2011-02-24
I was set up for dual boot into grub2 with the default being Ubuntu, but I could scroll down to Windows 7 loader to load it.  Today, I accidentally selected Windows Vista loader instead, which took me to some sort of recovery console.  I clicked Exit immediately, but when I rebooted, Linux would no longer boot. All I get is grub rescue or grub command prompt, and nothing works in either.  With a Windows recovery disk, I was able to fix the MBR to boot Win7 again, but I've tried everything I've seen in forums to fix or reinstall grub2 using the LiveCD and the grub prompt with no success.  

After 12h, I decided to reinstall, but the installer reports No Operating Systems Found.  My partitions are fine in Disk Utility and Windows.  I can read and write them all.  I just want to reinstall using my existing partitions without destroying them, and to keep a backup of my current "/" partition without disturbing my Win7 parts. I could use the space on the NTFS parts for storage if need be.

I have multiple Linux and NTFS partitions (/boot is separate in Linux), each of which have remained intact, but after the Vista episode, my first partition is PQSERVICE which never used to be called that.

As an aside, I was installing 64 bit Lucid because thats what I've been using and I'm a little wary about dist-upgrading my laptop when I had some problems with Maverick on my desktop.  If it's worth burning a Maverick cd to fix some of this, I'll do it.

---

### Post by Quackers on 2011-02-24
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by anypundit on 2011-02-24
sda5 is my /boot partition, sda6 is my root part, 7 is var and 8 is swap.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    27,278,369    27,278,307   7 HPFS/NTFS
/dev/sda2    *     27,278,370    27,487,214       208,845   7 HPFS/NTFS
/dev/sda3          27,487,215   287,264,783   259,777,569   7 HPFS/NTFS
/dev/sda4         287,264,817   488,408,129   201,143,313   f W95 Ext d (LBA)
/dev/sda5         287,266,816   287,459,327       192,512  83 Linux
/dev/sda6         287,461,376   434,540,543   147,079,168  83 Linux
/dev/sda7         434,546,688   444,405,759     9,859,072  83 Linux
/dev/sda8         444,409,856   446,455,791     2,045,936  82 Linux swap / Solaris
/dev/sda9         446,455,808   488,394,751    41,938,944   7 HPFS/NTFS

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7A48020D4801C8B9                       ntfs       PQSERVICE                     
/dev/sda2        44D0020ED00206C0                       ntfs       SYSTEM RESERVED               
/dev/sda3        AAE80367E80330DD                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4dfc3220-58ad-4827-9b0d-89275333034b   ext3                                     
/dev/sda6        3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec   ext3                                     
/dev/sda7        040e2d39-a80e-4f77-9498-eaf0ae0106ff   ext3                                     
/dev/sda8        7b6f2ed6-7a56-4dfa-aa22-791cbd68052a   swap                                     
/dev/sda9        403EE5523EE54210                       ntfs       Userdata                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

============================= sda5/grub/grub.cfg: =============================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
    linux    /vmlinuz-2.6.32-28-generic root=UUID=3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec ro   quiet splash profile
    initrd    /initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /vmlinuz-2.6.32-28-generic root=UUID=3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
    linux    /vmlinuz-2.6.32-27-generic root=UUID=3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec ro   quiet splash profile
    initrd    /initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /vmlinuz-2.6.32-27-generic root=UUID=3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4dfc3220-58ad-4827-9b0d-89275333034b
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7a48020d4801c8b9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 147.1GB: boot/grub/core.img
 147.1GB: grub/core.img
 147.0GB: grub/grub.cfg
 147.1GB: initrd.img-2.6.32-27-generic
 147.1GB: initrd.img-2.6.32-28-generic
 147.1GB: vmlinuz-2.6.32-27-generic
 147.1GB: vmlinuz-2.6.32-28-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda9 during installation

UUID=3012cf02-2b30-4b78-89e8-5a7b1ddbb8ec /               ext3    errors=remount-ro noatime 0       1


# /boot was on /dev/sda7 during installation

UUID=4dfc3220-58ad-4827-9b0d-89275333034b /boot           ext3    defaults         noatime 0       2


# /var was on /dev/sda8 during installation

UUID=040e2d39-a80e-4f77-9498-eaf0ae0106ff /var            ext3    defaults         noatime 0       2


# swap was on /dev/sda6 during installation

UUID=7b6f2ed6-7a56-4dfa-aa22-791cbd68052a none            swap    sw              0       0



=================== sda6: Location of files loaded by Grub: ===================


 172.1GB: boot/grub/core.img
 172.0GB: boot/vmlinuz-2.6.32-23-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 00 00 00 07 00 00 00  56 65 72 73 69 6f 6e 00  |........Version.|
00000010  c0 ff ff ff 6c 68 05 00  38 b1 c4 02 43 08 c7 da  |....lh..8...C...|
00000020  78 b0 c4 02 75 f5 0f 54  e8 b2 c4 02 1d d7 0f a7  |x...u..T........|
00000030  b8 b3 c4 02 e2 74 85 86  f0 ac c4 02 0d 73 12 51  |.....t.......s.Q|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  f8 ff ff ff 98 b1 c4 02  88 ff ff ff 6e 6b 20 00  |............nk .|
00000060  eb ab df eb 10 08 cb 01  00 00 00 00 60 7d 01 00  |............`}..|
00000070  02 00 00 00 00 00 00 00  c8 b7 c4 02 ff ff ff ff  |................|
00000080  01 00 00 00 28 b5 c4 02  d0 ee 22 01 ff ff ff ff  |....(.....".....|
00000090  0c 00 a0 00 00 00 00 00  00 00 00 00 36 00 00 00  |............6...|
000000a0  00 00 00 00 24 00 00 00  4d 69 63 72 6f 73 6f 66  |....$...Microsof|
000000b0  74 2e 4c 69 76 65 50 68  6f 74 6f 41 63 71 75 69  |t.LivePhotoAcqui|
000000c0  73 69 74 69 6f 6e 57 69  7a 61 72 64 00 00 00 00  |sitionWizard....|
000000d0  e8 ff ff ff 76 6b 00 00  36 00 00 00 e8 b4 c4 02  |....vk..6.......|
000000e0  01 00 00 00 00 00 00 00  c0 ff ff ff 4c 00 69 00  |............L.i.|
000000f0  76 00 65 00 50 00 68 00  6f 00 74 00 6f 00 41 00  |v.e.P.h.o.t.o.A.|
00000100  63 00 71 00 75 00 69 00  73 00 69 00 74 00 69 00  |c.q.u.i.s.i.t.i.|
00000110  6f 00 6e 00 57 00 69 00  7a 00 61 00 72 00 64 00  |o.n.W.i.z.a.r.d.|
00000120  00 00 00 00 00 00 00 00  f8 ff ff ff d0 b4 c4 02  |................|
00000130  a8 ff ff ff 6e 6b 20 00  eb ab df eb 10 08 cb 01  |....nk .........|
00000140  00 00 00 00 58 b4 c4 02  00 00 00 00 00 00 00 00  |....X...........|
00000150  ff ff ff ff ff ff ff ff  01 00 00 00 08 b6 c4 02  |................|
00000160  d0 ee 22 01 ff ff ff ff  00 00 a0 00 00 00 00 00  |..".............|
00000170  00 00 00 00 4e 00 00 00  00 00 00 00 05 00 00 00  |....N...........|
00000180  43 4c 53 49 44 00 00 00  f8 ff ff ff e0 b7 c4 02  |CLSID...........|
00000190  f8 ff ff ff c8 b8 c4 02  e8 ff ff ff 76 6b 00 00  |............vk..|
000001a0  4e 00 00 00 b0 b5 c4 02  01 00 00 00 00 00 00 00  |N...............|
000001b0  a8 ff ff ff 7b 00 34 00  44 00 38 00 41 00 00 fe  |....{.4.D.8.A...|
000001c0  ff ff 83 fe ff ff cf 07  00 00 00 f0 02 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 52 ff  02 00 7d 40 c4 08 00 00  |......R...}@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by srs5694 on 2011-02-24
Your partition table looks fine, although it's possible I've missed a problem. I recommend you download [Super GRUB 2 Disk](http://www.supergrubdisk.org) (note: That's Super GRUB ***2*** Disk, not Super GRUB Disk), burn it, and try to use it to boot the computer. If it works, you'll be able to boot Linux and then type "sudo grub-install /dev/sda" to re-install GRUB to the MBR, and everything will be back to normal. If you choose to then re-install or upgrade Ubuntu, you can tackle that with a working installation, hopefully with more luck than you're having now.

If you can't boot even with Super GRUB 2 Disk, you might try going into the manual partitioning option in the installer. If you can see your partitions there, then you should be able to set them up and re-install over the old system, even if the automatic OS-detection code is malfunctioning. If you don't see your partitions in the installer, though, you've got a more serious problem -- either a corrupt partition table (a problem I've missed) or something else wrong (maybe leftover RAID data).

---

### Post by anypundit on 2011-02-24
Super Grub2 worked like a charm!  I was able to boot into Ubuntu by selecting the cfg file from my /boot partition.  Grub-install fixed the issue permanently.  Thanks!

The partitioning is another matter.  I saw that "/dev/sda4 ends after the last sector of /dev/sda" so I used testdisk to fix the length of this extended partition.  But Gparted is still showing the whole disk as unallocated, and says "Can't have a partition outside of a disk."  Fdisk and testdisk both show the disk as normal.  How do I fix the extended part?  Here is my current table:

```

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    27,278,369    27,278,307   7 HPFS/NTFS
/dev/sda2    *     27,278,370    27,487,214       208,845   7 HPFS/NTFS
/dev/sda3          27,487,215   287,264,783   259,777,569   7 HPFS/NTFS
/dev/sda4         287,264,817   488,408,129   201,143,313   f W95 Ext d (LBA)
/dev/sda5         287,266,816   287,459,327       192,512  83 Linux
/dev/sda6         287,461,376   434,540,543   147,079,168  83 Linux
/dev/sda7         434,546,688   444,405,759     9,859,072  83 Linux
/dev/sda8         444,409,856   446,455,791     2,045,936  82 Linux swap / Solaris
/dev/sda9         446,455,808   488,394,751    41,938,944   7 HPFS/NTFS

/dev/sda4 ends after the last sector of /dev/sda

```

---

### Post by oldfred on 2011-02-24
Thread with similar issue:

[http://ubuntuforums.org/showthread.php?t=1693318](http://ubuntuforums.org/showthread.php?t=1693318)

Backup partition table to text file and store on another device.
sudo sfdisk -d /dev/sda > PT.txt

Fix overlaping partition error from srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

A few have had this work:

you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
e

---

### Post by srs5694 on 2011-02-25
> **anypundit said:**
> Super Grub2 worked like a charm!  I was able to boot into Ubuntu by selecting the cfg file from my /boot partition.  Grub-install fixed the issue permanently.  Thanks!

I'm glad that worked.

> The partitioning is another matter.  I saw that "/dev/sda4 ends after the last sector of /dev/sda" so I used testdisk to fix the length of this extended partition.  But Gparted is still showing the whole disk as unallocated, and says "Can't have a partition outside of a disk."  Fdisk and testdisk both show the disk as normal.  How do I fix the extended part?  Here is my current table:

I must have missed that when I looked at your partition table earlier. (Those big numbers tend to blur together!) I can't add much to oldfred's reply at this point. FWIW, I wrote one of the Web pages to which he refers. I can say, though, that reports indicate that TestDisk is one of the primary causes of this problem, so using it to fix it is unlikely to do any good.

---

### Post by anypundit on 2011-02-25
Indeed, it *was* your page ([http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)) that provided the fix. Excellent info in there.  Thanks again, to you and oldfred!

---

