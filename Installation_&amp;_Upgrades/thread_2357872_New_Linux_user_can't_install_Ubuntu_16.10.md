---
title: "New Linux user can't install Ubuntu 16.10"
date: 2017-04-06
forum: Installation &amp; Upgrades
---

### Post by tatetatetatenz on 2017-04-06
By the title I'm sure you can see what my issue is.

I am failing to install Ubuntu 16.10 on an empty drive.

When I turn on my machine I ma prompted to select a boot device, I have disconnected all unnecessary drives so I only see my boot USB which contains Ubuntu 16.10 ISO mounted.
I have the option to either just boot to the USB or boot to the USB in UEFI mode.

The first issue which I think I have resolved but is worth mentioning is no matter the mode I selected ( UEFI or regular ) when either using the "Try Ubuntu without installing" or "Install Ubuntu" option my monitor just went to sleep and nothing more happened.
After a little research I found that selecting "nomodereset" in the options for the regular boot and typing this command un UEFI mode allowed me to boot into Ubuntu when using the "Try Ubuntu without installing" mode or "Install Ubuntu".

For every scenario I have NOT selected the automatic updates and am not connected to the internet as selecting these options seems to hang up the machine and doesn't allow me to continue.

Scenarios using the "Something else" option from where i would like to install Ubuntu:

When Installing Ubuntu on an empty drive I first tried one partition mounted at "/" formatted as ext4.
This ran the installation to completion.
The drive does not show up on the boot menu.

I did some reading and found that I needed a swap partition so I followed some instructions on a post I found on StackExchange and partitioned my swap drive at a size larger than my memory and an ext4 partition mounted at "/".
This ran the installation to completion.
The drive does not show up on the boot menu.

I tried both of these scenarios directly from "Install Ubuntu" and "Try Ubuntu without installing" then selecting the install ubuntu from the desktop.
I also tried both of these scenarios from regular and UEFI modes.

Next I installed ubuntu on the drive as listed above but this time instead of reformatting the drive before trying again I left Ubuntu on the drive.
While installing I am given new options such as "Install Ubuntu 16.10 along side Ubuntu 16.10" ect... I decided to select the option that removes everything on the drive and installs Ubuntu 16.10.

After installing Ubuntu this way i can see the drive name at the boot menu however I can't boot into it.
Every time I select it the process restarts and offers me to boot into something else.

I am really not sure what is going on here. I have done a lot of reading about GRUB and I think there may be an issue here but as I said I am very new to linux and am not sure where to start.

Can anyone help me here or give me a step by step in debugging or installing?
Should I have a blank drive?
Should I remount the ISO to the USB?

The USB seems to be bootable every time is there a way I can put the ISO on the SSD and boot from that and rewrite the OS onto the SSD after booting?

Thanks in advance for reading the long post.

---

### Post by oldfred on 2017-04-07
What brand/model system? And what video card/chip?

Many UEFI systems need work arounds as they violate UEFI standard. The use description as part of boot and that description has to be "Windows Boot Manager". No idea why they think that is important?
But we have multiple work arounds, depending on if dual booting with Windows or only booting Ubuntu. 

If only Ubuntu, I do prefer to use UEFI with gpt partitioning and partition in advance.
But I multiple boot several Ubuntu flavors and then add larger data partition(s) and only use smaller / (root) partitions.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by tatetatetatenz on 2017-04-10
I am running an ASRock Z77 OC motherboard, Intel Core I7-3770K, Nvidia GTX 970, and 16GB of some corsair ram.

Like I said I am very new to this. Are there any guides I feel like this much barrier to entry is crazy for an OS.
I'm not even familiar with UEFI's or what this is... I am booting the USB via BIOS mode, I just mentioned I have the UEFI option.

I just want to install Ubuntu on an Empty drive via USB bootable ISO.
I have the empty drive and USB. A simple task like this seem out of reach for a beginner.

