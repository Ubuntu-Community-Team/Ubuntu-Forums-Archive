---
title: "Increase Ubuntu Partition"
date: 2018-01-11
forum: Installation &amp; Upgrades
---

### Post by eureka117 on 2018-01-11
Hello, 

I am trying to increase the amount of space I have for my Ubuntu partition. What I'd like to do is shrink my windows10 partition by 30GB and take that unallocated space to increase my 48GB Ubuntu partition to 78GB. I'm concerned about how to go about doing it. I believe that if I shave off the 30GB I'll have to delete a windows recovery partition and the grub2.0 partition so the unallocated space is adjacent to the Ubuntu partition. I'm hesitent to do this because I believe if I do this, then I won't be able to boot into windows or Ubuntu. I'm mostly looking for advice on how to not get myself locked out of my own computer a week before school starts. 

Am I right about this folks?

Attached is a picture of my partition table.

---

### Post by TheFu on 2018-01-11
An option is to split off the partition from Windows and just mount the newly created partition (and ext4 file system!!!!) somewhere you can use it under Linux. It is very common to have Linux OS as 1 partition (about 25G) and everything else used for /home/.  This is considered a "best practice."     If you might add more storage and want to merge the different disks, then using LVM would be strongly recommended.

If you decide that having only 1 partition is mandatory, we need more/better information.  Please install boot-repair and run the boot-info tool. That will create a file full of the information we need to help.

However, with simple partitioning, like you appear to have used, it isn't possible to expand storage that isn't contiguous (side-by-side). There are other partitions between the main Windows NTFS and the Linux ext4 partitions.  Removing those might be a bad idea. Can't tell from here.

So, if I were trying to do this more complicated space cut and merge, I would
* make a know-I-can-restore backup for everything - bad things happen when screwing with partitions. Really bad things.
* Remove Linux - everything.
* Resize Windows, verify that everything on it is working.
* Install Linux, using LVM. This will provide lots and lots of flexibility in the future. It would have made this little problem much easier to solve. LVM lets you shrink, grow, merge storage areas on the same and different disks.
* Be happy.

In the end, I'd ensure my daily backups for the new setup were working perfectly.  Daily, versioned, backups are very important for lots and lots of reasons.

Another option is to split off all the large files from Windows that you want to access from Linux into a separate partition, use NTFS, then mount that NTFS area from Linux and Windows.  Of course, this depends on the types of files involved and it might not work.  When sharing NTFS partitions with Linux, there are a few Windows settings that need to be changed so Windows properly closes the file systems at shutdown. Otherwise, the file system will be left "open" and linux will refuse to open it.

---

### Post by yancek on 2018-01-11
As pointed out above, the problem you have is the only partition with enough size to use is sda4 and you have TWO partitions between that and your Ubuntu partition so they are not contiguous.  You may not need the BIOS boot partition as you also have an EFI partition but there is no way to know that from the info posted.

If you need more room for data with Ubuntu, the simplest thing to do would be to use the unallocated space you have highlighted and create a separate data partition and mount it and set to mount on boot with an entry in /etc/fstab.

---

### Post by oldfred on 2018-01-11
Do not use the Ubuntu live installers option for LVM. That erases entire drive. And you cannot restore a Windows partition into the LVM as it is not supported.
You can manually create LVM on part of a drive.

---

### Post by TheFu on 2018-01-11
Thanks for clarifying oldfred!!!  I left of those EXTREMELY IMPORTANT items.  Actually, for someone really new to Linux attempting to use LVM in this way will likely be too difficult with data loss highly likely.  I find the LVM manual setup during the OS install less-than-intuitive to use and I've been using LVM for almost 20 yrs.

---

### Post by eureka117 on 2018-01-12
Thank you for your response TheFu. Here is the output of my boot-info. The boot-repair tool crashed unexpectantly, so it didn't load up a URL. 


