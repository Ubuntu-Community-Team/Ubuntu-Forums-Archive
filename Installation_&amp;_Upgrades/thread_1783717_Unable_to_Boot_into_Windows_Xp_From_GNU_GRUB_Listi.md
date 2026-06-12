---
title: "Unable to Boot into Windows Xp From GNU GRUB Listing.  :("
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Dilip Kumar Kar on 2011-06-16
Hello everyone..!

I have recently installed Ubuntu 11.04 as Dual Boot with Windows Xp..!

The Problem i'm facing is that ..the gnu grub 1.99 has listed the Windows xp but upon selecting doesn't boot up xp rather it comes back to the Grub menu...again.

I'm able to use my ubuntu but can't access my windows.

I'll be very thankful for any kind of Help.

1. Harddisk with 4 partitions.
2. Windows xp on first partition(primary), 2 partitions for ubuntu, other for data.
3. Bootloader installed on windows partition.
4. Details of Grub entry for Windows Xp...
           setparams 'Microsoft Windows XP Professional(on /dev/sda1)'
           insmod part_msdos
           insmod ntfs
           set root = '(/dev/sda,msdos1)'
           search --no-floppy --fs--uuid --set=root 1820352D2035136C
           drivemap -s(hd0) ${root}
           chainloader +1
5. System config Intel Pentium Dual Core, 2 GB Ram.
6. Have attached a screenshot of my Windows Partition Drive.

---

### Post by mikewhatever on 2011-06-16
Why is the bootloader installed on the Windows partition?
Are you sure Ubuntu is on a dedicated partition? According to the screenshot, you have a wubi installation.
To clarify those points, and provide the relevant info, run the [BOOTINFO script]("http://bootinfoscript.sourceforge.net/") from Ubuntu and post the output.

---

### Post by Dilip Kumar Kar on 2011-06-16
At first i burned a DVD for Ubuntu 11.04 image for installation but was unable to boot form it.
I selected the option of "Help me boot from CD/DVD" from the installation menu of Ubuntu while initiating the installation from inside windows.

Restarted the System and got a Ubuntu Entry While alongside Windows and Selected that and next installed the Ubuntu.

Ubuntu is installed on a Dedicated partition of 10GB and with a Swap Partition of 4GB.

Have installed the Bootloader at Windows Partition as my friend told me that it would be easier to remove if something goes wrong and recover the windows by repairing it.

Including the Results of the Script u told to execute as Results.txt in Attachments.

I'm really Thankful to you for your kind Concern. Please help me out.

I have backed up all my relevant data from windows.

---

### Post by Dilip Kumar Kar on 2011-06-16
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 56980130 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    51,199,154    51,199,092   7 NTFS / exFAT / HPFS
/dev/sda2          51,199,216   234,420,479   183,221,264   f W95 Extended (LBA)
/dev/sda5          51,199,218    71,199,217    20,000,000  83 Linux
/dev/sda6          96,357,933   234,420,479   138,062,547   7 NTFS / exFAT / HPFS
/dev/sda7          71,200,768    79,198,207     7,997,440  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697664 bytes
227 heads, 32 sectors/track, 1089 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,913,471     7,913,440   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1820352D2035136C                       ntfs       
/dev/sda5        350a0fc4-3ccb-4093-be74-4f89efbd078f   ext4       
/dev/sda6        66D88318D882E5A1                       ntfs       
/dev/sda7        26486d6a-5ed6-46a5-b243-8c427cac8001   swap       
/dev/sdb1        C68A-A606                              vfat       DILIP

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/1820352D2035136C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/66D88318D882E5A1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/DILIP             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 350a0fc4-3ccb-4093-be74-4f89efbd078f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 350a0fc4-3ccb-4093-be74-4f89efbd078f
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 350a0fc4-3ccb-4093-be74-4f89efbd078f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=350a0fc4-3ccb-4093-be74-4f89efbd078f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 350a0fc4-3ccb-4093-be74-4f89efbd078f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=350a0fc4-3ccb-4093-be74-4f89efbd078f ro single 
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 350a0fc4-3ccb-4093-be74-4f89efbd078f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 350a0fc4-3ccb-4093-be74-4f89efbd078f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1820352D2035136C
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=26486d6a-5ed6-46a5-b243-8c427cac8001 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  27.170269966 = 29.173855232   boot/grub/core.img                             1
  27.152455330 = 29.154726912   boot/grub/grub.cfg                             1
  31.968377113 = 34.325783552   boot/initrd.img-2.6.38-8-generic               2
  27.151432991 = 29.153629184   boot/vmlinuz-2.6.38-8-generic                  1
  31.968377113 = 34.325783552   initrd.img                                     2
  27.151432991 = 29.153629184   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 c0 03  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 bf 78 00 20 1e 00 00  00 00 00 00 02 00 00 00  |..x. ...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 06 a6 8a c6 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by mikewhatever on 2011-06-16