Boot Via USB
Install Ubuntu with 'nomodeset'
Restart
Remove USB
Drive is visible but not bootable

With a Windows install or even OSX there is 3 steps:
Boot via USB
Format/Install
Restart

Is there something similar available here?

---

### Post by westie457 on 2017-04-10
Hi, at the moment there is about 5 options that might work and only 1 that will work. We want/need to find the 1 that works.

Boot your system using your USB drive in Try-mode, connect to the internet and go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You will want the '2nd option'. Follow the instructions given to install Boot Repair. When the App opens DO NOT ATTEMPT ANY REPAIRS, click on the button to create a Boot-info Report.
Post the generated link back here. This will tell us exactly what we are dealing with.

---

### Post by tatetatetatenz on 2017-04-10
Thanks Westie,

In addition to potentially leading me in the right direction could you explain whats going on here? I am curious to know whats happening.

[http://paste2.org/kh21UZb1](http://paste2.org/kh21UZb1)

```

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]
 
 
============================= Boot Info Summary: ===============================
 
 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.
 
sda1: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/fbx64.efi /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi
 
sda2: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab
 
sda3: __________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info: 
 
sdb1: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32816 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
Disk /dev/sda: 117.4 GiB, 126035288064 bytes, 246162672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1                   1   246,162,671   246,162,671  ee GPT
 
 
GUID Partition Table detected.
 
Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2             1,050,624   212,858,879   211,808,256 Data partition (Linux)
/dev/sda3           212,858,880   246,161,407    33,302,528 Swap partition (Linux)
 
Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
 
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 15 GiB, 16039018496 bytes, 31326208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdb1    *          2,048    31,326,207    31,324,160   c W95 FAT32 (LBA)
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/loop0                                              squashfs   
/dev/sda1        EB54-FB85                              vfat       
/dev/sda2        d0ef731e-335e-4597-9e97-ce62b272d797   ext4       
/dev/sda3        466da28f-0f67-44d0-8b4c-8562b525e3bd   swap       
/dev/sdb1        424C-D45F                              vfat       UBUNTU 16_1
 
========================= "ls -l /dev/disk/by-id" output: ======================
 
total 0
lrwxrwxrwx 1 root root  9 Apr 10 09:50 ata-SanDisk_SDSSDP128G_140796402469 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 10 09:50 ata-SanDisk_SDSSDP128G_140796402469-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 10 09:50 ata-SanDisk_SDSSDP128G_140796402469-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 10 09:50 ata-SanDisk_SDSSDP128G_140796402469-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Apr 10 09:50 usb-USB_Flash_Disk_FBI1407172116920-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 10 09:50 usb-USB_Flash_Disk_FBI1407172116920-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr 10 09:50 wwn-0x5001b44bd3b39725 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 10 09:50 wwn-0x5001b44bd3b39725-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 10 09:50 wwn-0x5001b44bd3b39725-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 10 09:50 wwn-0x5001b44bd3b39725-part3 -> ../../sda3
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797 ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 
 
=========================== sda2/boot/grub/grub.cfg: ===========================
 
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
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
else
  search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
fi
    font="/usr/share/grub/unicode.pf2"
fi
 
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_NZ
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
if background_color 44,0,30,0; then
  clear
fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d0ef731e-335e-4597-9e97-ce62b272d797' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
    else
      search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
    fi
    linux    /boot/vmlinuz-4.8.0-46-generic.efi.signed root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.8.0-46-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-d0ef731e-335e-4597-9e97-ce62b272d797' {
    menuentry 'Ubuntu, with Linux 4.8.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-46-generic-advanced-d0ef731e-335e-4597-9e97-ce62b272d797' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
        else
          search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
        fi
        echo    'Loading Linux 4.8.0-46-generic ...'
        linux    /boot/vmlinuz-4.8.0-46-generic.efi.signed root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-46-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-46-generic-init-upstart-d0ef731e-335e-4597-9e97-ce62b272d797' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
        else
          search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
        fi
        echo    'Loading Linux 4.8.0-46-generic ...'
        linux    /boot/vmlinuz-4.8.0-46-generic.efi.signed root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-46-generic-recovery-d0ef731e-335e-4597-9e97-ce62b272d797' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
        else
          search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
        fi
        echo    'Loading Linux 4.8.0-46-generic ...'
        linux    /boot/vmlinuz-4.8.0-46-generic.efi.signed root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-22-generic-advanced-d0ef731e-335e-4597-9e97-ce62b272d797' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
        else
          search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
        fi
        echo    'Loading Linux 4.8.0-22-generic ...'
        linux    /boot/vmlinuz-4.8.0-22-generic root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-22-generic-init-upstart-d0ef731e-335e-4597-9e97-ce62b272d797' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
        else
          search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
        fi
        echo    'Loading Linux 4.8.0-22-generic ...'
        linux    /boot/vmlinuz-4.8.0-22-generic root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-22-generic-recovery-d0ef731e-335e-4597-9e97-ce62b272d797' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  d0ef731e-335e-4597-9e97-ce62b272d797
        else
          search --no-floppy --fs-uuid --set=root d0ef731e-335e-4597-9e97-ce62b272d797
        fi
        echo    'Loading Linux 4.8.0-22-generic ...'
        linux    /boot/vmlinuz-4.8.0-22-generic root=UUID=d0ef731e-335e-4597-9e97-ce62b272d797 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-22-generic
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
 
=============================== sda2/etc/fstab: ================================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d0ef731e-335e-4597-9e97-ce62b272d797 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=EB54-FB85  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=466da28f-0f67-44d0-8b4c-8562b525e3bd none            swap    sw              0       0
--------------------------------------------------------------------------------
 
=================== sda2: Location of files loaded by Grub: ====================
 
           GiB - GB             File                                 Fragment(s)
 
  58.790718079 = 63.126052864   boot/grub/grub.cfg                             1
   1.445438385 = 1.552027648    boot/vmlinuz-4.8.0-22-generic                  1
   2.269855499 = 2.437238784    boot/vmlinuz-4.8.0-46-generic                  1
   2.500125885 = 2.684489728    boot/vmlinuz-4.8.0-46-generic.efi.signed       1
   1.445438385 = 1.552027648    vmlinuz                                        1
   2.751262665 = 2.954145792    boot/initrd.img-4.8.0-22-generic               1
   3.140296936 = 3.371868160    boot/initrd.img-4.8.0-46-generic               3
   2.751262665 = 2.954145792    initrd.img                                     1
   2.751262665 = 2.954145792    initrd.img.old                                 1
 
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
            ?? = ??             ldlinux.sys                                    1
 
=============================== StdErr Messages: ===============================
 
File descriptor 63 (pipe:[47435]) leaked on lvs invocation. Parent PID 13113: bash
 
ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-04-10__09h50 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
boot-repair is executed in live-session (Ubuntu 16.10, yakkety, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash ---  nomodeset
ls: cannot access '/home/usr/.config': No such file or directory
 
=================== os-prober:
/dev/sda2:Ubuntu 16.10 (16.10):Ubuntu:linux
 
=================== blkid:
/dev/sda1: UUID="EB54-FB85" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="2f623478-d364-44ee-a773-156e60489df7"
/dev/sda2: UUID="d0ef731e-335e-4597-9e97-ce62b272d797" TYPE="ext4" PARTUUID="af217557-6b65-4942-9db7-6adb9a667fc2"
/dev/sdb1: LABEL="UBUNTU 16_1" UUID="424C-D45F" TYPE="vfat" PARTUUID="0004f25b-01"
/dev/loop0: TYPE="squashfs"
/dev/sda3: UUID="466da28f-0f67-44d0-8b4c-8562b525e3bd" TYPE="swap" PARTUUID="9a54415a-7704-479b-9072-16a31e404343"
 
 
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
 
 
=================== /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 10 09:42 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Sep  6  2016 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12261 Sep  6  2016 10_linux
-rwxr-xr-x 1 root root 11082 Sep  6  2016 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Sep  6  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Sep  6  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Sep  6  2016 40_custom
-rwxr-xr-x 1 root root   216 Sep  6  2016 41_custom
-rw-r--r-- 1 root root   483 Sep  6  2016 README
 
 
 
 
=================== /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797/etc/default/grub :
 
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
 
 
 
/boot/efi detected in the fstab of sda2: UUID=EB54-FB85   (sda1)
 
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.
 
 
=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797.
 
sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
 
 
=================== parted -l:
 
Model: ATA SanDisk SDSSDP12 (scsi)
Disk /dev/sda: 126GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:
 
Number  Start   End    Size    File system     Name                  Flags
1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
2      538MB   109GB  108GB   ext4
3      109GB   126GB  17.1GB  linux-swap(v1)
 
 
Model: USB Flash Disk (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
 
Number  Start   End     Size    Type     File system  Flags
1      1049kB  16.0GB  16.0GB  primary  fat32        boot, lba
 
=================== parted -lm:
 
BYT;
/dev/sda:126GB:scsi:512:512:gpt:ATA SanDisk SDSSDP12:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:109GB:108GB:ext4::;
3:109GB:126GB:17.1GB:linux-swap(v1)::;
 
BYT;
/dev/sdb:16.0GB:scsi:512:512:msdos:USB Flash Disk:;
1:1049kB:16.0GB:16.0GB:fat32::boot, lba;
 
=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk             15G
sdb1  part vfat        15G UBUNTU 16_1
loop0 loop squashfs   1.4G
sda   disk          117.4G
sda2  part ext4       101G
sda3  part swap      15.9G
sda1  part vfat       512M
 
KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
loop0    1  1  0         /rofs
sda      0  0  1 running
sda2     0  0  1         /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797
sda3     0  0  1         [SWAP]
sda1     0  0  1         /mnt/boot-sav/sda1
 
 
=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8137156k,nr_inodes=2034289,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1630636k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=cdb102b88742b2fc)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=35,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10593)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1630632k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda2 on /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 
 
=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hidraw6 hidraw7 hidraw8 hidraw9 hpet hugepages hwrng initctl input kmsg kvm lightnvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control
 
=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 00 04 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 85 fb 54 eb 4e  4f 20 4e 41 4d 45 20 20  |..)..T.NO NAME  |
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
 
=================== df -Th:
 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.8M  1.6G   1% /run
/dev/sdb1      vfat       15G  1.5G   14G  10% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      7.8G   69M  7.8G   1% /
tmpfs          tmpfs     7.8G   19M  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.8G  160K  7.8G   1% /tmp
tmpfs          tmpfs     1.6G  124K  1.6G   1% /run/user/999
/dev/sda2      ext4       99G  4.4G   90G   5% /media/ubuntu/d0ef731e-335e-4597-9e97-ce62b272d797
/dev/sda1      vfat      511M  3.5M  508M   1% /mnt/boot-sav/sda1
 
=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 
Disk /dev/loop0: 1.4 GiB, 1536229376 bytes, 3000448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
Disk /dev/sda: 117.4 GiB, 126035288064 bytes, 246162672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 776BCA96-9543-4C40-B49B-B97345CFD0E4
 
Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M EFI System
/dev/sda2    1050624 212858879 211808256  101G Linux filesystem
/dev/sda3  212858880 246161407  33302528 15.9G Linux swap
 
 
Disk /dev/sdb: 15 GiB, 16039018496 bytes, 31326208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0004f25b
 
Device     Boot Start      End  Sectors Size Id Type
/dev/sdb1  *     2048 31326207 31324160  15G  c W95 FAT32 (LBA)
 
 
 
 
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi
 
 
=================== Blockers in case of suggested repair
The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.
 
 
=================== Advice in case of suggested repair
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Alternatively, you may want to retry after deactivating the [Separate /boot/efi partition:] option.
Do you want to continue?
 
 
=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!
 
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
 
 
=================== User settings
The settings chosen by the user will not act on the boot.
 
 
 
 
paste.ubuntu.com ko (), using paste.debian
paste.debian.net ko (), using paste2
```

---

### Post by Bucky Ball on 2017-04-10
From your output.

```
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
```

Try booting to BIOS and changing the boot to UEFI mode. Were you aware you were installing in EFI? ;)

