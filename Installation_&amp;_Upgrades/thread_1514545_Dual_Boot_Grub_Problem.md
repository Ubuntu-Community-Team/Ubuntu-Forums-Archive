---
title: "Dual Boot Grub Problem"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by pgs3223 on 2010-06-21
[FONT=Times New Roman][SIZE=3]I have a Toshiba NB305 netbook that came delivered with a 250GB hard disk which had two 125GB partitions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The First C: (“Windows”) Contained Windows 7 and associated programs.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The Second D:(“Data”) Contained the rescue software.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I downloaded a copy of the Ubuntu 10.04 Lucid Lynx ISO image from the Ubuntu website and created a bootable CD.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I booted from the USB disc and installed Ubuntu alongside Windows 7 with the intention of creating a dual boot machine. I allocated Ubuntu 30GB of disk space.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I rebooted the machine I saw options to boot into either Linux (Ubuntu) or Windows 7 as expected.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I chose Windows 7 the computer boot to Windows 7 again as expected.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I chose Linux I get a blank screen with a cursor blinking in the top left corner, it does not boot in to Ubuntu.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Looking at the disc allocation Ubuntu has installed itself, I just can not boot from it, I suspect this is a GRUB problem.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I have included the following information as I am guessing that it would be helpful to somebody in helping me.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The GRUB menu declares itself as Grub Version 1.98[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[SIZE=3][FONT=Times New Roman]                                    Size                 Used[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]/dev/sda1         ntfs      419MB            Unknown        Win 7 loader[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda2         ntfs      125029MB      27793MB        “Windows”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda3         ntfs      94620MB        6052MB          “Data”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda5         ext4     28704MB        2817MB          “Ubuntu”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda6         swop    1283MB          0MB[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Can anybody help me boot into Ubuntu?[/SIZE][/FONT]

---

### Post by wilee-nilee on 2010-06-21
Post the bootscript in my sig in code tags. You can also highlight the script readout in the reply and click on the # in the reply panel to get it in code tags.

---

### Post by Steve Reeves on 2010-06-21
> **pgs3223 said:**
> [FONT=Times New Roman][SIZE=3]I have a Toshiba NB305 netbook that came delivered with a 250GB hard disk which had two 125GB partitions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The First C: (“Windows”) Contained Windows 7 and associated programs.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The Second D:(“Data”) Contained the rescue software.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I downloaded a copy of the Ubuntu 10.04 Lucid Lynx ISO image from the Ubuntu website and created a bootable CD.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I booted from the USB disc and installed Ubuntu alongside Windows 7 with the intention of creating a dual boot machine. I allocated Ubuntu 30GB of disk space.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I rebooted the machine I saw options to boot into either Linux (Ubuntu) or Windows 7 as expected.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I chose Windows 7 the computer boot to Windows 7 again as expected.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]When I chose Linux I get a blank screen with a cursor blinking in the top left corner, it does not boot in to Ubuntu.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Looking at the disc allocation Ubuntu has installed itself, I just can not boot from it, I suspect this is a GRUB problem.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I have included the following information as I am guessing that it would be helpful to somebody in helping me.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The GRUB menu declares itself as Grub Version 1.98[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[SIZE=3][FONT=Times New Roman]                                    Size                 Used[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]/dev/sda1         ntfs      419MB            Unknown        Win 7 loader[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda2         ntfs      125029MB      27793MB        “Windows”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda3         ntfs      94620MB        6052MB          “Data”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda5         ext4     28704MB        2817MB          “Ubuntu”[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/dev/sda6         swop    1283MB          0MB[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Can anybody help me boot into Ubuntu?[/SIZE][/FONT]
I have almost the same problem, except that my machine boots straight into win7 , i don't get the dual boot option. Ubuntu installed ok.

---

### Post by pgs3223 on 2010-06-21
> **wilee-nilee said:**
> Post the bootscript in my sig in code tags. You can also highlight the script readout in the reply and click on the # in the reply panel to get it in code tags.
 
Thanks for the quick reply, can you tell me how I get the boot script please?

---

### Post by darkod on 2010-06-21
> **Steve Reeves said:**
> I have almost the same problem, except that my machine boots straight into win7 , i don't get the dual boot option. Ubuntu installed ok.

If you have more than one disk, grub2 is not on the disk where you expect it, or you are not booting from the disk where grub2 is.

---

### Post by darkod on 2010-06-21
> **pgs3223 said:**
> Thanks for the quick reply, can you tell me how I get the boot script please?

Just click the link in his signature (or mine) saying bootscript.

---

### Post by pgs3223 on 2010-06-21
Thanks guys
 
I have pasted the boot script below
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD
sda2: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe
sda3: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sda4: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdc1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   245,018,623   244,197,376   7 HPFS/NTFS
/dev/sda3         245,018,624   429,823,884   184,805,261   7 HPFS/NTFS
/dev/sda4         429,823,998   488,396,799    58,572,802   5 Extended
/dev/sda5         429,824,000   485,887,999    56,064,000  83 Linux
/dev/sda6         485,890,048   488,396,799     2,506,752  82 Linux swap / Solaris

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdc1    *             32     3,915,775     3,915,744   6 FAT16

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        12FEEF4EFEEF2925                       ntfs       SYSTEM                        
/dev/sda2        4E0AF2D00AF2B3D5                       ntfs       WINDOWS                       
/dev/sda3        26A8F508A8F4D771                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2fc8e924-6601-444f-89ba-324cdad21868   ext4                                     
/dev/sda6        3cb87807-01c1-4e29-8b5d-38854926cf64   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        9820-96C8                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/WINDOWS           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== sda5/boot/grub/grub.cfg: ===========================
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2fc8e924-6601-444f-89ba-324cdad21868
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
search --no-floppy --fs-uuid --set 2fc8e924-6601-444f-89ba-324cdad21868
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 2fc8e924-6601-444f-89ba-324cdad21868
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=2fc8e924-6601-444f-89ba-324cdad21868 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 2fc8e924-6601-444f-89ba-324cdad21868
 echo 'Loading Linux 2.6.32-21-generic ...'
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=2fc8e924-6601-444f-89ba-324cdad21868 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 2fc8e924-6601-444f-89ba-324cdad21868
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 2fc8e924-6601-444f-89ba-324cdad21868
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set 12feef4efeef2925
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
UUID=2fc8e924-6601-444f-89ba-324cdad21868 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3cb87807-01c1-4e29-8b5d-38854926cf64 none            swap    sw              0       0
=================== sda5: Location of files loaded by Grub: ===================

 228.7GB: boot/grub/core.img
 228.8GB: boot/grub/grub.cfg
 228.9GB: boot/initrd.img-2.6.32-21-generic
 228.8GB: boot/vmlinuz-2.6.32-21-generic
 228.9GB: initrd.img
 228.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============
sdb

---

### Post by darkod on 2010-06-21
If you try to boot the ubuntu cd in live mode, Try Ubuntu option, does it load correctly? Can it load the live mode desktop and work on it?

---

### Post by pgs3223 on 2010-06-21
Yes I think so, I booted from the live CD (on a USB stick) and ran terminal from it to get the boot script I just posted.

---

### Post by darkod on 2010-06-21
Sorry, I can't see anything wrong right now. :(

---

### Post by oldfred on 2010-06-24
I like Darko do not see anything wrong. the script 'sees' the windows boot files & boot sector as if they are ok. Sometimes the window BCD gets confused or someother issue inside windows. Then about the only thing is to try all the windows repairs even reinstalling the windows boot loader. Of course you then have to reinstall grub after (if) you fix windows.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

Reinstall grub:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

After rebooting run
sudo update-grub

---

