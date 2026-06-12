---
title: "Unable to install ubuntu"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by Bartias on 2012-05-04
Hello

I have a big problem with installing ubuntu 12.04.

The thing is, that I had WIn 7 for a couple of months, then I've installed Ubuntu 11.10 along Win7 and I had no problems, except for not enough disk space on ubuntu partition (when I last used linux, 10 GB was more than enough). Because of the new release, I decided to extend my linux partition and upgrade ubuntu.

I used linux LiveCD (USB) to repartition and upgrade the system, but after installing and removing the pendrive, none of the systems boot. 

I have used some ways of restoring the boot manager, like Boot-Repair (the auto-help did not help - however, reseting the MBR allowed me to boot into windows again)

In windows I've tried two boot managers (easyBCD and something else) - they both seem to "see" linux, but they don't boot.

I have dropped the idea of keeping my ubuntu files, I have tried to remove it and install it again - I don't want to "save" ubuntu anymore, I just need to install it in order to work (I've lost 2 days on this).


This is what I get after sudo fdisk -l (at this point, windows does not boot as well)

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   421192169   210596053+   7  HPFS/NTFS/exFAT
/dev/sda2       421192170  1428885359   503846595    7  HPFS/NTFS/exFAT
/dev/sda3      1428885502  1465147391    18130945    5  Extended
/dev/sda5      1428885504  1448417279     9765888   83  Linux
/dev/sda6      1448419328  1450420223     1000448   82  Linux swap / Solaris
/dev/sda7      1450422272  1465147391     7362560   83  Linux