---

### Post by tatetatetatenz on 2017-04-10
Is EFI the option that is not UEFI?

And should I install in this mode then paste the result again?

Again for clarity:
I have two Options to boot with the same USB:

UEFI mode
and regular - " Just says the USB name "

EDIT:

I'm pretty sure I'm booting in UEFI mode because the BIOS says ASROCK UEFI when Im at the boot menu...

---

### Post by kc1di on 2017-04-10
boot up in UEFI  do the install again - you have a fairly new Nvidia card so use nomodeset - When it come to the install. don't select 3rd party code and don't do the update while installing.
disconnect the machine from the internet and allow the install to finish.  then try to boot into ubuntu.  If all went well it should boot. Once it's booted connect to the internet and do the updates. 
Good luck

---

### Post by tatetatetatenz on 2017-04-10
> **kc1di said:**
> boot up in UEFI  do the install again - you have a fairly new Nvidia card so use nomodeset - When it come to the install. don't select 3rd party code and don't do the update while installing.
disconnect the machine from the internet and allow the install to finish.  then try to boot into ubuntu.  If all went well it should boot. Once it's booted connect to the internet and do the updates. 
Good luck

So I tried that and I installed fine and restart the PC and I can see the drive on the boot menu but when I select it I get redirected straight back to the UEFI.
This is from installing in UEFI mode and Try in UEFI mode:

