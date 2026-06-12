---
title: "Dual boot Windows 10 / External USB disk with Ubuntu"
date: 2019-05-28
forum: Installation &amp; Upgrades
---

### Post by urrfaust on 2019-05-28
Hello everyone,

I have an issue whiel dual booting Windows 10 and Ubuntu on an external USB disk.
This is the current setup:
 - old fujitsu siemens desktop (Esprimo P 5270), about 2008, I think, BIOS is up to date.
 - Internal Sata Drive with Windows 10 installed
 - External (eSATA) disk used as backup
 - External USB Disk with Ubuntu Cosmic
 - external USB flash with Ubuntu Live

Windows 10 boots without problems.
The issue is when I try to boot Ubuntu. The GRUB menu does not appear and Windows 10 gets booted. Sometimes, and this I don't really understand, I can access the GRUB menu by pressing F8 just after the BIOS boot sequence. Other times this does not work.
A few more interesting info:

- The Ubuntu external disk boots ok on other pcs
- If I disconnect the internal Win10 disk, Grub menu is displayed and Ubuntu boots OK
- I have tried to install Grub on the second internal SATA disk (the backup one). If I disconnect the Windows 10, Grub menu is displayed. When I reconnect it, I get a grub rescue prompt with "cannot find device..." message

I have attached a screeshot from gparted

And here is the result of parted -l
```

sudo parted -l
Model: ATA ST3160815AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  160GB  160GB  primary  ntfs         boot


Model: ATA ST1000LM048-2E71 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  843GB   843GB  primary  ntfs
 2      843GB   1000GB  157GB  primary  ntfs


Model: Corsair Voyager (scsi)
Disk /dev/sdc: 31.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.1GB  31.1GB  primary  fat32        boot, lba


Model: WD My Passport 0830 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      54.2MB  41.9GB  41.9GB  primary   ntfs
 2      41.9GB  497GB   455GB   extended                  lba
 5      41.9GB  42.3GB  365MB   logical   ext4            boot
 6      42.3GB  64.4GB  22.1GB  logical   ext4
 7      64.4GB  497GB   433GB   logical   ext4
 3      497GB   500GB   2746MB  primary   linux-swap(v1)


```

and /etc/default/grub

```

# If yu change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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

```

bootinfoscript
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 130 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdc5 
                       and looks at sector 82399874 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 130 for .
    Operating System:  
    Boot files:        /grub/grub.cfg /extlinux/extlinux.conf

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.10
    Boot files:        /etc/fstab

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 149,1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,646,321,663 1,646,319,616   7 NTFS / exFAT / HPFS
/dev/sdb2       1,646,321,664 1,953,519,615   307,197,952   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 465,7 GiB, 500074283008 bytes, 976707584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1             105,903    81,920,159    81,814,257   7 NTFS / exFAT / HPFS
/dev/sdc2          81,922,048   971,343,871   889,421,824   f W95 Extended (LBA)
/dev/sdc5    *     81,924,096    82,636,799       712,704  83 Linux
/dev/sdc6          82,638,848   125,753,343    43,114,496  83 Linux
/dev/sdc7         125,755,392   971,343,871   845,588,480  83 Linux
/dev/sdc3         971,343,872   976,707,583     5,363,712  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop15                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/sda1        FC20A31C20A2DD40                       ntfs       
/dev/sdb1        AE74F53474F4FFBF                       ntfs       External
/dev/sdb2        EE6608AD6608791B                       ntfs       Backup
/dev/sdc1        187C5C427C5C1D36                       ntfs       Windows
/dev/sdc3        5e20e480-272f-455a-802d-ea42bb902656   swap       
/dev/sdc5        f316c437-0b83-4111-8c61-79134d213b0f   ext4       boot
/dev/sdc6        811ae150-da31-4652-93bb-8ce73dc3c93e   ext4       
/dev/sdc7        d999457a-97db-4724-8a71-e6d08ba55709   ext4       home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/simone/External   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdb2        /media/simone/Backup     fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc1        /media/simone/Windows    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc5        /boot                    ext4       (rw,relatime)
/dev/sdc6        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdc7        /home                    ext4       (rw,relatime,stripe=32738)


================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /bootlog
[spybotsd]
timeout.old=30
--------------------------------------------------------------------------------

