---
title: "After Installing ubuntu 10.04 , windows 7 failed to start (status: 0xc0000225)"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by enavy on 2010-09-08
I've installed ubuntu in a HP laptop 64bits, for which I've deleted the Recovery and HP tools partitions using windows disk management and created a new partition "L" (NTFS) for linux; and then wih the gparted utility from the Ubuntu installation CD, I have formated L partition to ext4 and then installed Ubuntu on it. After this, I could not start windows (ubuntu starts without problem). I did try to use the recovery disc without success; using the utilities of the recovery disc, I've noticed that windows does not recognize the partition (C) in which win 7 is installed,but  it is visible form ubuntu instead, the only detail was that ubuntu did not show the partition name, for which I tried to change it to C using gparted without success.

---

### Post by oldfred on 2010-09-08
So we can see where everything is at, from liveCd run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Mark Phelps on 2010-09-09
Apparently, you messed with the Win7 OS partition using GParted.  Could tell that because you had to open it read/write in order to change the partition name.

Bad idea.  This runs the risk of corrupting the Win7 OS partition.

So, if it wasn't hosed up before, it's likely to be hosed up now.

In future, use only the Win7 utilities to mess with the Win7 OS partition.  Something to remember when you get Win7 back working.

---

### Post by enavy on 2010-09-13
[COLOR=black][FONT=Verdana]I followed the advice of Oldfred, and the results showed that there are not partition errors, and it did recognize the windows partition, but how can I get it back to work in windows?[/FONT][/COLOR]

---

