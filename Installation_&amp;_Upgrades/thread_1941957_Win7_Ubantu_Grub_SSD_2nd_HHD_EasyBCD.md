---
title: "Win7 Ubantu Grub SSD 2nd HHD EasyBCD"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by KLund1 on 2012-03-16
I have win 7 on a SSD, I have data, and 3 OS's in 4 partitions on a 2TB HD. I made a small 20gb partition at the end of the HD for Ubantu 11. I used instructions for Linux partitions found [here page 51]("http://www.computerpoweruser.com/DigitalEditions/Default.aspx?RefreshCache=true") At the end of the install, ubantu could not install a bootloader/grub(?) on any  of the HD partitions. It gave an error, and an option to try other  partitions. I tried each. I assume, it was because I put it at the end of the drive. I finished the install with a Ubantu option to complete without a bootloader/grub. I used EasyBCD to add an entry on my boot menu. Of course Ubantu did not load. My boot menu is, Win7-SSD, Win7-HDD, Win8CP-HDD, XP-HDD, Ubantu 11.
I know some about bootloader's, MBR's. Probably just enough to do major damage or worse. My partitions are imaged backed-up.
I know zero about Linux command line instructions. Ubantu dose boot as 'Live' from a USB bootable HDD I made.
Suggestions how to get Ubantu to boot, while keeping all my other OS's working? I know there will be a Linux boot menu after I choose Ubantu from the windows bootloader. 
Any help would be welcome.

---

### Post by oldfred on 2012-03-16
Welcome to the forums.

With two drives you have two MBRs.installing grub2 to the PBR - partition boot sector is less reliable, but can work. It has to use blocklists but you get an error like this:

> Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 


You can install grub2's boot loader to the MBR of your hard drive and boot from that if you want. That would be the easiest & best.

Post boot info script from this:
You can download it into the Ubuntu liveCD/USB or download its full bootable liveCD.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by KLund1 on 2012-03-16
Thanks for the fast reply.
  No joy. Boot Repair boot disk could not load. It could not get past the SSD. It reported an I/O access error sd1, at some buffer address. Even with the failsafe option. I used 64bit since that is the Ubantu version I installed.
I think the problem may be that the SSD is a PCI device, RevoDrive version 1, 37gb raid 0 array. And Boot Repair has no drivers for a PCI SSD? any other suggestions.

ps
"You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration."
where is this?

---

### Post by oldfred on 2012-03-16
One of Boot-Repairs capabilities is to download & run the Boot_info script so we can see you exact configuration.

Direct down load of the newest git/test version that has some fixes, download into your LiveCD:

```
The git/testing version has some fixes:
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```Instructions are here:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by KLund1 on 2012-03-16
Here is the Results.txt file. from a LiveCD (actually USB) boot.
Thanks again for help me with this. It's kind of fun. :)  I always learn more like this.