```




ot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]




============================= Boot Info Summary: ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    834342912 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt7)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Acronis/bootwiz.efi 
                       /EFI/Boot/bootx64.efi /EFI/ubuntu/fbx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/HP/boot/bootmgfw.efi /EFI/HP/boot/bootmgr.efi 
                       /EFI/HP/boot/memtest.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/HP/EFI/Boot/bootx64.efi


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda6: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sda7: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  KDE neon LTS User Edition 5.8
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img


sda9: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   937,703,087   937,703,087  ee GPT




GUID Partition Table detected.


Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1      R          2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2               821,248     1,353,727       532,480 EFI System partition
/dev/sda3             1,353,728     1,615,871       262,144 Data partition (Windows/Linux)
/dev/sda4             1,615,872   832,517,079   830,901,208 Data partition (Windows/Linux)
/dev/sda5      R    832,518,144   834,342,911     1,824,768 Windows Recovery Environment (Windows)
/dev/sda6           834,342,912   834,344,959         2,048 BIOS Boot partition
/dev/sda7           834,344,960   936,744,959   102,400,000 Data partition (Linux)
/dev/sda9           936,744,960   937,701,375       956,416 Data partition (Windows/Linux)


Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 7.5 GiB, 8029470208 bytes, 15682559 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


/dev/sdb1 ends after the last sector of /dev/sdb


GUID Partition Table detected.


Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048    15,682,525    15,680,478 Data partition (Windows/Linux)


Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        DA80E26C80E24E97                       ntfs       WINRE
/dev/sda2        305F-E03A                              vfat       
/dev/sda3        782282B422827742                       ntfs       
/dev/sda4        8868F00968EFF43A                       ntfs       
/dev/sda5        A67872FD7872CB95                       ntfs       
/dev/sda6                                                          
/dev/sda7        1bb9780c-7e8d-4455-9e08-7d95466fb58b   ext4       
/dev/sda9        40A0F0ADA0F0AA94                       ntfs       
/dev/sdb1        DA5E-6D1F                              vfat       UBUNTU 16_0
/dev/sr1         2008-05-06-12-26-42-                   iso9660    U3 System


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jan 12 22:25 ata-SSD2SC480G1CS1754D117-514_PNY36150000877641959-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Jan 12 17:21 ata-hp_BDDVDRW_CT40N_KV3CBAJ3416 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan 12 22:25 usb-SanDisk_Cruzer_4320201DAA434660-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan 12 22:25 usb-SanDisk_Cruzer_4320201DAA434660-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jan 12 17:21 usb-SanDisk_Cruzer_4320201DAA434660-0:1 -> ../../sr1
lrwxrwxrwx 1 root root  9 Jan 12 17:21 wwn-0x5001480000000000 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan 12 22:25 wwn-0x5f8db4c365641959 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jan 12 22:25 wwn-0x5f8db4c365641959-part9 -> ../../sda9


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




========================== sda2/EFI/ubuntu/grub.cfg: ===========================


--------------------------------------------------------------------------------
search.fs_uuid c5db33d9-d729-4c78-8905-eeff6b4ad8f0 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------


=========================== sda7/boot/grub/grub.cfg: ===========================


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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
else
  search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
else
  search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
fi
insmod gfxmenu
loadfont ($root)/boot/grub/themes/breeze/unifont-bold-16.pf2
loadfont ($root)/boot/grub/themes/breeze/unifont-regular-14.pf2
loadfont ($root)/boot/grub/themes/breeze/unifont-regular-16.pf2
loadfont ($root)/boot/grub/themes/breeze/unifont-regular-32.pf2
insmod png
set theme=($root)/boot/grub/themes/breeze/theme.txt
export theme
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=5
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=5
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'GNU/Linux' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1bb9780c-7e8d-4455-9e08-7d95466fb58b' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
    else
      search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
    fi
        linux    /boot/vmlinuz-4.10.0-38-generic root=UUID=1bb9780c-7e8d-4455-9e08-7d95466fb58b ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.10.0-38-generic
}
submenu 'Advanced options for GNU/Linux' $menuentry_id_option 'gnulinux-advanced-1bb9780c-7e8d-4455-9e08-7d95466fb58b' {
    menuentry 'GNU/Linux, with Linux 4.10.0-38-generic' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-38-generic-advanced-1bb9780c-7e8d-4455-9e08-7d95466fb58b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
        else
          search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
        fi
        echo    'Loading Linux 4.10.0-38-generic ...'
            linux    /boot/vmlinuz-4.10.0-38-generic root=UUID=1bb9780c-7e8d-4455-9e08-7d95466fb58b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-38-generic
    }
    menuentry 'GNU/Linux, with Linux 4.10.0-38-generic (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-38-generic-recovery-1bb9780c-7e8d-4455-9e08-7d95466fb58b' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
        else
          search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
        fi
        echo    'Loading Linux 4.10.0-38-generic ...'
            linux    /boot/vmlinuz-4.10.0-38-generic root=UUID=1bb9780c-7e8d-4455-9e08-7d95466fb58b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-38-generic
    }
    menuentry 'GNU/Linux, with Linux 4.10.0-37-generic' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-37-generic-advanced-1bb9780c-7e8d-4455-9e08-7d95466fb58b' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
        else
          search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
        fi
        echo    'Loading Linux 4.10.0-37-generic ...'
            linux    /boot/vmlinuz-4.10.0-37-generic root=UUID=1bb9780c-7e8d-4455-9e08-7d95466fb58b ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-37-generic
    }
    menuentry 'GNU/Linux, with Linux 4.10.0-37-generic (recovery mode)' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-37-generic-recovery-1bb9780c-7e8d-4455-9e08-7d95466fb58b' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
        else
          search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
        fi
        echo    'Loading Linux 4.10.0-37-generic ...'
            linux    /boot/vmlinuz-4.10.0-37-generic root=UUID=1bb9780c-7e8d-4455-9e08-7d95466fb58b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.10.0-37-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
    else
      search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  1bb9780c-7e8d-4455-9e08-7d95466fb58b
    else
      search --no-floppy --fs-uuid --set=root 1bb9780c-7e8d-4455-9e08-7d95466fb58b
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-8868F00968EFF43A' {
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  8868F00968EFF43A
    else
      search --no-floppy --fs-uuid --set=root 8868F00968EFF43A
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------


=============================== sda7/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=1bb9780c-7e8d-4455-9e08-7d95466fb58b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=1ed2bdd5-c1ef-4448-b278-3011e2889591 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda7: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 402.931385040 = 432.644280320  boot/grub/grub.cfg                             1
 424.614353180 = 455.926190080  boot/grub/i386-pc/core.img                     1
 417.509761810 = 448.297693184  boot/vmlinuz-4.10.0-37-generic                 1
 436.616191864 = 468.813066240  boot/vmlinuz-4.10.0-38-generic                 1
 436.616191864 = 468.813066240  vmlinuz                                        1
 417.509761810 = 448.297693184  vmlinuz.old                                    1
 435.677871704 = 467.805552640  boot/initrd.img-4.10.0-37-generic              3
 436.815425873 = 469.026992128  boot/initrd.img-4.10.0-38-generic              2
 436.815425873 = 469.026992128  initrd.img                                     2
 435.677871704 = 467.805552640  initrd.img.old                                 3


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


============================== sdb1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/grub.cfg                             1


================= sdb1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             syslinux.cfg                                   1


=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/5472/mounts) leaked on lvs invocation. Parent PID 19290: bash
File descriptor 63 (pipe:[49116]) leaked on lvs invocation. Parent PID 19290: bash


ADDITIONAL INFORMATION :
=================== log of boot-info 20180112_2225 ===================
boot-info version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 has been opened read-only.
Error: /dev/sr1: unrecognised disk label
boot-info is executed in live-session (Ubuntu 16.04.3 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory


=================== os-prober:
/dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda7:KDE neon LTS User Edition 5.8 (16.04):neon:linux


=================== blkid:
/dev/sda1: LABEL="WINRE" UUID="DA80E26C80E24E97" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="eb76a59e-2ea4-448f-8806-228fe63be4c1"
/dev/sda2: UUID="305F-E03A" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="4e860a2f-6f6b-49da-9906-a361fb08e902"
/dev/sda3: UUID="782282B422827742" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="f09fba20-ed63-01d2-10d9-47f8b176e900"
/dev/sda4: UUID="8868F00968EFF43A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="4cf56599-8bfb-4fd4-aed2-b48400324f8d"
/dev/sda5: UUID="A67872FD7872CB95" TYPE="ntfs" PARTUUID="aee13b55-37ce-4a6e-8697-7d7dfb1dcd09"
/dev/sda7: UUID="1bb9780c-7e8d-4455-9e08-7d95466fb58b" TYPE="ext4" PARTUUID="43357c90-610c-444e-b6fa-60d48f275a99"
/dev/sda9: UUID="40A0F0ADA0F0AA94" TYPE="ntfs" PARTUUID="6158d366-3845-11e7-af8e-d37621706d99"
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="DA5E-6D1F" TYPE="vfat" PARTLABEL="Microsoft Basic Data" PARTUUID="fea57502-7105-4433-a5f4-53e090aa438b"
/dev/loop0: TYPE="squashfs"
/dev/sr1: UUID="2008-05-06-12-26-42-" LABEL="U3 System" TYPE="iso9660"
/dev/sda6: PARTUUID="149bbb75-f2a7-4657-ab7c-65b1b06bd230"




1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


Windows not detected by os-prober on sda4.
Linux not detected by os-prober on sda6. Please report this message to boot.repair@gmail.com
=================== No kernel in /mnt/boot-sav/sda2/boot:
boot.sdi




Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi


=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Oct 29 01:41 grub.d
total 80
-rwxr-xr-x 1 root root  9791 May 20  2017 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 May 20  2017 10_linux
-rwxr-xr-x 1 root root 11082 May 20  2017 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 20  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 May 20  2017 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 20  2017 40_custom
-rwxr-xr-x 1 root root   216 May 20  2017 41_custom
-rw-r--r-- 1 root root   483 May 20  2017 README








=================== sda7/etc/default/grub :


GRUB_THEME=/boot/grub/themes/breeze/theme.txt


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"


GRUB_CMDLINE_LINUX=""








=================== sda7recordfail=1/grub/grubenv :
recordfail=1








=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     204 Aug  1 11:28 grub.d
total 57
-rwxr-xr-x 1 root root  9791 Jun 21  2017 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 Jun 21  2017 10_linux
-rwxr-xr-x 1 root root 11082 Jun 21  2017 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jun 21  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 Jun 21  2017 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 21  2017 40_custom
-rwxr-xr-x 1 root root   216 Jun 21  2017 41_custom
-rw-r--r-- 1 root root   483 Jun 21  2017 README








=================== /etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






=================== No kernel in /boot:
abi-4.10.0-28-generic
config-4.10.0-28-generic
grub
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-4.10.0-28-generic






=================== efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 3003,3000,3002,2001,2002,2003
Boot0000* Acronis loader    HD(2,GPT,4e860a2f-6f6b-49da-9906-a361fb08e902,0xc8800,0x82000)/File(EFIAcronisbootwiz.efi)RestoreFake_tag
Boot0001* Notebook Hard Drive    BBS(HD, \FF ,0x0).......................................................................
Boot0002* Ubuntu    HD(2,GPT,4e860a2f-6f6b-49da-9906-a361fb08e902,0xc8800,0x82000)/File(EFIubuntugrubx64.efi)RC
Boot0003* Windows Boot Manager    HD(2,GPT,4e860a2f-6f6b-49da-9906-a361fb08e902,0xc8800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...n............. ...
Boot0004* USB Hard Drive - SanDisk Cruzer    BBS(7,
\FF ,0x500).......................................................................
Boot0005* USB Hard Drive (UEFI) - <null string>    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/Unit(0)/HD(1,GPT,fea57502-7105-4433-a5f4-53e090aa438b,0x800,0xef43de)RC
Boot000A* Internal Hard Disk or Solid State Disk    RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-kernel,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda7.
sda9    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda9.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    no-kernel,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    is-biosboot, .


sda    : GPT,    BIOS_boot,    has-correctEFI,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes




=================== parted -lm:


BYT;
/dev/sda:480GB:scsi:512:512:gpt:ATA SSD2SC480G1CS175:;
1:1049kB:420MB:419MB:ntfs:Basic data partition:hidden, diag;
2:420MB:693MB:273MB:fat32:EFI system partition:boot, esp;
3:693MB:827MB:134MB:ntfs:Basic data partition:msftdata;
4:827MB:426GB:425GB:ntfs:Basic data partition:msftdata;
5:426GB:427GB:934MB:ntfs::hidden, diag;
6:427GB:427GB:1049kB:::bios_grub;
7:427GB:480GB:52.4GB:ext4::;
9:480GB:480GB:490MB:ntfs::msftdata;


BYT;
/dev/sdb:8029MB:scsi:512:512:gpt:SanDisk Cruzer:;
1:1049kB:8029MB:8028MB:fat32:Microsoft Basic Data:msftdata;


BYT;
/dev/sr1:101MB:unknown:2048:2048:unknown:Unknown:;


=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk            7.5G
sdb1  part vfat       7.5G UBUNTU 16_0
sr0   rom            1024M
loop0 loop squashfs   1.4G
sda   disk          447.1G
sda4  part ntfs     396.2G
sda2  part vfat       260M
sda9  part ntfs       467M
sda7  part ext4      48.8G
sda5  part ntfs       891M
sda3  part ntfs       128M
sda1  part ntfs       400M WINRE
sda6  part              1M
sr1   rom  iso9660     96M U3 System


KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs
sda      0  0  0 running
sda4     0  0  0         /mnt/boot-sav/sda4
sda2     0  0  0         /mnt/boot-sav/sda2
sda9     0  0  0         /mnt/boot-sav/sda9
sda7     0  0  0         /mnt/boot-sav/sda7
sda5     0  0  0         /mnt/boot-sav/sda5
sda3     0  0  0         /mnt/boot-sav/sda3
sda1     0  0  0         /mnt/boot-sav/sda1
sda6     0  0  0
sr1      1  0  1 running




=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8142548k,nr_inodes=2035637,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1631720k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=2474ee88c3c58db2)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=33,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14990)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1631720k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw,relatime,data=ordered)
/dev/sda9 on /mnt/boot-sav/sda9 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 dvd dvdrw ecryptfs fb0 fb1 fd freefall full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-18 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda9 sdb sdb1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 7f 0c 00 00 00 00 00  |................|
00000030  55 85 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  97 4e e2 80 6c e2 80 da  |.........N..l...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 0c 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 3a e0 5f 30 4e  4f 20 4e 41 4d 45 20 20  |..):._0NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 01 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 14 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff 03 00 00 00 00 00  |................|
00000030  55 55 01 00 00 00 00 00  10 00 00 00 00 00 00 00  |UU..............|
00000040  02 00 00 00 08 00 00 00  42 77 82 22 b4 82 22 78  |........Bw.".."x|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 18 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  d7 8b 86 31 00 00 00 00  |...........1....|
00000030  00 00 0c 00 00 00 00 00  e5 b8 7c 03 00 00 00 00  |..........|.....|
00000040  f6 00 00 00 01 00 00 00  3a f4 ef 68 09 f0 68 88  |........:..h..h.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 9f 31  |........?....8.1|
00000020  00 00 00 00 80 00 80 00  ff d7 1b 00 00 00 00 00  |................|
00000030  00 29 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |.)..............|
00000040  f6 00 00 00 01 00 00 00  95 cb 72 78 fd 72 78 a6  |..........rx.rx.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda9
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 98 d5 37  |........?......7|
00000020  00 00 00 00 80 00 80 00  ff 97 0e 00 00 00 00 00  |................|
00000030  aa 9b 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  94 aa f0 a0 ad f0 a0 40  |...............@|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200


=================== df -Th:


Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.4M  1.6G   1% /run
/dev/sdb1      vfat      7.5G  1.5G  6.0G  20% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      7.8G   52M  7.8G   1% /
tmpfs          tmpfs     7.8G  172K  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.8G   32K  7.8G   1% /tmp
tmpfs          tmpfs     1.6G   80K  1.6G   1% /run/user/999
/dev/sda1      fuseblk   400M  234M  167M  59% /mnt/boot-sav/sda1
/dev/sda2      vfat      256M  123M  134M  48% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   128M  7.9M  121M   7% /mnt/boot-sav/sda3
/dev/sda4      fuseblk   397G  315G   83G  80% /mnt/boot-sav/sda4
/dev/sda5      fuseblk   891M  351M  541M  40% /mnt/boot-sav/sda5
/dev/sda7      ext4       48G   22G   24G  48% /mnt/boot-sav/sda7
/dev/sda9      fuseblk   467M   10M  458M   3% /mnt/boot-sav/sda9


=================== fdisk -l:
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 50CE0B53-5FBA-4355-B34A-ADE60200E10B


Device         Start       End   Sectors   Size Type
/dev/sda1       2048    821247    819200   400M Windows recovery environment
/dev/sda2     821248   1353727    532480   260M EFI System
/dev/sda3    1353728   1615871    262144   128M Microsoft basic data
/dev/sda4    1615872 832517079 830901208 396.2G Microsoft basic data
/dev/sda5  832518144 834342911   1824768   891M Windows recovery environment
/dev/sda6  834342912 834344959      2048     1M BIOS boot
/dev/sda7  834344960 936744959 102400000  48.8G Linux filesystem
/dev/sda9  936744960 937701375    956416   467M Microsoft basic data








Disk /dev/sdb: 7.5 GiB, 8029470208 bytes, 15682559 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C6FE4DE2-092A-4EE9-9467-841A3A65F11F


Device     Start      End  Sectors  Size Type
/dev/sdb1   2048 15682525 15680478  7.5G Microsoft basic data








=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of sda7, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file




=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!


If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi




=================== User settings
The settings chosen by the user will not act on the boot.





```

