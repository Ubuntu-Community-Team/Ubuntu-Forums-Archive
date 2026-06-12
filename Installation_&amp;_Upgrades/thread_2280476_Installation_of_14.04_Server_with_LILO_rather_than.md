---
title: "Installation of 14.04 Server with LILO rather than GRUB"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by davzd on 2015-05-30
I recently tried installing a clean install of Ubuntu Server x64 14.04.2 (just downloaded earlier today). Everything seemed to go smoothly, but when I rebooted after taking out the USB stick I used to install, all I got was a blank screen. I then went back and checked my notes as I had tried a test install on I believe a much earlier version (maybe 12.04?) and experienced the same problem, but was successful when I tried selecting LILO rather than GRUB. However, there doesn't seem to be an option to do this any more - GRUB seems to be installed automatically, without the ability to choose (which I recall was in the previous version). 

I was wondering if anyone would know which version had the ability to choose between GRUB and LILO or, alternatively, if there's a relatively simple way to replace GRUB with LILO on an unbootable system. I tried booting again from the USB to recover, but there still doesn't seem to be an option to install LILO. But I'm sure I'm missing something (as I'm somewhat a newbie to Ubuntu). I also tried searching a fair bit - was able to find some material on replacing GRUB with LILO, but unfortunately seemed to be oriented to someone who could already boot into their system, which I can't. Also of course open to any other thoughts or suggestions as to how to fix an unbootable system - not even sure how to diagnose something like this, seeing as how the system just doesn't boot.

In case it's relevant, I suspect this is due to the fact that the machine I'm trying to install it on is rather old - dates from circa 2008 - an old Rackspace S5000PSL. Currently only one single 500 GB drive and Ubuntu is the only thing I'm trying to install.

Also tried a couple of different times - first time installing an image using the Universal USB Installer (pendrivelinux.com), second time using Rufus. Not sure if relevant, but oddly enough I got a different install screen between the two and slightly different menu options, even though it was supposedly the same image being written to the USB. The first time had many more options for additional stuff (e.g. Mythbuntu, VM hosting, etc.) while the second time it did not (and seemed to go much faster). Also tried 14.04.1. However, each time I've tried (been about 4 now), when I reboot, it's still the same blank screen.

Any guidance, suggestions or recommendations would certainly be most appreciated.

---

### Post by davzd on 2015-05-31
I managed to boot a LiveCD and ran a boot info script. As far as I can tell, everything seems normal:

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......}..9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 3200754 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048   943,230,975   943,228,928  83 Linux
/dev/sda2         943,233,022   976,771,071    33,538,050   5 Extended
/dev/sda5         943,233,024   976,771,071    33,538,048  82 Linux swap / Solaris




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 2003 MB, 2003828736 bytes
43 heads, 42 sectors/track, 2167 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *             32     3,913,727     3,913,696   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/loop1       0dbe5d83-2c86-e74b-b078-e9c6a5d6e1d8   ext2       
/dev/sda1        9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718   ext4       
/dev/sda5        f64f7dba-dcc5-4f32-adac-eba55dc53e52   swap       
/dev/sdb1        0FE7-1655                              vfat       UUI


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sda1/boot/grub/grub.cfg: ===========================


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
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
else
  search --no-floppy --fs-uuid --set=root 9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
    else
      search --no-floppy --fs-uuid --set=root 9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
    fi
    linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718 ro  
    initrd    /boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718' {
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
        else
          search --no-floppy --fs-uuid --set=root 9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
        else
          search --no-floppy --fs-uuid --set=root 9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
    else
      search --no-floppy --fs-uuid --set=root 9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
    else
      search --no-floppy --fs-uuid --set=root 9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
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


=============================== sda1/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9dbbc0a0-cb6e-4ac6-b6e2-931399aa7718 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f64f7dba-dcc5-4f32-adac-eba55dc53e52 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




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


menuentry "Install Ubuntu Server" {
    set gfxpayload=keep
    linux /install/netboot/ubuntu-installer/amd64/linux cdrom-detect/try-usb=true noprompt NULL=vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
    initrd /install/netboot/ubuntu-installer/amd64/initrd.gz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux /install/netboot/ubuntu-installer/amd64/linux cdrom-detect/try-usb=true noprompt NULL=vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet oem-config/enable=true --
    initrd /install/netboot/ubuntu-installer/amd64/initrd.gz
}
menuentry "Multiple server install with MAAS" {
    set gfxpayload=keep
    linux /install/netboot/ubuntu-installer/amd64/linux cdrom-detect/try-usb=true noprompt NULL=vmlinuz  modules=maas-enlist-udeb vga=788 initrd=/install/initrd.gz quiet --
    initrd /install/netboot/ubuntu-installer/amd64/initrd.gz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux /install/netboot/ubuntu-installer/amd64/linux cdrom-detect/try-usb=true noprompt NULL=vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
    initrd /install/netboot/ubuntu-installer/amd64/initrd.gz
}
menuentry "Rescue a broken system" {
    set gfxpayload=keep
    linux /install/netboot/ubuntu-installer/amd64/linux cdrom-detect/try-usb=true noprompt NULL=vmlinuz  rescue/enable=true --
    initrd /install/netboot/ubuntu-installer/amd64/initrd.gz
}
--------------------------------------------------------------------------------


