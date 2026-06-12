---
title: "How do I get a clean install of Xubuntu 16.04 on a Lenovo G50-45?"
date: 2017-08-09
forum: Installation &amp; Upgrades
---

### Post by bouncing-hole on 2017-08-09
Note: Widows has been removed completely. The drive was reformatted and  repartitioned with GParted before installation. UEFI mode is being used. The install medium is a USB drive.

So far this has been a nightmare as the installation is rife with problems. I have reinstalled five times. I have a list that continues to grow.

So, in short, how should I install Xubuntu 16.04 (or any *buntu of any version) so as to get a good clean installation. Pointing to step by step documentation is preferred over clogging the site with a potentially duplicate post.

Thanks.

---

### Post by vocx on 2017-08-09
> **bouncing-hole said:**
> Note: Widows has been removed completely. The drive was reformatted and  repartitioned with GParted before installation. UEFI mode is being used. The install medium is a USB drive.

So far this has been a nightmare as the installation is rife with problems. I have reinstalled five times. I have a list that continues to grow.

So, in short, how should I install Xubuntu 16.04 (or any *buntu of any version) so as to get a good clean installation. Pointing to step by step documentation is preferred over clogging the site with a potentially duplicate post.

Thanks.
I honestly don't like these types of posts, where the poster says "help, I tried everything and nothing works!".

My response is always: so, exactly, what did you try? What steps did you follow? What guides did you read? What videos were you watching? What error messages exactly did you get? What do you consider "rife with problems"?

I mean, posting that you had a problem is okay, but giving actual helpful information about it will allow the community to suggest solutions. Also, what kind of computer is that? Is that a laptop? What are the specifications? The more troublesome parts are the video drivers (either Nvidia or AMD/ATI) and the wireless card drivers.

---

### Post by TheFu on 2017-08-09
The Lenovo G50-45 seems to be the issue here.  I can assure you that XFCE-Ubuntu 16.04 installs fairly easily on most hardware.  Usually the main issue is with wifi support, which can be added later, after the install has been completed. Using a wired ethernet connector almost always works.

What have you tried?  "rife with problems" is a little vague. 
Does running with a live-boot Xubuntu work well?  (Try Xubuntu)

---

### Post by oldfred on 2017-08-09
If you have actually installed:
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I do not know AMD systems and then what is now current AMD driver for whatever chip/card you have. But to boot you may temporarily need nomodeset. And if only Ubuntu installed, you normally do not get grub menu to be able to add nomodeset. With UEFI press Escape key, perhaps more than once, to get grub menu.
If you left fast boot on in UEFI, you may not have time to press any key, and need to cold boot or boot from full power down.

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

If you press UEFI one time boot menu key, often f10 or f12, do you have an Ubuntu entry, you probably should have two, one shim for secure boot and one grub.

At least some Lenovo's need the work around for those vendors that violate UEFI standard and only boot by UEFI menu description and only valid description is "Windows Boot Manager". If only booting Ubuntu you can rename the ubuntu UEFI entry to Windows and boot.

---

### Post by bouncing-hole on 2017-08-09
Lenovo G50-45: Laptop; AMD A8; 6 GB RAM (I added 2 GB); Video: AMD/ATI xserver-xorg-video-ati_7.5.0-1_amd64. To enter the Boot Menu I press a button on the side near the power adapter that is flush with the surface and select from a menu (third down).

 The stick: SanDisk 16 GB. Currently it has a GPT with one FAT32 partition. Each time I redo this to make sure the drive is clean. I have used ms-dos and ext3 and 4 partitions. But only one partition on the stick at a time.
 
 Tutorials: Two times (including this last one which is not installed, but have run live): [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0). The other times were with other 'boot makers'. Some with full (or not) instructions.
 
 Xubuntu does boot into a live-session from the stick. As do other distros. However sometimes I just get an installer. Which would be fine if it worked and I broke it later.
 
 Difficulties: [FONT=FreeSans][SIZE=3]&#65279;[/SIZE][/FONT]I get "Error: file '/boot/' not found (Oldfred?). There are several 'boot' folders and files of various sorts on the disk. If I go straight to install, instead of try first, it produces a start job that will go on for hours. As an install there are between zero and six error messages at startup (it seems to be random). I can not crtl-x or -c anything (those shortcuts, and paste, are not even listed under the keyboard shortcuts). But I can Ctrl-v after I cut/copy through the drop-down menu. All three work in all other programs. In that same menu Move to Trash does not work. Instead I am prompted to Delete. My Trash is only available when I drag an icon to it on the Desktop. At this point it tells me that the file/folder was deleted three months and two days ago even though my clock and calender show the correct time and date. My sound and display brightness are not remembered. There are three video drivers installed (???). Software updater tells me that updates are ready even though I have not plugged in my Ethernet cable (I unplug it when I shut down and do not plug it in until I am logged in and the system is fully loaded, which incidentally ends up being after the updater prompts me to update, plus wi-fi has not been setup on my router and it does not show when I scan for wi-fi signals). This update is just less than 100 MB (it varies). "sudo apt-get upgrade" tells me that is, at most, ~5,000 KB. The list goes on. To many things I do give some error or do not work. Abiworb flickers continuously (nothing else does that).

 I have a few empty partitions just for experimentation. Apparently this one is too.