============================= sdc5/grub/grub.cfg: ==============================

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
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
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
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
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
insmod part_msdos
insmod ext2
set root='hd2,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos6 --hint-efi=hd2,msdos6 --hint-baremetal=ahci2,msdos6  811ae150-da31-4652-93bb-8ce73dc3c93e
else
  search --no-floppy --fs-uuid --set=root 811ae150-da31-4652-93bb-8ce73dc3c93e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=C
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-811ae150-da31-4652-93bb-8ce73dc3c93e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
    else
      search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
    fi
    linux    /vmlinuz-4.18.0-20-generic root=UUID=811ae150-da31-4652-93bb-8ce73dc3c93e ro  quiet splash $vt_handoff
    initrd    /initrd.img-4.18.0-20-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-811ae150-da31-4652-93bb-8ce73dc3c93e' {
    menuentry 'Ubuntu, with Linux 4.18.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-20-generic-advanced-811ae150-da31-4652-93bb-8ce73dc3c93e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
        else
          search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
        fi
        echo    'Loading Linux 4.18.0-20-generic ...'
        linux    /vmlinuz-4.18.0-20-generic root=UUID=811ae150-da31-4652-93bb-8ce73dc3c93e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.18.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-20-generic-recovery-811ae150-da31-4652-93bb-8ce73dc3c93e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
        else
          search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
        fi
        echo    'Loading Linux 4.18.0-20-generic ...'
        linux    /vmlinuz-4.18.0-20-generic root=UUID=811ae150-da31-4652-93bb-8ce73dc3c93e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.18.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-10-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-10-generic-advanced-811ae150-da31-4652-93bb-8ce73dc3c93e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
        else
          search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
        fi
        echo    'Loading Linux 4.18.0-10-generic ...'
        linux    /vmlinuz-4.18.0-10-generic root=UUID=811ae150-da31-4652-93bb-8ce73dc3c93e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.18.0-10-generic
    }
    menuentry 'Ubuntu, with Linux 4.18.0-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.18.0-10-generic-recovery-811ae150-da31-4652-93bb-8ce73dc3c93e' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
        else
          search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
        fi
        echo    'Loading Linux 4.18.0-10-generic ...'
        linux    /vmlinuz-4.18.0-10-generic root=UUID=811ae150-da31-4652-93bb-8ce73dc3c93e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-4.18.0-10-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
    else
      search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
    fi
    knetbsd    /memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos5 --hint-efi=hd2,msdos5 --hint-baremetal=ahci2,msdos5  f316c437-0b83-4111-8c61-79134d213b0f
    else
      search --no-floppy --fs-uuid --set=root f316c437-0b83-4111-8c61-79134d213b0f
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-FC20A31C20A2DD40' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  FC20A31C20A2DD40
    else
      search --no-floppy --fs-uuid --set=root FC20A31C20A2DD40
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Microsoft Windows XP Professional (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-187C5C427C5C1D36' {
    insmod part_msdos
    insmod ntfs
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  187C5C427C5C1D36
    else
      search --no-floppy --fs-uuid --set=root 187C5C427C5C1D36
    fi
    parttool ${root} hidden-
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

========================= sdc5/extlinux/extlinux.conf: =========================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc5: Version of COM32(R) files used by Syslinux: ===============

 extlinux/chain.c32                 :  COM32R module (v4.xx)

=============================== sdc6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd6 during installation
UUID=811ae150-da31-4652-93bb-8ce73dc3c93e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdd5 during installation
UUID=f316c437-0b83-4111-8c61-79134d213b0f /boot           ext4    defaults        0       2
# /home was on /dev/sdd7 during installation
UUID=d999457a-97db-4724-8a71-e6d08ba55709 /home           ext4    defaults        0       2
# swap was on /dev/sdd3 during installation
UUID=5e20e480-272f-455a-802d-ea42bb902656 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


============== sdc6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-fI03kqG8/Tmp_Log: File o directory non esistente
cat: /tmp/BootInfo-fI03kqG8/Tmp_Log: File o directory non esistente
cat: /tmp/BootInfo-fI03kqG8/Tmp_Log: File o directory non esistente 

```

---

### Post by yancek on 2019-05-28
Your output shows 4 hard drives of  varying sizes.  3 have only windows partitions while the 3rd (sdd 500GB drive) has both windows and Linux partitions.  The bootinfoscript output shows that you installed Grub boot code to the MBR of sdc (31GB drive) and your Ubuntu is on sdd.  If you can boot Ubuntu, you should install Grub to the MBR of sdd:  sudo grub-install /dev/sdd  and after doing that run:  sudo update-grub and then set the 500GB drive (sdd) to first boot priority in the BIOS.

Is your windows 10 and update from 7?  It's a bit unusual to have windows 10 on a Legacy drive and not UEFI/GPT.

I'm not sure if the bootinfoscript output is correct as you say you can boot Ubuntu on the external drive but bootinfoscript shows no boot code in the MBR?  You might try setting sdd to first boot priority in the BIOS or sdc which shows boot code in the MBR?

---

### Post by oldfred on 2019-05-28
Not sure how you are booting. Grub in MBR does not look correct, is it using a Windows boot loader to load the grub in the partition boot sector. That is not a particularly good way.

I would reinstall grub to MBR of sdc.
But with you multiple external drives you may have drive number issues. I have that when I boot an install from my flash drive.
You show this which BIOS, grub see as third drive, hd0, hd1 & hd2. But if you directly boot the hd2 drive, it is the hd0. And if you plug drives in a different order it may be anything. I often have boot error, realize my drive order has changed and in grub manually edit the hd2 to hd0. In some cases I was not sure what drive it was and experimented until it worked.
set root='[COLOR=#ff0000]hd2[/COLOR],msdos5'

It is supposed to use UUID, and find that, but sometimes with external drives it stops looking and gets lost?

---

### Post by urrfaust on 2019-05-28
Yes I  did an upgrade Win7->Win10.
I did install grub to sdd but to no avail.

> **yancek said:**
> Your output shows 4 hard drives of  varying sizes.  3 have only windows partitions while the 3rd (sdd 500GB drive) has both windows and Linux partitions.  The bootinfoscript output shows that you installed Grub boot code to the MBR of sdc (31GB drive) and your Ubuntu is on sdd.  If you can boot Ubuntu, you should install Grub to the MBR of sdd:  sudo grub-install /dev/sdd  and after doing that run:  sudo update-grub and then set the 500GB drive (sdd) to first boot priority in the BIOS.

Is your windows 10 and update from 7?  It's a bit unusual to have windows 10 on a Legacy drive and not UEFI/GPT.

I'm not sure if the bootinfoscript output is correct as you say you can boot Ubuntu on the external drive but bootinfoscript shows no boot code in the MBR?  You might try setting sdd to first boot priority in the BIOS or sdc which shows boot code in the MBR?

---

### Post by urrfaust on 2019-05-28
How do you see that a Windows boot loader is loading grub in the partition boot sector?
How do I check what grub sees what?

> **oldfred said:**
> Not sure how you are booting. Grub in MBR does not look correct, is it using a Windows boot loader to load the grub in the partition boot sector. That is not a particularly good way.

I would reinstall grub to MBR of sdc.
But with you multiple external drives you may have drive number issues. I have that when I boot an install from my flash drive.
You show this which BIOS, grub see as third drive, hd0, hd1 & hd2. But if you directly boot the hd2 drive, it is the hd0. And if you plug drives in a different order it may be anything. I often have boot error, realize my drive order has changed and in grub manually edit the hd2 to hd0. In some cases I was not sure what drive it was and experimented until it worked.
set root='[COLOR=#ff0000]hd2[/COLOR],msdos5'

It is supposed to use UUID, and find that, but sometimes with external drives it stops looking and gets lost?

---

### Post by oldfred on 2019-05-28
Did drive change to sdd? Then it will install as hd3, but when directly booting it needs to be hd0. 
When booting if you get grub menu, change boot entry to hd0.

Re-looking at it the grub in the partition boot sector also refers to partition 130. Not sure if its grub or old version of bootinfoscript. Try using Boot-Repair from Ubuntu live installer.
```
=> Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in [COLOR=#ff0000]partition 130[/COLOR] for .

sdc5: _______________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdc5 
                       and looks at sector 82399874 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in [COLOR=#ff0000]partition 130 [/COLOR]for .

```

Only install grub to MBR of drive with Ubuntu. Some USB boot configurations have the now very old BIOS issue of boot files must be near (within first 137GB) of a drive. New UEFI based systems do not have this issue. You have a /boot and smaller / (root) inside the normal limit, but do have a larger NTFS partition at beginning of drive. Should not be an issue.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by urrfaust on 2019-05-28
boot-info report [http://paste.ubuntu.com/p/qX2yVgVsrd/](http://paste.ubuntu.com/p/qX2yVgVsrd/)

---

### Post by oldfred on 2019-05-28
It still looks like a drive order issue.
All your drives want to be first, or need to be first when booted.

Only if Boot-Repair does not overwrite the Windows boot loader in sda, should you run the autofix. With internal drives, it always wants to install grub to every MBR, but with external drives it knows to only install it to the external drive's MBR.

But when booting you may have to edit the grub entries to be the correct hdX. When directly booted it it hd0, When booted from another drive it may be hd1. But external drives mount depending on BIOS, so you may just have to experiment.

At grub menu, use e for edit and change hdX to correct drive. Depending on which grub you are using, it may vary.

```
    set root='[COLOR=#ff0000]hd2[/COLOR],msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=[COLOR=#ff0000]hd2[/COLOR],msdos5 --hint-efi=[COLOR=#ff0000]hd2[/COLOR],msdos5 --hint-baremetal=[COLOR=#ff0000]ahci2[/COLOR],msdos5  f316c437-0b83-4111-8c61-79134d213b0f
    
```
If booting directly from external, all the 2 should be 0. But if from grub on internal drive, it may be 1 or some other drive number.
If once you boot from external's grub, run this and it will update those entries to all be 0.
sudo update-grub

---

### Post by urrfaust on 2019-05-29
I tried changing hd2 to hd0 in grub and ran update-grub. Restarted and it still booted win10.
It seems that grub menu shows up only when I turn on the pc i.e. cold start.  If I restart it, it doesn’t show. It is probably a BIOS issue

---

### Post by urrfaust on 2019-05-29
Also, looking at /boot/grub/grub.cfg I see that it’s using hd2 all over the place. Could it be that the grub boot loader installed in the mbr of the second disk sdb is messing up the whole thing. How do I get rid of it? sdb is just an NTFS formatted disk I use for backup (pics, movies etc)

---

### Post by yancek on 2019-05-29
You have a grub.cfg file on sdc5 with the Ubuntu menuentries and another grub.cfg on sdc6 with only windows entries??  Unusual to say the least.

Have you set sdc, the 465GB drive to first boot priority in the BIOS of your computer??  Grub is in the MBR of this drive and the boot files are also on this drive (partition sdc5) with Ubuntu entries so setting this to first boot priority should boot Ubuntu.  Not sure how/why you have Grub files on 2 partitions?

> I tried changing hd2 to hd0 in grub and ran update-grub

How?  If you edited the grub.cfg file directly the change will not be saved if you update grub.  You need to change the entry in a file in /etc/grub.d/ and then run update grub.
I'm not sure why you are concerned with sdb.  You need to set the correct drive (sdc) first in boot priority.

---

### Post by urrfaust on 2019-05-29
Yes I have set sdc to be the first in the boot order in BIOS.
I changed hd2 to hd0 in the grub menu at boot, by pressing 'e'. Then I ran update-grub. But then in grub.cfg I see hd2.
I'm wondering if the disk numbering hd0, hd1... changes between reboots???

---

### Post by oldfred on 2019-05-29
If plug in a drive, flash drive or unplug it, or reboot,  drive order can change.

I thought if you directly boot from sdc, that would be seen as hd0 in grub.
My old system that was BIOS, boot drive always was hd0 and I booted from just about every drive, but they were all internal. Only my flash drives were external and I normally only had one plugged in at a time and it always was sdf when plugged in and sda when rebooted if still plugged in.

But BIOS does keep track of drive order primarily by SATA port order. Its just flash drives or other external drives may change that.

---

### Post by yancek on 2019-05-29
>  changed hd2 to hd0 in the grub menu at boot, by pressing 'e'. Then I ran update-grub. But then in grub.cfg I see hd2.

Changing a menuentry by using the e key to edit it on boot is one time only.  Nothing is saved.  Not sure why you ran update-grub.  If you change the hd2 to hd0 for test purposes in the grub.cfg menu, do NOT run update-grub as the change will be overwritten when you update grub.  If you are just testing, doing it with the e key on boot is simpler.  What happened when you changed the entry on boot with the e key to hd0?   If it boots correctly, you would then need to edit the 40_custom or another file in /etc/grub.d directory to make the change permanent.

---

### Post by urrfaust on 2019-05-29
Yes it booted when I changed it to hd0. Anyway i’m Thinking this is a timing issue with the usb disk. Whenever the pc is rebooted, I don’t get the grub menu. If I turn it on, or, if I disconnect/reconnect it between boots, then It works. probably at reboot, the USB port does not get reset or something

---

### Post by yancek on 2019-05-30
I'm not sure what the problem is but, if it booted when you changed the entry to hd0, try booting again and then copy the menuentry for Ubuntu to the file:  /etc/grub.d/40_custom.  Make sure you change the entry so that it shows hd0 rather than hd2, save the file (need to use sudo for root privileges to edit this file) then run sudo update-grub.  If that doesn't work, I'm not sure what else you could do.

---

