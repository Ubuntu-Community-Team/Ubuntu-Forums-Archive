---
title: "Doing changes to my dual boot configuration"
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by Hadden89 on 2016-04-14
Probably I'll need some extra steps, as I only use 2 ide drives having one port (and this pc won't boot from usb)

/dev/sda is a 120gb HDD on IDE (30gb ntfs and 80 ext4+swap)
/dev/sdb is a 500gb HDD on SATA (but doesn't count much, having more than 200+ bad sectors)
/dev/sr0 is DVD unit

0) On /dev/sdb I've also a win 10 loader which is useless (even if it works) but xp (/dev/sda) rely on grub to start
1) I'd like to resize (not format) /dev/sda to use whole disk with NTFS (better gparted or use a win tool for that?) and remove ext+swap from there
2) Fully format /dev/sdb and isolate bad sector if possible (however its use will be very limitated)
3) Then I'll unplug from pc the /dev/sda to install lubuntu in a new drive which has the same size (lets say /dev/sdX)
4) When lubuntu will be started, I'll unplug /dev/sr0 from pc
5) My fear is that grub won't recognize the /dev/sdX (win drive), but probably will work adjusting some lines.

If it is possible to start lubuntu install cd from grub itself, probably all is more simple xD

---

### Post by oldfred on 2016-04-14
You can directly boot ISO from grub, but not exactly simple. 
Newest versions I have to umount /mnt/ISO which uses sda partition, sometimes even the one I want to install. Some random mount??
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
Boot ISO from harddrive. To install it would have to be different partition

Generally easier to just create flash drive.
      
 Tools for booting ISO
[http://ubuntuforums.org/showthread.php?t=2289225](http://ubuntuforums.org/showthread.php?t=2289225)
Not ISO boot, uses syslinux - sudodus

  One pendrive for all PC (Intel/AMD) computers

 [http://ubuntuforums.org/showthread.php?t=2259682](http://ubuntuforums.org/showthread.php?t=2259682)
UEFI & BIOS & Live installer - sudodus
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)

While old XP required IDE, better to use AHCI. Required if a newer SSD.

If during install it does not find Windows, run this:
sudo update-grub

With multiple drives either use Something Else or totally disconnect all but Ubuntu drive when installing. Something Else is the only install option that gives you the choice on which drive to install Ubuntu and you want it on same drive as Ubuntu install. Default is always sda.

        Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by yancek on 2016-04-14
> I'd like to resize (not format) /dev/sda to use whole disk with NTFS  (better gparted or use a win tool for that?) and remove ext+swap from  there

Making changes to windows partitions is usually best done with windows tools.  I don't think xp has any?  windows 10 does but from your post, you don't see able to boot it.  
You should be able to use GParted to resize but if you want ntfs and now have a swap and ext4 filesystem, you will obviously need to format it.  If you have any data on the drive, get it off first. 

I'm not sure why you think Ubuntu/Grub won't recognize windows.  It should update-grub at the end of the install and find windows.  If your windows install is problematic, it might not.

Booting an iso of Lubuntu from the hard drive isn't really that difficult if you have a reason to.  I don't see how you can do it based on the description of what you plan to do.  If you delete the ext4 partition on its drive you are also deleting Grub and if you delete Grub you have no bootloader and therefore you can't boot.  If you want to boot an iso with Grub, put the iso file on the current Linux partition on the old drive, put the loopback loop entry in /boot/grub/grub.cfg, save the changes and reboot.  The example below worked for me.  You would need the exact correct name of the iso file you are using and the correct drive/partition on the loopback loop line if it is not sdb3.

> menuentry "Lubuntu14.04" {
    loopback loop (hd1,msdos3)/lubuntu-14.04-desktop-i386.iso
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lubuntu-14.04-desktop-i386.iso quiet splash --
    initrd (loop)/casper/initrd.lz
}

---

### Post by Hadden89 on 2016-04-15
Ok, I'll try grubISO then or try other booting usb methods (but this pc doesn't seem to boot via usb, I hope syslinux works).
Also the menu entry seems a good idea, but probably the best will be the flash drive (for grub safety XD)

---

### Post by grahammechanical on 2016-04-15
When you install Lubuntu to sdx make sure that Grub is being intalled to sdx & not sda (default). Then use the BIOS settings to boot from sdx. You should get a boot menu that gives you options to load Lubuntu and any other OS in the machine.

If you disconnect those other drives before installing Lubuntu, than after installing Lubuntu & reconnecting those other drives load Lubuntu, open a terminal & run

```
sudo update-grub
```

That should then detect the other OSes on those other drives.

Regards

---

### Post by Hadden89 on 2016-04-15
I will post the grub.cfg as the usb boot does not work with unebootin.
I have my iso in windows partition, can I simply add a menu entry for that?
The guide says to put in /boot, but is the drive I am going to resize after the installation in a new drive.
A lot of things in the cfg are broken, as the latest kernels - 70 and 38, and the win 10 loader, which works but I dont need it.