---

### Post by oldfred on 2017-08-09
Are you doing  a full install to a USB flash drive?

Is live installer working? It will not do some things as it is like a DVD or not writeable. If you add persistence you can save some data to an installer, but have to reinstall any apps as they are just in memory.

If full install to flash drive and you want UEFI, you must use gpt partitioning and include the ESP - efi system partition as first partition (FAT32). And then have to copy files from ESP on drive seen as sda to flash drive.

Issue with full installs to any second drive or particularly USB drives is that UEFI only boots from a FAT32 ESP and /EFI/Boot/bootx64.efi folder & files on external devices. 

And grub only installs to /EFI/ubuntu folder on ESP on drive seen as sda. So files have to be copied twice, once to /EFI/ubuntu on USB drive and again to /EFI/Boot and shimx64.efi renamed to bootx64.efi. Both copies are required as the full install grub expects more boot files in /EFI/ubuntu. 

The limited live installer version of grub also boots from /EFI/Boot/bootx64.efi, but that grub only has what is needed to boot a live installer.

---

### Post by bouncing-hole on 2017-08-09
The stick is not a full install or persistent. That is beyond me right   now (as in side-track/ focus). Just something to  get started and see  what it is like. I haven't even gotten a HDD install to work yet. I  changed the theme and font which reverted on restart. And I tried  to  change the icons (sudo gtk-update-icon-cache   /user/share/icons/elementary-xfce-darkest). That got an immediate and  firm 'no'.

I can only kind-of understand this from my Windows expirience. Some  partitions are named to reserve them for when I get to LFS. However I am  flexible.

My compliments to the Boot-info programer(s). Impressive.

