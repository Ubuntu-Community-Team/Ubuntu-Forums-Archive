---
title: "Ubuntu 11.04 boot problem"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by jwmaddox on 2011-10-16
Hello,
 
I just installed Ubuntu 11.04 from a CD on a new USB 2.0 external hard drive following the instructions provided by [http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/) The CD was created using a download from the Ubuntu site.
 
When I restart my laptop, which normally runs Windows XP, Windows XP boots as usual. And when I look in My Computer from within Windows, the external hard drive isn't shown. It's as if I had done nothing and had no external hard drive. Can you offer any guidance as to how to boot Ubuntu from my external hard drive?
 
I did look around fora to see if someone else had this or a similar problem, and there were several posts on the subject; but honestly, I'm brand new to this, and it was not clear to me how to proceed. I did note that generation of a "RESULTS.txt" file was usually involved, so I produced that file for my system, and have attached it below.
 
Regards,
James
 
```

                  Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /ntdetect.com
sda2: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM
sdb1: __________________________________________________________________________
    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img
sdb2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: __________________________________________________________________________
    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
sdb6: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab
sdb7: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *             63    16,390,079    16,390,017   7 NTFS / exFAT / HPFS
/dev/sda2          16,390,080   117,195,119   100,805,040   7 NTFS / exFAT / HPFS
 
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *          2,048       503,807       501,760  83 Linux
/dev/sdb2             505,854 1,953,517,567 1,953,011,714   5 Extended
/dev/sdb5             505,856     4,409,343     3,903,488  82 Linux swap / Solaris
/dev/sdb6           4,411,392    23,941,119    19,529,728  83 Linux
/dev/sdb7          23,943,168 1,953,517,567 1,929,574,400  83 Linux
 
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        528CEC848CEC63C7                       ntfs       
/dev/sda2        7684EB4884EB0A07                       ntfs       
/dev/sdb1        badb25c6-b286-4b00-947e-68bc69ee3668   ext2       
/dev/sdb6        ebfe821d-062d-40ab-b2b5-1767fabc3a14   ext4       
/dev/sdb7        d6d9f94a-3812-4a35-bf73-b6edf4a2430a   ext4       
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
 
================================ sda1/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\BOOTSECT.DAT="System Restore" /minint 
--------------------------------------------------------------------------------
================================ sda2/boot.ini: ================================
--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------
============================= sdb1/grub/grub.cfg: ==============================
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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root ebfe821d-062d-40ab-b2b5-1767fabc3a14
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
set locale_dir=($root)/grub/locale
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
 set root='(/dev/sdb,msdos1)'
 search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
 linux /vmlinuz-2.6.38-8-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro   quiet splash vt.handoff=7
 initrd /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 set gfxpayload=$linux_gfx_mode
 insmod part_msdos
 insmod ext2
 set root='(/dev/sdb,msdos1)'
 search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
 echo 'Loading Linux 2.6.38-8-generic ...'
 linux /vmlinuz-2.6.38-8-generic root=UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sdb,msdos1)'
 search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
 linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(/dev/sdb,msdos1)'
 search --no-floppy --fs-uuid --set=root badb25c6-b286-4b00-947e-68bc69ee3668
 linux16 /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
 insmod part_msdos
 insmod ntfs
 set root='(/dev/sda,msdos1)'
 search --no-floppy --fs-uuid --set=root 528CEC848CEC63C7
 drivemap -s (hd0) ${root}
 chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
 insmod part_msdos
 insmod ntfs
 set root='(/dev/sda,msdos2)'
 search --no-floppy --fs-uuid --set=root 7684EB4884EB0A07
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
=================== sdb1: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
   0.211028099 = 0.226589696    grub/core.img                                  2
   0.211551666 = 0.227151872    grub/grub.cfg                                  1
   0.061859131 = 0.066420736    initrd.img-2.6.38-8-generic                   74
   0.009290695 = 0.009975808    vmlinuz-2.6.38-8-generic                      20
=============================== sdb6/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=ebfe821d-062d-40ab-b2b5-1767fabc3a14 /               ext4    errors=remount-ro 0       1
/dev/sdb1       /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=d6d9f94a-3812-4a35-bf73-b6edf4a2430a /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
#UUID=911e8316-1642-4547-ae98-104d3ed0c1e3 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------
=============================== StdErr Messages: ===============================
unlzma: Decoder error
 

```

---

### Post by Merk42 on 2011-10-22
Moved to Installation & Upgrades

---

### Post by 2F4U on 2011-10-22
Its quite unclear to me what your problem is. Is it that you are not able to boot Ubuntu or that can boot Ubuntu, but are unable to see anything inside Ubuntu from Windows?
If you are unable to boot Ubuntu, then you may need to change boot order in your BIOS, so that the external hdd comes first. If you don't see anything inside Ubuntu from Windows, this is probably due to the ext4 filesystem. As far as I know, Windows by default is not able to read content from a ext4 filesystem.

---

### Post by raja.genupula on 2011-10-22
you said that Ubuntu installed in your external harddisk.ok put a live cd boot from it and do this

sudo dpkg-reconfigure grub-pc

install your grub to external hard disk i mean to your sdb.

all the best. 

& one more thing i can help for you is go with the grub recovery link in my signature and make sure that you have connected your external hard disk while doing this process.

---

### Post by jwmaddox on 2011-10-23
2F4U, my difficulty is that I cannot boot Ubuntu; when I start my laptop, it boots XP.  The reference to Windows that I made in my original post was meant to provide additional information that might help resolve the problem.  I had been able to see the external hard drive from My Computer before the Ubuntu installation to the hard drive, but not after, so I thought that might be another piece to the puzzle.  Sorry if it came across as confusing.

Regards,
James

---

### Post by jwmaddox on 2011-10-24
raja.genupula, I followed your instructions, and it resolved the issue, so thank you for taking the time to offer some solutions.
 
If anyone is interested, I first ran the following command:
sudo dpkg-reconfigure grub-pc
which did not fix the problem.  So I then followed the "Grub Recovery" link, clicked "Boot-Repair" under "Using Boot-Repair-Disk", then used the "2nd Option: install Boot-Repair in Ubuntu" to run the two commands listed there.  It worked like a charm.
 
Regards,
James

---