[http://paste2.org/WwIhazyJ](http://paste2.org/WwIhazyJ)

PLEASE HELP ME!

---

### Post by oldfred on 2017-04-10
Asrock has as few settings or configurations that may be required.
Issues are common across Intel based Asrock motherboards, so even newer ones have similar issues.

I have both Asus & Gigabyte motherboards which required multiple UEFI settings changes to get system to boot and work correctly. And then update to UEFI from vendor reset to defaults. So keep a list of changes you make. 

Check that you are not using any Asmedia ports, just the standard Intel ones. One user had issues with just the DVD in an Asmedia port.
Some were able to turn off nVidia card and boot with Intel video, then install nVidia driver from repository and re-enable nVidia card.

 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
[http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual](http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by kc1di on 2017-04-10
Ok now I want you to insert the usb stick or DVD you used to install the program with and boot to a live session. 
Once there go to a terminal and type this command ```
sudo apt-get install grub-efi-amd64
```
reboot see if that works first.  If not we'll try some other things.

---

### Post by tatetatetatenz on 2017-04-11
> **kc1di said:**
> Ok now I want you to insert the usb stick or DVD you used to install the program with and boot to a live session. 
Once there go to a terminal and type this command ```
sudo apt-get install grub-efi-amd64
```
reboot see if that works first. If not we'll try some other things.

Hey kc1di,

Thanks for the help. I'm assuming when you say "Live session" you mean "Try Ubuntu without installing".
If so then I did this. ( Also I'm no expert but installing something while in this mode wont stay will it... When I restart I mean doesn't everything get wiped?" )

I have restarted and at the boot menu I can still see my drive but cannot boot to it.

---

### Post by westie457 on 2017-04-11
Hi, the next possibility for a fix is as follows.

Boot into 'try-mode' > Start 'Gparted' > Right-click the FAT32 partition > 'Manage Flags'

Mark the boxes called 'Boot' and 'ESP'. Close the window and wait for the changes to take effect.

Reboot your system (hopefully) to the installed OS.

Info was found here [http://askubuntu.com/questions/353683/uefi-partitioning-for-dummies](http://askubuntu.com/questions/353683/uefi-partitioning-for-dummies)

---

### Post by tatetatetatenz on 2017-04-11
Thanks for the help.

Unfortunately this did not work either. I can see the drive but again can't boot :(

Any idea what is going on here? I would do some more research but I have about exhausted the search terms for whats going on.

EDIT:
Is this an issue with my hardware? Is Ubuntu just not going to work with my setup? Should I try a different distro?

---

### Post by oldfred on 2017-04-11
Are you using nomodeset when booting Ubuntu on hard drive?
With nVidia card you need nomodeset until you install the nVidia driver from the Ubuntu repository.

With UEFI and only one install, you will not get grub menu by default.
You can press Escape key (perhaps more than once) from UEFI but before system starts to boot. You will need UEFI fast boot off, as then it boots too quick to have time to press a key.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Did you check that you are not using an Asmedia ports?

---

### Post by tatetatetatenz on 2017-04-11
I have installed using the boot option nomodeset.
How I did it:
After booting into UEFI menu I pressed 'e' and modified the line with "quiet splash" and added "nomodeset" ---> " quite nomodeset splash"
Then I pressed F10 to boot, depending on the option "Install Ubuntu" or "Try Ubuntu" This allows me to either install or go into Try mode.

If I don't do this I can't go any further so I assume I'm doing it correctly.

In the first article you linked the OP mentions pressing SHIFT after selecting a boot option "My installed drive" to get into a grub menu. This doesn't seem to work for me although I'm not sure If I am doing it correctly.

Also the OP mentions pressing F6 to edit options. This was only available to me in the Legacy mode.

Not sure what I'm missing here.

In the second link this looks like my UEFI ( the second black image ) although I do not get these options.

When holding shift I still have:
"Try Ubuntu without Installing"
"Install Ubuntu"
"OEM Install"
"Check Disk for defects"

When I remove the USB before booting I get directed to the BIOS (UEFI).

---

### Post by Bucky Ball on 2017-04-11
> **tatetatetatenz said:**
> In the first article you linked the OP mentions pressing SHIFT after selecting a boot option "My installed drive" to get into a grub menu. This doesn't seem to work for me although I'm not sure If I am doing it correctly.

Then try 'Esc'. It's one for legacy and the other for UEFI, don't remember which goes with which.

---

### Post by tatetatetatenz on 2017-04-12
So holding Escape or Shift while booting does nothing.
When I am in the UEFI menu however pressing escape takes me to a grub command line, nothing similar to the post however...

I also can do this by pressing 'c' in the Grub menu.

OK! So something does happen when I hold shift after BIOS image... it's an error of some kind but it flashes so quick then goes back to the UEFI Grub menu where i can select what to do.
After many restarts I found that the error when holding shift says "error: file '/boot/' not found.

What am I trying to accomplish here? I feel like I have mostly already done this.... I am booting using nomodeset.

---

### Post by oldfred on 2017-04-12
Holding Shift key is for BIOS boot, & Escape key is for UEFI boot to get grub menu when you only have one install.

Choice of UEFI or BIOS is always from how you choose to boot from UEFI boot menu. But you can tell how you booted live installer, BIOS is purple screen and it boots with syslinux and grub menu is UEFI.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tatetatetatenz on 2017-04-13
WOW ok I have said many times it's being booted in UEFI mode... please...

---

### Post by oldfred on 2017-04-13
Then Escape key is only key that will work to get into UEFI or choose boot drive, before grub starts to load.
Once at grub menu only grub commands work.

With UEFI you need at the minimum, the ESP - efi system partition, / (root) and swap. Although with 17.04 they are changing to using a swap file, not a swap partition. See also link at bottom in my signature. 

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