---

### Post by TheFu on 2018-01-12
Did you decide which option to go with?

I would go with the easiest one, shrink sda4, create a new partition there, create an ext4 file system and mount that new storage inside Linux, probably for /home/

---

### Post by oldfred on 2018-01-12
You do not have lots of room on your drive.
Windows NTFS partitions like 30% free, at 20% free they start to slow down and at 10% you just about cannot do a defrag as you have no working room.
Linux partitions also need extra space, but not quite as much as Windows.

You also have Ubuntu in BIOS boot mode which uses the 1MB bios_grub partition but at some point had it installed in UEFI mode as you have an ubuntu entry in UEFI. HP makes it a bit more difficult to use UEFI and dual boot, but there are multiple work arounds.

You can delete the bios_grub and recreate it anywhere on drive and re-install grub in BIOS mode, or convert to UEFI boot.
Then you probably want to backup sda5, but then can also move it all the way left using gparted or Windows tools.
Then you can move the Linux partition all the way left and then expand right. The moves can be slow and any interruption will totally corrupt data so be sure to have good backups. While gparted allows you to queue tasks always run one at a time and make sure it completes correctly. 

On my Dell, when I did a Windows backup to flash drive, it offered to delete that partition. Same with a Dell partition, once I backed it up, it offered to delete it. Both were using Windows or Dell tools for the backup.