```I was also told to show the boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and this is the current result [http://pastebin.com/SbuL4m6z](http://pastebin.com/SbuL4m6z)

Help me please

Regards

---

### Post by darkod on 2012-05-04
Use the 12.04 cd to boot into live mode.

You have to delete grub2 that you installed onto /dev/sda1 partition boot sector. Windows partitions can't work if grub is in its boot sector. You can use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Also, you need to open /dev/sda2 and delete the /grub/grub.cfg and /grub/core.img files. They shouldn't be there.

From that point on, you can think if you want to save ubuntu, or reinstall. You can give it a go at saving it, in live mode in terminal try:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Restart and see if that gives you the correct grub2 menu and if it works.

If you want to get rid of ubuntu, simply reuse the same partitions and install over them. You don't even need to format /home (/dev/sda7) and you can reuse it.

Or delete all ubuntu partitions including the extended one, and use that unallocated space to install.

---

### Post by Bartias on 2012-05-04
THank you very much.

And, when I install Ubuntu again - what should be the mounting point, on which partition etc?

---

### Post by darkod on 2012-05-04
For reusing existing /home, it has to be done with manual partitioning.

/dev/sda5 is root, mount point /
/dev/sda6 is swap area (no mount point)
/dev/sda7 is /home

For root tick the format box, for /home no. But you have to use the same filesystem, for example if it's ext4 now, use it as ext4 again.

---

### Post by Bartias on 2012-05-04
> **darkod said:**
> Use the 12.04 cd to boot into live mode.



Also, you need to open /dev/sda2 and delete the /grub/grub.cfg and /grub/core.img files. They shouldn't be there.



How do I do this? I was not able to find it, nor to access it in console.

---

### Post by mips on 2012-05-04
Just boot up with your Win 7 DVD and select repair and the do a FIXMBR do delte grub. You should be able to boot into Win 7 now.

Next delte all the linux partitions from your livecd and reinstall linux which will install a new grub.

---

### Post by Bartias on 2012-05-04
THe problem is I was able to boot into windows and yet installing a fresh Ubuntu did not solve the issue.

And currently, i get "read error" after "Loading operating system" and nothing happens (unless I use Live USB).

And I cannot use my Win7 DVD because I don't have a DVD drive in this PC at the moment.


Anyway, I've tried Boot-Repair again, because I'm a little terrified that now I don't have the access to any of the OS'es.

It showed me this [http://paste.ubuntu.com/967436/](http://paste.ubuntu.com/967436/) report. Now I'm gonna see what happens when I reboot.

Well, a read error - so now I cannot use any of the systems.

---

### Post by darkod on 2012-05-04
> **Bartias said:**
> How do I do this? I was not able to find it, nor to access it in console.

Simply open Nautilus (click on the folder icon in Unity), and once the file browser opens the detected partitions are shows on the left. Click on the partition you want to open (you can tell by the size). That's it.

In terminal you could mount it manually but maybe deleting files in terminal will be more difficult unless you are used to it.

---

### Post by Bartias on 2012-05-04
Yeah, I've done that - it turned out that dev/sda2 is my D: disk from windows:) There was a large folder "grub", i Have deleted only that two files. Is that okay?

A moment ago I've tried to install ubuntu once again, but it still, the same error.

Maybe the problem is "device for bootloader information"? I have chosen dev/sda (750GB)

Maybe I shopuld choose something else?

---

### Post by mips on 2012-05-04
> **Bartias said:**
> 
And I cannot use my Win7 DVD because I don't have a DVD drive in this PC at the moment.

If you have access to another PC MS has a utility to write the DVD to a USB flash stick. 

[http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars](http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars)
[http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool](http://www.microsoftstore.com/store/msstore/html/pbPage.Help_Win7_usbdvd_dwnTool)

---

### Post by darkod on 2012-05-04
> **Bartias said:**
> Yeah, I've done that - it turned out that dev/sda2 is my D: disk from windows:) There was a large folder "grub", i Have deleted only that two files. Is that okay?

A moment ago I've tried to install ubuntu once again, but it still, the same error.

Maybe the problem is "device for bootloader information"? I have chosen dev/sda (750GB)

Maybe I shopuld choose something else?

/dev/sda is correct for the bootloader. But I've seen cases where it is not correctly installed especially if grub2 was already there, as in your case.

Try the two commands to install grub2 from live mode from post #2. It can't hurt.

---

### Post by Bartias on 2012-05-04
Read Error again.

I will post results of the new test from #1 again - maybe I have changed something accidentally.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   421192169   210596053+   7  HPFS/NTFS/exFAT
/dev/sda2       421192170  1428885359   503846595    7  HPFS/NTFS/exFAT
/dev/sda3      1428885502  1465147391    18130945    5  Extended
/dev/sda5      1428885504  1448417279     9765888   83  Linux
/dev/sda6      1448419328  1450420223     1000448   82  Linux swap / Solaris
/dev/sda7      1450422272  1465147391     7362560   83  Linux

```

                ```
  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 1442073064 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /NST/nst_linux.mbr 
                       looks at sector 1433902815 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   421,192,169   421,192,107   7 NTFS / exFAT / HPFS
/dev/sda2         421,192,170 1,428,885,359 1,007,693,190   7 NTFS / exFAT / HPFS
/dev/sda3       1,428,885,502 1,465,147,391    36,261,890   5 Extended
/dev/sda5       1,428,885,504 1,448,417,279    19,531,776  83 Linux
/dev/sda6       1,448,419,328 1,450,420,223     2,000,896  82 Linux swap / Solaris
/dev/sda7       1,450,422,272 1,465,147,391    14,725,120  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4023 MB, 4023385600 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7858175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       222ec6d1-cd5b-9644-ae48-69e4743494b0   ext2       casper-rw
/dev/sda1        01CD23B1B1584CB0                       ntfs       
/dev/sda2        01CD23B1A8345D40                       ntfs       
/dev/sda5        5a77b378-5257-449d-ada8-dee89c80b52f   ext4       
/dev/sda6        4454280e-51f2-4250-a19c-88602672d6db   swap       
/dev/sda7        b720b949-c3da-4ef5-82f0-69fcd5c26e45   ext4       
/dev/sdb1        10DD-0862                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 5a77b378-5257-449d-ada8-dee89c80b52f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 5a77b378-5257-449d-ada8-dee89c80b52f
  set locale_dir=($root)/boot/grub/locale
  set lang=pl_PL
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5a77b378-5257-449d-ada8-dee89c80b52f
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=5a77b378-5257-449d-ada8-dee89c80b52f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.2.0-24-generic-pae (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5a77b378-5257-449d-ada8-dee89c80b52f
    echo    'Wczytywanie systemu Linux 3.2.0-24-generic-pae...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=5a77b378-5257-449d-ada8-dee89c80b52f ro recovery nomodeset 
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5a77b378-5257-449d-ada8-dee89c80b52f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 5a77b378-5257-449d-ada8-dee89c80b52f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 01CD23B1B1584CB0
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
UUID=5a77b378-5257-449d-ada8-dee89c80b52f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=b720b949-c3da-4ef5-82f0-69fcd5c26e45 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=4454280e-51f2-4250-a19c-88602672d6db none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 686.349647522 = 736.962322432  boot/grub/core.img                             1
 689.629440308 = 740.483973120  boot/grub/grub.cfg                             1
 682.759765625 = 733.107716096  boot/initrd.img-3.2.0-24-generic-pae           2
 682.502719879 = 732.831715328  boot/vmlinuz-3.2.0-24-generic-pae              1
 682.759765625 = 733.107716096  initrd.img                                     2
 682.502719879 = 732.831715328  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

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

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

---

### Post by darkod on 2012-05-04
So, none of the OSs boot, or only windows doesn't boot?

---

### Post by Bartias on 2012-05-04
None of them

---

### Post by darkod on 2012-05-04
I can't see anything wrong in the results, except that you still have grub2 on /dev/sda1 as we discussed.

But even if windows can't boot because of that, ubuntu should boot.

The only thing that could possibly be a problem that I can see, is that the grub files and kernels are towards the end of the disk, after the 680GiB. Somtimes, some computers have problems if the boot files are so far from the start.

I don't have any large disks and have never seen this issue, but I have seen it mentioned here.

However, it's very inconvenient now to rearrange the disk layout, with data on it, and move ubuntu closer to the start, and the ntfs data partition to the back. Plus, I can't say 100% that this is the problem.

---

### Post by Bartias on 2012-05-04
And I cannot remove grub2 from /dev/sda1, at least not with the procedure described in that link.

Perpahs removing the entire Ubuntu partitions, all of them, then fixing the win7 bootloader somehow from USB, and THEN installing a fresh version of ubuntu could help?

---

### Post by darkod on 2012-05-04
Yes, that is one approach. I hope the same error won't be there again since we don't know what is causing it.

---

### Post by Bartias on 2012-05-04
Ok, now that is freaking crazy - I have changed the BIOS settings into fail safe and bang, there is my GRUB loader with WORKING ubuntu 12.04 and not working Win 7.

So, basically, now I have to bring Win back to the Grub loader. At this point, when I click Windows 7, sceen goes black and only "_" blinks and nothing else happens.

---

### Post by darkod on 2012-05-04
> **Bartias said:**
> Ok, now that is freaking crazy - I have changed the BIOS settings into fail safe and bang, there is my GRUB loader with WORKING ubuntu 12.04 and not working Win 7.

So, basically, now I have to bring Win back to the Grub loader. At this point, when I click Windows 7, sceen goes black and only "_" blinks and nothing else happens.

This is because of the grub2 installed onto its partition.

PS. You said you couldn't fix it with testdisk. What exactly is the problem? testdisk should fix that easy.

---

### Post by Bartias on 2012-05-04
Yeah, and Testdisk did not help to remove it...

---

### Post by darkod on 2012-05-04
> **Bartias said:**
> Yeah, and Testdisk did not help to remove it...

What exactly did it say? It should help in these cases.

---

### Post by Bartias on 2012-05-04
There was no error, but, according to the instruction

If  the sixth  screen did not have  a "BackupBS"  tab,  it usually means  that the original and backup boot sector are identical, and you are  probably suffering from a different problem. But it could also mean that  your backup boot sector is corrupted, in which case you will of to use  "fixboot" from a Windows CD to repair the boot sector.   

I did somethings anyway (I hoped that one of the options will restore original Win MBR) but nothing happened.

I tried to fix Win with Boot-Repair and it gave me this report [http://paste.ubuntu.com/967807/](http://paste.ubuntu.com/967807/)

And after rebooting there were only 3 options in GRUB and no windows.

---

### Post by darkod on 2012-05-04
And was there an option Rebuild BS?

Now in your latest results the windows boot files are gone. Not sure what you did, but you just made it worse.

Now you do need to boot with a win7 dvd/usb and try to recover them with the manual procedure explained here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If that makes windows boot, you will need to reinstall grub2 to the MBR with instructions in the same link.

---

### Post by Bartias on 2012-05-04
Yes, there was such option and I've used it

The funny thing is that Windows Recovery Disk freezes and I cannot use it.

---