```
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
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
else
  search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=it_IT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
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
 
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-FE8C573B8C56EDA1' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  FE8C573B8C56EDA1
    else
      search --no-floppy --fs-uuid --set=root FE8C573B8C56EDA1
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 10 (loader) (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-2064DDDD64DDB62E' {
    insmod part_msdos
    insmod ntfs
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  2064DDDD64DDB62E
    else
      search --no-floppy --fs-uuid --set=root 2064DDDD64DDB62E
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

### BEGIN /etc/grub.d/33_linux_proxy ###
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-4e619e66-caaf-4b36-992c-03c09dc1518e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
    else
      search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
    fi
    linux    /boot/vmlinuz-3.16.0-70-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-70-generic
}
submenu "Advanced options for Ubuntu"{
menuentry "Ubuntu, with Linux 3.16.0-70-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-70-generic-advanced-4e619e66-caaf-4b36-992c-03c09dc1518e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
        else
          search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
        fi
        echo    'Loading Linux 3.16.0-70-generic ...'
        linux    /boot/vmlinuz-3.16.0-70-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-70-generic
}
menuentry "Ubuntu, with Linux 3.16.0-70-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-70-generic-recovery-4e619e66-caaf-4b36-992c-03c09dc1518e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
        else
          search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
        fi
        echo    'Loading Linux 3.16.0-70-generic ...'
        linux    /boot/vmlinuz-3.16.0-70-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-70-generic
}
menuentry "Ubuntu, with Linux 3.16.0-38-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-advanced-4e619e66-caaf-4b36-992c-03c09dc1518e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
        else
          search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
        fi
        echo    'Loading Linux 3.16.0-38-generic ...'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-38-generic
}
menuentry "Ubuntu, with Linux 3.16.0-38-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-recovery-4e619e66-caaf-4b36-992c-03c09dc1518e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
        else
          search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
        fi
        echo    'Loading Linux 3.16.0-38-generic ...'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-38-generic
}
menuentry "Ubuntu, with Linux 3.16.0-30-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-4e619e66-caaf-4b36-992c-03c09dc1518e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
        else
          search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
}
menuentry "Ubuntu, with Linux 3.16.0-30-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-4e619e66-caaf-4b36-992c-03c09dc1518e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
        else
          search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
}
}
### END /etc/grub.d/33_linux_proxy ###

### BEGIN /etc/grub.d/34_linux_xen ###

### END /etc/grub.d/34_linux_xen ###

### BEGIN /etc/grub.d/35_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
    else
      search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  4e619e66-caaf-4b36-992c-03c09dc1518e
    else
      search --no-floppy --fs-uuid --set=root 4e619e66-caaf-4b36-992c-03c09dc1518e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/35_memtest86+ ###

### BEGIN /etc/grub.d/36_uefi-firmware ###
### END /etc/grub.d/36_uefi-firmware ###

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


```

*edit*
Ok, probably I'm on the right way :3
I moved my iso in /boot and then I used Grub customizer to create a bootable iso menuentry.
Then I'll install lubuntu in a new drive I attach (removing DVD unit) leaving untouched for now the one with win+linux
At this point I'll install grub on the new drive (should be auto if I use whole disk?) minus the sata which has 10 loader I'll remove, and the other drive which has another grub.
Then, if lubuntu will work, I'll use win partition tool to use all the disk as ntfs (the one in which there was win+linux, plus the lubuntu iso)
At last, using sudo update-grub, I'll fix any things that can occur. At this point probably all works, however.
Should I remove with grub customizer the voices I don't need before start? ("broken" kernels and win10 loader)
I'll backup the file, in any case.
Should I separate / from /home? (But usually I don't. Should be fifty-fifty?)

---

### Post by yancek on 2016-04-15
> I have my iso in windows partition, can I simply add a menu entry for that?

Yes, but add  'insmod ntfs' above the set root line in the entry.  I've never used Grub customizer so have no idea what you can do with it.  It's simpler to just use a / (root) and swap paartition.  You can always shrink a partition later to create an additional partition for data.

---

### Post by oldfred on 2016-04-15
The only option that gives a choice on where to install grub is Something Else. Otherwise grub auto installs to sda, overwriting your existing grub. You can repair it by booting into install in sda and reinstall grub to MBR, but better to use Something Else.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL]

---

### Post by Hadden89 on 2016-04-15
I used grub customizer (mainly a GRUB GUI editor) only for make a bootable and working Lubuntu ISO in dev/sda. (I used /boot folder of ext4 partition)
Ok, i'll use "something else" to put the bootloader (probably will be dev/sdb) in the right drive and I'll do a root (/) and 2gb of swap partition.
When lubuntu will work, with win I'll remove ext4/swap from /dev/sda (I'll ensure that grub is also on /dev/sdb) and extend the ntfs to whole disk.
This, shouldn't touch MBR. If need, I'll do sudo update-grub.

*edit*
Tested all the grub entries and they works :P
Probably, in new install, I've to extend a bit the /swap partiton as I did a bit small. Can I safely do with gparted using the other drive?
Should I update grub then in new install?

---