According to the output, there two installations of Ubuntu, one inside Windows, the other on a dedicated partition (sda5). However, you seem to have overwritten the boot sector of the Windows partition (sda1), which is likely what causes the problem.
I suggest you wait for a Windows boot expert, or, perhaps, ask your friend. It's his advice that got you in trouble in the first place.

---

### Post by Dilip Kumar Kar on 2011-06-16
Isn't there any other way to rebuild the bootsector for Windows...!
Should i remove Ubuntu installed at Windows partition...? is there any way of knowing which of the ubuntu installation i'm using currently..?

---

### Post by mikewhatever on 2011-06-16
To find out which Ubuntu installation you are using, look at the output of **cat /etc/fstab**. As for rebuilding the boot sector, I am sure there are many ways, so don't know what you mean by 'any other'.

---

### Post by Dilip Kumar Kar on 2011-06-16
i was using the standalone installation...!
Have repaired the master Bootsector but it removed the grub laoder and now i have runing windows.
 
but now i can't use  my standalone Ubuntu installation...as grub is not there! :(
 
and
 
the Ubuntu installed at windows partition was incomplete hence removed it by using Add and Remove Programs from Control Panel.
 
Is there any way to add a entry to the boot.ini file in xp to boot Ubuntu.. or i have to reinstall the grub loader to be able to use the Ubuntu ?
 
And thanx for ur analysis it had really hepled me out.

---

### Post by oldfred on 2011-06-16
Windows fixBoot or this will store the PBR or partition boot sector:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You then have to install grub2's boot loader to the MBR of sda:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Hreinsi on 2011-06-16
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html#more](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html#more)

---

### Post by Dilip Kumar Kar on 2011-06-16
Yipeeee... :D i got both of my Windows and Ubuntu back as Dual Boot.

Thanku to **Oldfred**, **mikewhatever** and **Hreinsi** for providing me some insight about the problem in details, its cause and moreover the links that they provided were of great help.

Here is what i did to solve my problem.

1. Restored the windows mbr using testdisk tool from the [**link** ]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"). Restart after restoration.
      [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

2. The above restoration removed grub and windows can be booted directly. Then for Restoring the grub again i used [**Unetbootin for Windows**]("http://unetbootin.sourceforge.net/") to use the iso of Ubuntu to boot to ubuntu without using a CD/DVD.
 
 U have to read how to do it from their **[site]("http://unetbootin.sourceforge.net/")**.
  
The above software gives u a Unetbootin entry in the Windows os boot menu which can be used to get a live Ubuntu OS running.

3. Next follow the steps given at the ubuntu forum  **[thread]("http://ubuntuforums.org/showthread.php?t=1014708")** to restore the Grub..! Grub will automatically detect your windows and set the grub for u..! :)


Again Thanku to "Ubuntu forum" and the Developers of the nice Softwares...! :)

---