============================== sdb1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent


label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit  persistent


label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- persistent


label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent


label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent


label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit  persistent


label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit  persistent


--------------------------------------------------------------------------------


=================== sdb1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




================= sdb1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)




============== sdb1: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-aqrXYX6t/Tmp_Log: No such file or directory
/home/ubuntu/Downloads/bootinfoscript-061/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-aqrXYX6t/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-aqrXYX6t/Tmp_Log: No such file or directory
  No volume groups found



```

---

### Post by oldfred on 2015-05-31
Please use code tags for longer text.

Some older systems have issues with newer larger drives. They could only boot if all boot files were in the first 137GB of the drive. So either / (root) should be smaller and fully within the first part of drive or separate /boot at beginning of drive. I normally suggest & use 20 or 25GB for / and rest of drive as data or /home.

Report did leave blank the locations of files, so that may indicate it is part of issue.

You can quickly test is that is issue, by using Desktop live installer and gparted or a gparted liveCD and shrink the / partition to 100GB or less. If it then works you can create /home or data partitions or reinstall. This suggestion has only worked on about half of those I suggest so no guarantees.

---

### Post by davzd on 2015-05-31
Oops. Very sorry about that. I mistakenly used quote rather than code tags. Thanks very much for the suggestion, but it appears the issue was not with the system.

I was able to find instructions elsewhere on how to replace GRUB with LILO and tried that. Perhaps not surprisingly it didn't work - I got a "No boot signature in partition" edition and tried researching that but it didn't lead anywhere.

So I decided I had nothing left to lose by trying yet another installation, this time from the LiveCD I had created using unetbootin. I suspected it was a desktop version but figured I had nothing to lose. Ran through and, amazingly, this time it booted up just fine. Not sure why or what had gone wrong the last several times when I had tried creating a bootable USB stick from an image of the server. I would think that installs would be the same regardless. 

In any event, I really do appreciate your thoughts on the issue, oldfred, and taking the time to respond. I suspect given the age of the box, it won't be the last problem I have, which makes me wonder if I should perhaps consider replacing it with something a bit more current...

---

### Post by davzd on 2015-06-01
Well, this is a bit frustrating. As noted above, I was able to install the desktop version just fine. I then tried converting it to a server install using the following:

```

sudo apt-get install tasksel
sudo tasksel install server

```

There were some updates available in Software Center, so I updated those as well. It prompted me to reboot, and boom, same place as before. Just a dead, blank screen. It blinks a bit after BIOS finishes up and then nothing. When I power down if an OS is actually running, I need to hold the button down. But in this state, a quick press and it shuts down right away.

I imagine this has something to do with some element of the server that I'm trying to install, though I'm surprised it would cause such a severe problem. Given the nature of the problem, not really sure where to begin. Any help would be most appreciated.

---

### Post by davzd on 2015-06-01
Sorry - should have mentioned that I also installed openssh server, though I don't think that had anything to do with it.

---

### Post by oldfred on 2015-06-01
I do not really know server installs. But it is just more software on top of the same grub & kernel.

Did you use a smaller / (root) partition on second install? 
Even the first install may have had all boot files inside the 137GB, but an update installed a file beyond that point. 

If running Desktop version you can try running Boot-Repair which runs the same bootinfosummary but includes more info and can reinstall grub.

Your Lilo install sounded like you only had the MBR updated. Lilo works like a Windows boot loader and can be a Windows boot loader if you just install the MBR part. It looks for the partition with the boot flag and jumps to more code in the partition boot sector and then menus & more code in the /boot partition. But it seemed like you did not have the full Lilo install.

---

### Post by davzd on 2015-06-01
Thanks again oldfred. Yes, I would have thought updating or adding server modules wouldn't actually break things so badly, but it looks like they have.

No, I didn't use a smaller root partition, but you do raise a good point - I will try that with a LiveCD, as well as your suggestions for boot-repair.

As for LILO, based on the instructions I've seen elsewhere, supposedly all that is needed is sudo lilo -M /dev/sda mbr if replacing grub. I also checked the partitions - and /dev/sda1 did seem to have the boot flag. Very puzzling.

---

### Post by oldfred on 2015-06-01
That instruction on Lilo is just the MBR, more for booting Windows as Linux does not have the actual Windows boot loader due to copyright.

I had installed Lilo just to test it for booting Windows, but always have used grub and grub2. But after I installed Lilo, I would always get error messages on kernel updates that Lilo was not correctly configured. Never fully installed Lilo as a Linux boot loader.

Found this in my old notes, but I still suggest & prefer grub2:
Lilo info
[http://tldp.org/HOWTO/LILO.html#toc2](http://tldp.org/HOWTO/LILO.html#toc2)

---

### Post by davzd on 2015-06-01
Thanks again oldfred. Since I was able to get GRUB to work (at least for a while), hoping to stick with it.

---