### Post by oldfred on 2010-09-13
It helps if we can see the results.txt as it often is what is missing that is the problem. Post results.txt in the code (# on  edit panel) tags.

---

### Post by enavy on 2010-09-13
```

```                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   307,443,711   307,034,112  42 SFS
/dev/sda4         307,443,712   625,140,399   317,696,688  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        92D47C11D47BF5B7                       ntfs       SYSTEM                        
/dev/sda3        CE2A6BC92A6BACE1                       ntfs                                     
/dev/sda4        598fdc4f-dbc2-4048-968d-088c489f667b   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 598fdc4f-dbc2-4048-968d-088c489f667b
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 598fdc4f-dbc2-4048-968d-088c489f667b
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
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 598fdc4f-dbc2-4048-968d-088c489f667b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=598fdc4f-dbc2-4048-968d-088c489f667b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 598fdc4f-dbc2-4048-968d-088c489f667b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=598fdc4f-dbc2-4048-968d-088c489f667b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 598fdc4f-dbc2-4048-968d-088c489f667b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 598fdc4f-dbc2-4048-968d-088c489f667b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 92d47c11d47bf5b7
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ce2a6bc92a6bace1
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=598fdc4f-dbc2-4048-968d-088c489f667b /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


 295.0GB: boot/grub/core.img
 187.6GB: boot/grub/grub.cfg
 295.0GB: boot/initrd.img-2.6.32-21-generic
 294.9GB: boot/vmlinuz-2.6.32-21-generic
 295.0GB: initrd.img
 294.9GB: vmlinuz

---

### Post by oldfred on 2010-09-13
the windows in sda2 is a recovery or something and the install is sda3. It looks like sda3 has all the boot files but the boot flag is on sda2. Boot flag does not effect grub as it just jumps to the partition boot sector. Windows boot loader in the MBR needs to see the boot flag (active partition) to know what partition boot sector to jump to to continue booting.

Did you try booting sda3?

If not, move boot flag to sda3 and try windows repair tools. You can use gparted, disk Utility or command line.

set boot flag on for sda3 (off for others)
sudo sfdisk -A3 /dev/sda

It also says you have SFS partitions, which are a windows proprietary type but still NTFS. This sometimes has caused issues as I think windows stopped using it.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

If in windows repair you run fixMBR you will overwrite grub. That is ok if you want to confirm that windows boots ok, but you will have to reinstall grub2 to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by apple.kiddo on 2011-11-22
> **oldfred said:**
> the windows in sda2 is a recovery or something and the install is sda3. It looks like sda3 has all the boot files but the boot flag is on sda2. Boot flag does not effect grub as it just jumps to the partition boot sector. Windows boot loader in the MBR needs to see the boot flag (active partition) to know what partition boot sector to jump to to continue booting.

Did you try booting sda3?

If not, move boot flag to sda3 and try windows repair tools. You can use gparted, disk Utility or command line.

set boot flag on for sda3 (off for others)
sudo sfdisk -A3 /dev/sda

It also says you have SFS partitions, which are a windows proprietary type but still NTFS. This sometimes has caused issues as I think windows stopped using it.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

If in windows repair you run fixMBR you will overwrite grub. That is ok if you want to confirm that windows boots ok, but you will have to reinstall grub2 to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
Hello,

If you could help me on my problem i would really appreciate it.

I installed ubuntu 11.10 and i ended up messing my windows boot. I followed the boot_info_script part and i am attaching the info below:

So my win 7 exists on sda4 and the boot files are missing. How do i install the boot files on it and get back my windows ?

Thanks in advance,  


              Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       204797951 sectors, but according to the info from 
                       fdisk, it has 771973167 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63         2,047         1,985  42 SFS
/dev/sda2               2,048       206,847       204,800  42 SFS
/dev/sda3             208,894   204,795,903   204,587,010   5 Extended
/dev/sda5             208,896   188,413,951   188,205,056  83 Linux
/dev/sda6         188,416,000   204,795,903    16,379,904  82 Linux swap / Solaris
/dev/sda4         204,797,952   976,771,119   771,973,168  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        523E11C53E11A2D1                       ntfs       System Reserved
/dev/sda4        C07EC89B7EC88B9A                       ntfs       
/dev/sda5        4dce46a4-0a43-45db-86b2-b6995eed20bf   ext4       
/dev/sda6        e3284cc4-2e55-4144-9c4f-771558d40c65   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


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
search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
  set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    echo    'Loading Linux 3.0.0-13-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-13-generic-pae root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 4dce46a4-0a43-45db-86b2-b6995eed20bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 523E11C53E11A2D1
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
UUID=4dce46a4-0a43-45db-86b2-b6995eed20bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e3284cc4-2e55-4144-9c4f-771558d40c65 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-12-generic-pae           1
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/initrd.img-3.0.0-13-generic-pae           3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              2
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic-pae              2
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  19 96 27 7f 0a 59 15 a4  36 ed 8b 22 33 46 ec b9  |..'..Y..6.."3F..|
00000010  87 54 af b2 06 76 63 5b  9b 9a d1 6c f4 49 d7 38  |.T...vc[...l.I.8|
00000020  03 20 73 0a 27 51 f9 ce  96 8b 4e 31 14 95 2d 30  |. s.'Q....N1..-0|
00000030  63 2f 1e 38 5a 79 35 c1  5e 2c 0b fd 9e cc 35 9e  |c/.8Zy5.^,....5.|
00000040  7c 49 f9 9c f2 6e ad f2  77 c7 c3 44 c3 2e 61 a0  ||I...n..w..D..a.|
00000050  e2 a6 04 e1 25 c2 e3 e5  04 5b 44 a1 01 0b f5 e3  |....%....[D.....|
00000060  21 45 98 3d ba bc 7a 3a  db b6 4a 79 38 f3 38 63  |!E.=..z:..Jy8.8c|
00000070  6b 19 e5 04 6f 48 19 e8  ac 29 f5 06 04 b1 fc c2  |k...oH...)......|
00000080  81 f5 b9 5e 3f f1 f1 76  45 c4 7f f5 d5 2a 19 3f  |...^?..vE....*.?|
00000090  a2 58 fb 7b 44 0b fd 54  04 87 6f 47 f3 a3 f5 c2  |.X.{D..T..oG....|
000000a0  f6 57 55 96 05 05 c8 a1  3b 06 fb 78 c8 bc 53 79  |.WU.....;..x..Sy|
000000b0  e0 47 9a dc 62 9b 0c d1  25 f9 33 5e 9f 78 23 bc  |.G..b...%.3^.x#.|
000000c0  a9 96 c3 8b 08 a1 15 f7  26 2f e6 7c ef 85 86 06  |........&/.|....|
000000d0  41 af 42 52 5d f9 74 96  5c ac 83 71 2d 3e 3c ec  |A.BR].t.\..q-><.|
000000e0  76 9f 43 19 17 1e 1f 29  0b d9 04 e9 6b 36 47 05  |v.C....)....k6G.|
000000f0  94 90 27 b8 f8 f0 f1 d5  22 5b 5e 33 b1 52 34 ac  |..'....."[^3.R4.|
00000100  5a 5c 5b 6e ae 5f 85 e1  7e b3 ad af 95 28 1b c4  |Z\[n._..~....(..|
00000110  30 d1 49 a2 ac 76 b4 0a  13 2e 4a 4d 8f a6 b5 7b  |0.I..v....JM...{|
00000120  fb 1b fb a0 ea 99 fe 4f  a1 25 0b 76 e9 09 8d 8d  |.......O.%.v....|
00000130  70 50 7f f9 9c 13 bd 1b  97 a2 e6 6d 2d a7 29 90  |pP.........m-.).|
00000140  5f 7e 78 e8 38 09 e8 c9  5c 4d d1 70 1a f3 15 e7  |_~x.8...\M.p....|
00000150  b6 02 de 9b 1c db 3b 17  aa b8 40 1c 72 96 3b bf  |......;...@.r.;.|
00000160  d5 90 ba 45 7a 67 94 1e  72 e2 22 79 18 b3 08 dc  |...Ezg..r."y....|
00000170  37 e9 e4 51 1a c9 05 39  cf b8 6e 88 8d 47 db ac  |7..Q...9..n..G..|
00000180  7d 4c c0 1a 58 c0 01 b6  a0 1e 44 3c 25 48 f3 f8  |}L..X.....D<%H..|
00000190  c5 67 45 7e 45 de 2f 3b  90 60 bb 2b e6 c8 21 17  |.gE~E./;.`.+..!.|
000001a0  30 e6 e7 7d 04 7f e9 b8  9c d2 2b c9 97 9d 1d 1a  |0..}......+.....|
000001b0  fa d2 c4 7d 6a 60 0b 73  51 2e e7 9a 04 52 00 00  |...}j`.sQ....R..|
000001c0  34 0d 83 fe ff ff 02 00  00 00 00 c8 37 0b 00 fe  |4...........7...|
000001d0  ff ff 05 fe ff ff 02 c8  37 0b 00 f8 f9 00 00 00  |........7.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