```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdi.
 => Windows is installed in the MBR of /dev/mapper/sil_acacagbjfhdf.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 371554304. But according to the info from 
                       fdisk, sda5 starts at sector 371556352.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 2055. But according to the info from fdisk, 
                       sdb5 starts at sector 4103.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30510 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sil_acacagbjfhdf1: _____________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /NTLDR /ntdetect.com

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   477,528,063   477,526,016   5 Extended
Empty Partition.
/dev/sda5    *    371,556,352   477,528,063   105,971,712   7 NTFS / exFAT / HPFS
/dev/sda2    *    477,528,064   504,150,015    26,621,952   7 NTFS / exFAT / HPFS
/dev/sda3         504,152,082   586,067,264    81,915,183   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
240 heads, 63 sectors/track, 258401 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               4,101 3,875,969,023 3,875,964,923   f W95 Extended (LBA)
/dev/sdb5               4,103 3,862,298,623 3,862,294,521   7 NTFS / exFAT / HPFS
/dev/sdb6       3,862,300,672 3,863,078,911       778,240  83 Linux
/dev/sdb7       3,863,080,960 3,875,969,023    12,888,064  83 Linux
/dev/sdb3       3,875,971,072 3,887,689,727    11,718,656  82 Linux swap / Solaris
/dev/sdb4       3,887,689,728 3,907,026,943    19,337,216  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,831,551     7,831,489   c W95 FAT32 (LBA)


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78161328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sil_acacagbjfhdf _____________________________________________________________________

Disk /dev/mapper/sil_acacagbjfhdf: 80.0 GB, 80035053568 bytes
144 heads, 14 sectors/track, 77538 cylinders, total 156318464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/sil_acacagbjfhdf1   *          2,048   156,305,407   156,303,360   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/sil_acacagbjfhdf1 1ED8AA24D8A9FA63                       ntfs       Win 7 SSD
/dev/sda2        A6BCF048BCF01511                       ntfs       SSD PageFile
/dev/sda3        9474987D749863B0                       ntfs       XP-MCE
/dev/sda5        E8D67CAFD67C7F9C                       ntfs       Win8
/dev/sda6        0672129D72129213                       ntfs       Win 7 HDD
/dev/sdb3        c31c9dc6-10ae-495f-989a-4a5d4ccff82b   swap       
/dev/sdb4        8efc8fb3-28eb-40ab-83cc-2a8255dd792c   ext4       
/dev/sdb5        01CBA972EDABB450                       ntfs       Data
/dev/sdb6        1bd2c4e2-da22-46d7-839c-1153a51f8f70   ext2       
/dev/sdb7        4fff7921-de45-4325-82fc-14fb67e085bd   ext4       
/dev/sdc1        1DFE-1F46                              vfat       PENDRIVE
/dev/sdh                                                silicon_medley_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sil_acacagbjfhdf
sil_acacagbjfhdf1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sdb6/grub/grub.cfg: ==============================

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
true
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set=root 4fff7921-de45-4325-82fc-14fb67e085bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bd2c4e2-da22-46d7-839c-1153a51f8f70
    linux    /vmlinuz-3.0.0-16-generic-pae root=UUID=4fff7921-de45-4325-82fc-14fb67e085bd ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bd2c4e2-da22-46d7-839c-1153a51f8f70
    echo    'Loading Linux 3.0.0-16-generic-pae ...'
    linux    /vmlinuz-3.0.0-16-generic-pae root=UUID=4fff7921-de45-4325-82fc-14fb67e085bd ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-16-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bd2c4e2-da22-46d7-839c-1153a51f8f70
    linux    /vmlinuz-3.0.0-12-generic root=/dev/sdb7 ro   quiet splash vt.handoff=7
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bd2c4e2-da22-46d7-839c-1153a51f8f70
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=/dev/sdb7 ro recovery nomodeset 
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bd2c4e2-da22-46d7-839c-1153a51f8f70
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 1bd2c4e2-da22-46d7-839c-1153a51f8f70
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root A6BCF048BCF01511
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9474987D749863B0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/mapper/sil_acacagbjfhdf1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd5,msdos1)'
    search --no-floppy --fs-uuid --set=root 1ED8AA24D8A9FA63
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

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                   81
               =                initrd.img-3.0.0-16-generic-pae               79
               =                vmlinuz-3.0.0-12-generic                      20
               =                vmlinuz-3.0.0-16-generic-pae                  22

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=4fff7921-de45-4325-82fc-14fb67e085bd /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb6 during installation
UUID=1bd2c4e2-da22-46d7-839c-1153a51f8f70 /boot           ext2    defaults        0       2
# /home was on /dev/sdb4 during installation
UUID=8efc8fb3-28eb-40ab-83cc-2a8255dd792c /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=c31c9dc6-10ae-495f-989a-4a5d4ccff82b none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  02 66 b9 01 00 00 00 66  8b 1e 32 02 66 8b 36 26  |.f.....f..2.f.6&|
00000010  02 1e 07 66 8b 3e 42 02  e8 45 fb e8 a1 fc 66 61  |...f.>B..E....fa|
00000020  1f 07 c3 66 50 66 53 66  51 66 8b 1e 46 02 66 8b  |...fPfSfQf..F.f.|
00000030  c8 66 c1 e8 03 66 83 e1  07 66 03 d8 66 b8 01 00  |.f...f...f..f...|
00000040  00 00 66 d3 e0 67 84 03  74 03 f8 eb 01 f9 66 59  |..f..g..t.....fY|
00000050  66 5b 66 58 c3 67 80 7b  08 01 74 04 66 2b c0 c3  |f[fX.g.{..t.f+..|
00000060  66 67 8d 73 10 66 67 8b  56 08 66 3b c2 77 09 66  |fg.s.fg.V.f;.w.f|
00000070  67 8b 16 66 3b c2 73 04  66 2b c0 c3 67 03 5e 10  |g..f;.s.f+..g.^.|
00000080  66 2b f6 67 80 3b 00 74  3c e8 7b 00 66 03 f1 e8  |f+.g.;.t<.{.f...|
00000090  37 00 66 03 ca 66 3b c1  7c 21 66 8b d1 66 50 66  |7.f..f;.|!f..fPf|
000000a0  67 0f b6 0b 66 8b c1 66  83 e0 0f 66 c1 e9 04 66  |g...f..f...f...f|
000000b0  03 d9 66 03 d8 66 43 66  58 eb c8 66 2b c8 66 2b  |..f..fCfX..f+.f+|
000000c0  c2 66 03 c6 c3 66 2b c0  c3 66 2b c9 67 8a 0b 80  |.f...f+..f+.g...|
000000d0  e1 0f 66 83 f9 00 75 04  66 2b c9 c3 66 53 66 52  |..f...u.f+..fSfR|
000000e0  66 03 d9 66 67 0f be 13  66 49 66 4b 66 83 f9 00  |f..fg...fIfKf...|
000000f0  74 0d 66 c1 e2 08 67 8a  13 66 4b 66 49 eb ed 66  |t.f...g..fKfI..f|
00000100  8b ca 66 5a 66 5b c3 66  53 66 52 66 2b d2 67 8a  |..fZf[.fSfRf+.g.|
00000110  13 66 83 e2 0f 66 2b c9  67 8a 0b c0 e9 04 66 83  |.f...f+.g.....f.|
00000120  f9 00 75 08 66 2b c9 66  5a 66 5b c3 66 03 da 66  |..u.f+.fZf[.f..f|
00000130  03 d9 66 67 0f be 13 66  49 66 4b 66 83 f9 00 74  |..fg...fIfKf...t|
00000140  0d 66 c1 e2 08 67 8a 13  66 4b 66 49 eb ed 66 8b  |.f...g..fKfI..f.|
00000150  ca 66 5a 66 5b c3 66 0b  c9 75 01 c3 66 51 66 56  |.fZf[.f..u..fQfV|
00000160  67 83 3e 61 7c 0a 67 83  3e 7a 7f 04 67 83 2e 20  |g.>a|.g.>z..g.. |
00000170  66 83 c6 02 e2 ea 66 5e  66 59 c3 66 50 66 51 66  |f.....f^fY.fPfQf|
00000180  8b d0 66 a1 2e 02 66 67  8d 58 10 67 03 43 04 66  |..f...fg.X.g.C.f|
00000190  67 8d 40 10 66 8b da e8  33 f9 66 0b c0 74 05 66  |g.@.f...3.f..t.f|
000001a0  59 66 59 c3 66 a1 32 02  66 0b c0 75 08 66 59 66  |YfY.f.2.f..u.fYf|
000001b0  59 66 33 c0 c3 66 8b 16  32 02 66 67 8d 52 00 41  |Yf3..f..2.fg.R.A|
000001c0  09 00 07 47 57 d3 02 00  00 00 f9 ef 35 e6 00 ef  |...GW.......5...|
000001d0  ff ff 05 ef ff ff fb ef  35 e6 00 e8 0b 00 00 00  |........5.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

---

### Post by oldfred on 2012-03-16
Added code tags which you get by highlighting some code and clicking on the # in the edit panel above your message.

Is sdi the SSD with the RAID or LVM sil mapper? That often causes confusion. Any RAID or LVM requires extra drivers that only are on the alternate installer. If installed you can add the drivers.

Did you run the git or test version of boot script? It does not look like it as it has some bits missing that supposedly were fixed.

Your sda has two boot flags. You only can have one. Ubuntu/grub do not use a boot flag, Windows has to have a boot flag on a primary partition and a few BIOS also need a boot flag so I usually suggest one on every drive on a primary partition. In Ubuntu you can use gparted, or Disk Utility as well as several command line ways to change boot flags. In Windows it is makeactive. Normally when you set a boot flag the software removes boot flags from other partitions. Not sure how you got two?

IF you boot from sdb, your 2TB drive in BIOS, does Ubuntu boot ok? If so rerun the git version of boot script after adding these drivers.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils

---

### Post by KLund1 on 2012-03-16
> **oldfred said:**
> Added code tags which you get by highlighting some code and clicking on the # in the edit panel above your message.
Thanks


> **oldfred said:**
> Is sdi the SSD with the RAID or LVM sil mapper? That often causes confusion. Any RAID or LVM requires extra drivers that only are on the alternate installer. If installed you can add the drivers.
I'm going to assume that it is RAID, as that is what it says during booting

 > **oldfred said:**
> Did you run the git or test version of boot script? It does not look like it as it has some bits missing that supposedly were fixed.
just the git version from link you posted above. all download links go to the same file.


 > **oldfred said:**
> Your sda has two boot flags. You only can have one. Ubuntu/grub do not use a boot flag, Windows has to have a boot flag on a primary partition and a few BIOS also need a boot flag so I usually suggest one on every drive on a primary partition. In Ubuntu you can use gparted, or Disk Utility as well as several command line ways to change boot flags. In Windows it is makeactive. Normally when you set a boot flag the software removes boot flags from other partitions. Not sure how you got two?
I use Acronis Disk Director. BUt have know idea about boot flags, or how to change them. Will google to learn more.  


> **oldfred said:**
> IF you boot from sdb, your 2TB drive in BIOS, does Ubuntu boot ok? If so rerun the git version of boot script after adding these drivers.
Nothing boots, no menu, computer just sits with black screen.

> **oldfred said:**
> Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
Do not understand what this is. I think they a commands for execution from a linux terminal? I'm still new to linux in general.

---

### Post by KLund1 on 2012-03-16
Sorry, Booting from 2tb drive does get to Grub. I selected the other HD drive (300gb) by mistake.  Menu
GNU Grub v1.99-12ubantu5 (title at top of screen)
menu items:
Ubantu with linux 3.0.0-16 generic pae
Ubantu with linux 3.0.0-16 generic pae (recovery mode)
Previous versions of linux
memtest
WIn7 loader on /dev/sda2
WIn7 loader on /dev/sda3
WIn7 loader on /dev/mapper/sil_acacajgjfdhf1

'c' for command line

Ubantu with linux 3.0.0-16 generic pae option does nothing but blinking cursor top left
Ubantu with linux 3.0.0-16 generic pae (recovery mode) gets me to a 
Recovery Menu - Limited read only menu
Resume normal boot
fsck
remount
root

'Resume normal boot' starts to work as executed commands fly by and is usual for linux loading but stops with this error
Warning: fake initctl called, doing nothing. of which i see several above it also. 
I hit enter and Ubantu purple screen shows, and the 4 dot change color from white to red and back. There is not HD activity, it just sits at that screen. 
But I'm closer then before. next steps?

---

### Post by oldfred on 2012-03-17
What video card/chip so you have? Often those who boot to grub menu but then cannot fully boot have video issues. I have to add nomodeset with my nVidia on CD/USB and all first boots until I load the nVidia driver.

A few also need other kernel options or have to change settings in BIOS.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by KLund1 on 2012-03-18
WOW, lets hold on here. this is getting just a bit out on comfort zone.
Let try a different tack, 
 with my current multi boot setup my win7 SDD take up most of the PCI, raid0 drive. There are no other partitions on that drive. BUt on the HD that I have win7 HDD, WIn XP, WIn 8, partitions, could I put a ubantu install "along" (as the ubantu installer asks during the install, but dose not ask where) the win7 install that has 50gb free in it's partition? 

As you asked, I got a xfx nvinda 260 video card. NOMODESET link you have is for version 10, not 11. I think I got grub 1.9, not 2 as shown above.

I just check the OCZ web site and they do not have drivers for Linux for my revodrive. I'm not sure if my mbr booloader is on the win7 HHD, or the win7 SSD. I assume it must be on the HD since I got to a grub menu somehow.  
 
I will be reading the links above to learn move, but currently above my usable knowledge level. 
I still appreciate you help, and experience with my lack there of ...

---

### Post by oldfred on 2012-03-18
Boot script showed grub2's boot loader in the MBR of your 2TB drive. Grub2 is currently at version 1.99, it is just the second version of grub. The old version is now called grub legacy but never go past version 0.97.

I have had to use the nomodeset for every version since 10.04, it still applies. Although I now notice some of the new recovery modes have nomodeset. Not sure now, if I reset that as a default or if it came that way.

---