---

### Post by C.S.Cameron on 2018-01-12
Yesterday I shrunk Windows partition using Windows and moved and/or expanded the other partitions using gparted. I had a little trouble moving the /home partition and should probably have left it where it was.

---

### Post by eureka117 on 2018-01-15
Here's what I have done so far. I have cleared up over 130GB of space on my sda4 partition. So now I have
tons of space. I used clonezilla to back up sda7 and sda5. Now oldFred, about deleting grub- how do I install it to the proper location after I delete it? Further, wouldn't the computer not be able to boot into linux after I delete the bios_grub partition? My fear is that this situation happens and I'm left scrambling searching desperately around on the internet trying to figure out what to do. 


I clicked on the links in your signature, about UEFI installing. Is the guide I seek on that post? I don't want to have to reinstall my entire distribution again if it is not absolutely necessary.

---

### Post by oldfred on 2018-01-16
If working from live installer, you can delete bios_grub, create new bios_grub in preferred location and reinstall grub.
Yes when you have deleted bios_grub partition, you break grub so system will not boot. But if you immediately reinstall grub everything should be ok.

Most use Boot-Repair from live installer to install or reinstall grub. Often if autofix does not work then the full un-install/reinstall of grub  from advanced options does work. And if multiple installs of Ubuntu or multiple drives, Boot-Repair should only be used in advanced mode.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Link below in my signature is primarily for UEFI installs. Since also info on gpt, that part may be useful. And the parts on general use like partitioning, backup and some other info may be useful even if not UEFI. But lots of detail. New users often do not even know what BIOS, UEFI or gpt are (see acronyms), but are overwhelmed.

---

### Post by eureka117 on 2018-02-16
It has been nearly a month since I opened this thread and so much has changed since then. Ultimately I did solve my problem. I increased my Linux partition and now have about 150GB for it. I did my best to follow OldFred&#8217;s advice about how to reinstall GRUB2, but alas I ran into problems that I could not surmount. The boot-repair tool was buggy for me and it ended up messing up my wifi card so I could not properly use the wifi on Linux (but it works okay with Windows). Ultimately I decided to just back up the partition and copy the home folder to a back up folder on a separate hard drive. Then I formatted and reinstalled KDE 5.11 on my partition and it works great now.  
 
 
 I&#8217;m so happy to have received so much outstanding support through the forums. Thank you so much you guys! You really helped me learn more about my system and helped me find a deeper appreciation for Linux.

---