```
Lenovo G50-45
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                    34     1,028,159     1,028,126 EFI System partition
/dev/sda2             1,028,160     1,044,224        16,065 Data partition (Linux)
/dev/sda3             1,044,225    13,623,119    12,578,895 Swap partition (Linux)
/dev/sda4            13,623,120    47,182,904    33,559,785 Data partition (Linux)
/dev/sda5            47,182,905    80,742,689    33,559,785 Data partition (Linux)
/dev/sda6            80,742,690   114,302,474    33,559,785 Data partition (Linux)
/dev/sda7           114,302,475   147,862,259    33,559,785 Data partition (Linux)
/dev/sda8           147,862,260   164,634,119    16,771,860 Data partition (Linux)
/dev/sda9           164,634,120   181,405,979    16,771,860 Data partition (Linux)
/dev/sda10          181,405,980   976,768,064   795,362,085 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        374D-F03F                              vfat       
/dev/sda10       0debf301-d7ff-4b3a-bfac-7d193a4ab438   ext4       Data
/dev/sda2        476b0c45-c254-48fd-be59-ba43175b643c   ext2       Empty
/dev/sda3        d2080fdb-120a-44db-a719-1e10452a8839   swap       
/dev/sda4        06f845df-8fb4-4ba4-842d-56271bedb427   ext4       Debian
/dev/sda5        dc136fdd-026a-46e0-8c84-438e01e173db   ext4       Gentoo
/dev/sda6        c19788a7-30a3-4719-8b2d-2d8d7b8f66fd   ext4       Davian
/dev/sda7        146d0512-1fd1-4daf-9990-75a842ba7df1   ext4       Davtoo
/dev/sda8        595895f9-a3b8-4ee1-ad89-bbc5884b5aa8   ext4       Android
/dev/sda9        a3ee15d4-86a9-43d2-861e-b4e78b62e92f   ext4       Davdroid

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug  9 16:14 ata-HL-DT-ST_DVDRAM_GUC0N_KWGF37J2855 -> ../../sr0
lrwxrwxrwx 1 root root  9 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT -> ../../sda
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part10 -> ../../sda10
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Aug  9 16:33 ata-TOSHIBA_MQ01ABF050_35IACIAMT-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Aug  9 16:33 wwn-0x50000396237871bd -> ../../sda
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Aug  9 16:33 wwn-0x50000396237871bd-part10 -> ../../sda10
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Aug  9 16:33 wwn-0x50000396237871bd-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Aug  9 16:14 wwn-0x5001480000000000 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat        (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
else
  search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
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
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/09_lowlatency ###
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

### END /etc/grub.d/09_lowlatency ###

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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class  os $menuentry_id_option  'gnulinux-simple-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
    else
      search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
    fi
    linux    /boot/vmlinuz-4.4.0-89-generic.efi.signed  root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro  quiet splash  $vt_handoff
    initrd    /boot/initrd.img-4.4.0-89-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd' {
    menuentry 'Ubuntu, with Linux 4.4.0-89-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-4.4.0-89-generic-advanced-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        else
          search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        fi
        echo    'Loading Linux 4.4.0-89-generic ...'
        linux    /boot/vmlinuz-4.4.0-89-generic.efi.signed  root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro  quiet splash  $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-89-generic (upstart)' --class  ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-4.4.0-89-generic-init-upstart-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        else
          search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        fi
        echo    'Loading Linux 4.4.0-89-generic ...'
        linux    /boot/vmlinuz-4.4.0-89-generic.efi.signed  root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro  quiet splash  $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-89-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-4.4.0-89-generic-recovery-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd'  {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        else
          search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        fi
        echo    'Loading Linux 4.4.0-89-generic ...'
        linux    /boot/vmlinuz-4.4.0-89-generic.efi.signed root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-89-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-83-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-4.4.0-83-generic-advanced-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        else
          search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        fi
        echo    'Loading Linux 4.4.0-83-generic ...'
        linux    /boot/vmlinuz-4.4.0-83-generic.efi.signed  root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro  quiet splash  $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-83-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-83-generic (upstart)' --class  ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-4.4.0-83-generic-init-upstart-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        else
          search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        fi
        echo    'Loading Linux 4.4.0-83-generic ...'
        linux    /boot/vmlinuz-4.4.0-83-generic.efi.signed  root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro  quiet splash  $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-83-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-83-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-4.4.0-83-generic-recovery-c19788a7-30a3-4719-8b2d-2d8d7b8f66fd'  {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6  --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6   c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        else
          search --no-floppy --fs-uuid --set=root c19788a7-30a3-4719-8b2d-2d8d7b8f66fd
        fi
        echo    'Loading Linux 4.4.0-83-generic ...'
        linux    /boot/vmlinuz-4.4.0-83-generic.efi.signed root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-83-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=374D-F03F  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=d2080fdb-120a-44db-a719-1e10452a8839 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda6/boot/extlinux/extlinux.conf: =======================

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

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  51.539978981 = 55.340631040   boot/grub/grub.cfg                             1
  39.487374306 = 42.399245312   boot/vmlinuz-4.4.0-83-generic                  1
  43.249909401 = 46.439236608   boot/vmlinuz-4.4.0-83-generic.efi.signed       2
  39.232525826 = 42.125603840   boot/vmlinuz-4.4.0-89-generic                  1
  42.663975716 = 45.810095104   boot/vmlinuz-4.4.0-89-generic.efi.signed       1
  39.232525826 = 42.125603840   vmlinuz                                        1
  39.487374306 = 42.399245312   vmlinuz.old                                    1
  49.615803719 = 53.274563584   boot/initrd.img-4.4.0-83-generic               3
  39.356038094 = 42.258224128   boot/initrd.img-4.4.0-89-generic               4
  39.356038094 = 42.258224128   initrd.img                                     4
  49.615803719 = 53.274563584   initrd.img.old                                 3

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  42.698388100 = 45.847045120   boot/extlinux/extlinux.conf                    1
  53.347134590 = 57.281049600   boot/extlinux/chain.c32                        1

============== sda6: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

umount: /mnt/BootInfo/sda10: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-08-09__16h33 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
boot-info is executed in installed-session (Ubuntu 16.04.3 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.4.0-89-generic.efi.signed root=UUID=c19788a7-30a3-4719-8b2d-2d8d7b8f66fd ro quiet splash vt.handoff=7
Partition 1 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.
Partition 6 does not start on physical sector boundary.
Partition 7 does not start on physical sector boundary.
Partition 8 does not start on physical sector boundary.
Partition 10 does not start on physical sector boundary.

=================== os-prober:
/dev/sda6:The OS now in use - Ubuntu 16.04.3 LTS CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="374D-F03F" TYPE="vfat" PARTLABEL="UEFI" PARTUUID="c3935edb-f6c2-4d07-b0ad-2552eff45716"
/dev/sda2: LABEL="Empty" UUID="476b0c45-c254-48fd-be59-ba43175b643c" TYPE="ext2" PARTUUID="99044a7f-ff0c-41f7-b5a0-cb259583811a"
/dev/sda3: UUID="d2080fdb-120a-44db-a719-1e10452a8839" TYPE="swap"  PARTLABEL="Swap" PARTUUID="cc31bd7d-a241-4084-8ff4-b38dbe97102b"
/dev/sda4: LABEL="Debian" UUID="06f845df-8fb4-4ba4-842d-56271bedb427"  TYPE="ext4" PARTLABEL="Debian"  PARTUUID="ba69d27f-4646-4f11-9f2d-46130623e347"
/dev/sda5: LABEL="Gentoo" UUID="dc136fdd-026a-46e0-8c84-438e01e173db"  TYPE="ext4" PARTLABEL="Gentoo"  PARTUUID="b325ba01-d843-4b72-819e-7906b16dabb6"
/dev/sda6: LABEL="Davian" UUID="c19788a7-30a3-4719-8b2d-2d8d7b8f66fd"  TYPE="ext4" PARTUUID="80fccb41-8116-41f0-bf49-389b3d0e7772"
/dev/sda7: LABEL="Davtoo" UUID="146d0512-1fd1-4daf-9990-75a842ba7df1"  TYPE="ext4" PARTUUID="2a6456af-f95e-468a-999f-22fb96217a7b"
/dev/sda8: LABEL="Android" UUID="595895f9-a3b8-4ee1-ad89-bbc5884b5aa8"  TYPE="ext4" PARTUUID="3fdcb434-4926-46bc-a91b-bc0ed91fa989"
/dev/sda9: LABEL="Davdroid" UUID="a3ee15d4-86a9-43d2-861e-b4e78b62e92f"  TYPE="ext4" PARTUUID="b47539bf-d820-4b4c-ba5e-83941fe36dcc"
/dev/sda10: LABEL="Data" UUID="0debf301-d7ff-4b3a-bfac-7d193a4ab438" TYPE="ext4" PARTUUID="58f0aa57-ecb9-43fd-b2f8-7287355ac8ad"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Partition 1 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.
Partition 6 does not start on physical sector boundary.
Partition 7 does not start on physical sector boundary.
Partition 8 does not start on physical sector boundary.
Partition 10 does not start on physical sector boundary.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Aug  7 20:59 grub.d
total 92
-rwxr-xr-x 1 root root  9791 Aug  2  2016 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root  9921 Apr  9  2014 09_lowlatency
-rwxr-xr-x 1 root root 12512 Jun 20 23:11 10_linux
-rwxr-xr-x 1 root root 11082 Jun 20 23:11 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Aug  2  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Aug  2  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Aug  2  2016 40_custom
-rwxr-xr-x 1 root root   216 Aug  2  2016 41_custom
-rw-r--r-- 1 root root   483 Aug  2  2016 README




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



/boot/efi detected in the fstab of sda6: UUID=374D-F03F   (sda1)

=================== efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,2001,2003,2002
Boot0000* ubuntu    HD(1,GPT,c3935edb-f6c2-4d07-b0ad-2552eff45716,0x22,0xfb01e)/File(EFIubuntushimx64.efi)
Boot0001* EFI Network 0 for IPv4 (68-F7-28-7E-AC-31)      PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(68f7287eac31,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)RC
Boot0002* EFI Network 0 for IPv6 (68-F7-28-7E-AC-31)      PciRoot(0x0)/Pci(0x2,0x4)/Pci(0x0,0x0)/MAC(68f7287eac31,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* EFI USB Device (SanDisk Cruzer Blade)    PciRoot(0x0)/Pci(0x10,0x0)/USB(2,0)/HD(1,MBR,0x4294967195,0x3818,0x1240)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    signed  grub-efi ,    update-grub,    64,    with-boot,    is-os,     not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,     no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,     apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    standard,    not-far,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /boot/efi.
sda2    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda2.
sda4    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda4.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda5.
sda7    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda7.
sda8    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda8.
sda9    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda9.
sda10    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    farbios,    /mnt/boot-sav/sda10.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    34 sectors * 512 bytes


=================== parted -l:

Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name    Flags
1      17.4kB  526MB   526MB   fat32           UEFI    boot, esp
2      526MB   535MB   8225kB  ext2
3      535MB   6975MB  6440MB  linux-swap(v1)  Swap
4      6975MB  24.2GB  17.2GB  ext4            Debian
5      24.2GB  41.3GB  17.2GB  ext4            Gentoo
6      41.3GB  58.5GB  17.2GB  ext4
7      58.5GB  75.7GB  17.2GB  ext4
8      75.7GB  84.3GB  8587MB  ext4
9      84.3GB  92.9GB  8587MB  ext4
10      92.9GB  500GB   407GB   ext4

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA TOSHIBA MQ01ABF0:;
1:17.4kB:526MB:526MB:fat32:UEFI:boot, esp;
2:526MB:535MB:8225kB:ext2::;
3:535MB:6975MB:6440MB:linux-swap(v1):Swap:;
4:6975MB:24.2GB:17.2GB:ext4:grin:ebian:;
5:24.2GB:41.3GB:17.2GB:ext4:Gentoo:;
6:41.3GB:58.5GB:17.2GB:ext4::;
7:58.5GB:75.7GB:17.2GB:ext4::;
8:75.7GB:84.3GB:8587MB:ext4::;
9:84.3GB:92.9GB:8587MB:ext4::;
10:92.9GB:500GB:407GB:ext4::;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk        465.8G
sda1  part vfat     502M
sda2  part ext2     7.9M Empty
sda3  part swap       6G
sda4  part ext4      16G Debian
sda5  part ext4      16G Gentoo
sda6  part ext4      16G Davian
sda7  part ext4      16G Davtoo
sda8  part ext4       8G Android
sda9  part ext4       8G Davdroid
sda10 part ext4   379.3G Data
sr0   rom          1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /boot/efi
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         [SWAP]
sda4     1  0  0         /mnt/boot-sav/sda4
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         /
sda7     1  0  0         /mnt/boot-sav/sda7
sda8     1  0  0         /mnt/boot-sav/sda8
sda9     1  0  0         /mnt/boot-sav/sda9
sda10    1  0  0         /mnt/boot-sav/sda10
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2498248k,nr_inodes=624562,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=503820k,mode=755)
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup  (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup  (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup  (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup  (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot/efi type vfat  (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=503820k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda2 on /mnt/boot-sav/sda2 type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl,stripe=4)
/dev/sda4 on /mnt/boot-sav/sda4 type ext4 (rw,relatime,data=ordered)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw,relatime,data=ordered)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw,relatime,data=ordered)
/dev/sda8 on /mnt/boot-sav/sda8 type ext4 (rw,relatime,data=ordered)
/dev/sda9 on /mnt/boot-sav/sda9 type ext4 (rw,relatime,data=ordered)
/dev/sda10 on /mnt/boot-sav/sda10 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight integrity power queue range removable ro sda1 sda10  sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace  uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight integrity power queue range removable ro size slaves  stat subsystem trace uevent
/dev (filtered):  adsp autofs block bsg btrfs-control bus cdrom cdrw  char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 dsp dvd  dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hugepages hwrng  i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kfd  kmsg lightnvm log mapper mcelog media0 mem memory_bandwidth mixer mqueue  net network_latency network_throughput null port ppp psaux ptmx pts  random rfkill rtc rtc0 sda sda1 sda10 sda2 sda3 sda4 sda5 sda6 sda7 sda8  sda9 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput  urandom usb userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls: cannot access '': No such file or directory

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 22 00 00 00  |........?..."...|
00000020  1e b0 0f 00 eb 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 3f f0 4d 37 20  20 20 20 20 20 20 20 20  |..)?.M7         |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
Partition 1 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.
Partition 6 does not start on physical sector boundary.
Partition 7 does not start on physical sector boundary.
Partition 8 does not start on physical sector boundary.
Partition 10 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.4G     0  2.4G   0% /dev
tmpfs          tmpfs     493M  7.6M  485M   2% /run
/dev/sda6      ext4       16G   13G  2.4G  85% /
tmpfs          tmpfs     2.5G  156K  2.5G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.5G     0  2.5G   0% /sys/fs/cgroup
/dev/sda1      vfat      502M  3.4M  498M   1% /boot/efi
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     493M   36K  492M   1% /run/user/1000
/dev/sda2      ext2      7.6M   45K  7.2M   1% /mnt/boot-sav/sda2
/dev/sda4      ext4       16G   44M   15G   1% /mnt/boot-sav/sda4
/dev/sda5      ext4       16G   44M   15G   1% /mnt/boot-sav/sda5
/dev/sda7      ext4       16G   44M   15G   1% /mnt/boot-sav/sda7
/dev/sda8      ext4      7.8G   18M  7.4G   1% /mnt/boot-sav/sda8
/dev/sda9      ext4      7.8G   18M  7.4G   1% /mnt/boot-sav/sda9
/dev/sda10     ext4      374G  212G  144G  60% /mnt/boot-sav/sda10

=================== fdisk -l:
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 41C85187-5798-4D14-ACA3-716F62DB6583

Device         Start       End   Sectors   Size Type
/dev/sda1         34   1028159   1028126   502M EFI System
/dev/sda2    1028160   1044224     16065   7.9M Linux filesystem
/dev/sda3    1044225  13623119  12578895     6G Linux swap
/dev/sda4   13623120  47182904  33559785    16G Linux filesystem
/dev/sda5   47182905  80742689  33559785    16G Linux filesystem
/dev/sda6   80742690 114302474  33559785    16G Linux filesystem
/dev/sda7  114302475 147862259  33559785    16G Linux filesystem
/dev/sda8  147862260 164634119  16771860     8G Linux filesystem
/dev/sda9  164634120 181405979  16771860     8G Linux filesystem
/dev/sda10 181405980 976768064 795362085 379.3G Linux filesystem




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the  grub-efi-amd64-signed of sda6, using the following options:         sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by TheFu on 2017-08-09
When you "live-boot" from a flash drive, no changes will ever be saved.  It is read-only media. So all those complaints about changing the theme and that being lost at the next boot is a non-sequitur, as oldfred says.

If you want to save things, then you must "install" to some storage.  I've only done 1 efi install and it wasn't on a Lenovo, so I cannot help there. Sorry.

And whenever posting command output, please, please, please, please use "code tags" so it is readable.  We are used to reading that stuff in the terminal format with correct spacing and columns.

The other suggestion I have is to simplify and test. If that doesn't fix the issue, simplify and test again over and over until you get to the root issue.  I see there are multiple disks with multiple partitions.  For a first install, I'd simplify that into 1 empty HDD (zero partitions) and 1 flash drive with the installer.

---

### Post by bouncing-hole on 2017-08-09
One more difficulty (maybe not). When I mount sda10 (Name: Data) from the desktop it mounts as "media/Data/". When mounted from the terminal it is "media/Library". Library is the first folder.

---

### Post by oldfred on 2017-08-09
Your Lenovo may be one that only boots UEFI from "Windows Boot Manager".

Since you only have Ubuntu you can from Live installer run this:
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Then see if your new "Windows" UEFI entry boots grub/ubuntu.

But you may already be booting and the hang up is your video. AMD (and nVidia) almost always need nomodeset. So have you tried getting to grub menu with Escape key? And add nomodeset as posted above.

---

### Post by bouncing-hole on 2017-08-09
This is why I have all of those extra partitions: I have been trying the various nomodeset settings. This reply is from the live-usb I created earlier today. Because the current installation won't display a log-in screen. However at one point I did see the intro-splash which just happens to lookjust  like the outro-splash ("Ubutu Studio...". I will do a fresh install and work on the "As an install..." problems and getting Blender to render to texture (as a contradiction to most the game is designed to be non-salable). It was educational. At some point I'll try again. Thanks anyway.

---

