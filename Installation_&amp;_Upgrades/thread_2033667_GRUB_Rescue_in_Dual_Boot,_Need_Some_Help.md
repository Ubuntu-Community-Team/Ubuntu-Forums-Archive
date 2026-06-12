---
title: "GRUB Rescue in Dual Boot, Need Some Help"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by amt897 on 2012-07-26
Hey guys,

So I've been playing around with my system to a detriment, apparently.  I have a laptop with a 120 GB SSD split about 85/20 between Windows 7 and Ubuntu with, with a 750  GB HDD for storage as well.  I wanted to extend my Ubuntu partition, so I went to format over it and reinstall (I couldn't in gparted for whatever reason), and when I did I had some grub errors.  After reinstalling I would get an error whenever I tried to configure GRUB or update it, or even upgrade to Precise Pangolin.  However, my GRUB loader still worked just the same.

I posted the error message here:
[http://askubuntu.com/questions/167739/grub-cannot-update-but-does-recognize-all-partitions](http://askubuntu.com/questions/167739/grub-cannot-update-but-does-recognize-all-partitions)

A couple of days ago, but nobody responded.

Today I was playing around again and tried to change some of the device.map stuff and after a reboot, I was greeted with a GRUB recovery prompt.  I could boot into a Windows recovery disk and fix the MBR, but I want to fix this first.  It's looking for a device on /dev/sdb that should never have been there.  I haven't tried to install GRUB there knowingly.

I saw that someone had a boot info script and I ran that.  Here are the results from the Live CD:

```
  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/mt/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdb1 starts at sector 63. According to the info in the 
                       boot sector, sdb1 has 1465141247 sectors, but 
                       according to the info from fdisk, it has 1465147056 
                       sectors.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 2127944 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   176,766,975   176,355,328   7 NTFS / exFAT / HPFS
/dev/sda3         176,769,022   234,440,703    57,671,682   5 Extended
/dev/sda5         176,769,024   217,853,951    41,084,928  83 Linux
/dev/sda6         217,856,000   234,440,703    16,584,704  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,465,147,119 1,465,147,057  42 SFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32     7,905,278     7,905,247   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9E0677E10677B93B                       ntfs       System
/dev/sda2        801E7BEF1E7BDC9A                       ntfs       OS
/dev/sda5        0794bfe2-b2a8-4348-9dc2-214ed2935d3f   ext4       
/dev/sda6        33b4e6e6-1085-4976-bc0c-81ea877f6000   swap       
/dev/sdb1        72BA6B91BA6B50A1                       ntfs       AToombs Media
/dev/sdc1        1C0D-1F27                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    linux    /boot/vmlinuz-3.2.0-27-generic root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    echo    'Loading Linux 3.2.0-27-generic ...'
    linux    /boot/vmlinuz-3.2.0-27-generic root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    linux    /boot/vmlinuz-3.0.0-23-generic-pae root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    echo    'Loading Linux 3.0.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-23-generic-pae root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f ro recovery nomodeset 
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
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0794bfe2-b2a8-4348-9dc2-214ed2935d3f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 9E0677E10677B93B
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
UUID=0794bfe2-b2a8-4348-9dc2-214ed2935d3f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=33b4e6e6-1085-4976-bc0c-81ea877f6000 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-27-generic               2
               =                boot/initrd.img-3.2.0-27-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-27-generic                  1
               =                boot/vmlinuz-3.2.0-27-generic-pae              1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
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
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```I have everything important off of /dev/sda (the SSD) backed up, so if I do need to reinstall it's not the end of the world.  But I've exhausted Google (to the best of my abilities) and would really appreciate some help.

Thanks.

---

### Post by drs305 on 2012-07-26
There is an odd bit from the RESULTS.txt:
> 
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for **[COLOR="Red"](,msdos5)/mt/[/COLOR]**boot/grub on this drive.

Normally it's just (,msdos5)/boot/...

At the grub prompt, run these commands:
```
ls (hd0,5)/boot
ls (hd0,5)/mt/boot
```
Which one, if either, contains the normal boot files such as the kernel and initrd image?

---

### Post by darkod on 2012-07-26
Another thing I noticed is that your hdd seems to be dynamic disk (SFS type). Usually you can't install a functioning dual boot on dynamic disk because that's MS format and ubuntu doesn't work correctly on it. But in your case the dual boot is on the ssd so I have no idea if you can expect issues in the future.

---

### Post by drs305 on 2012-07-26
I'm going to be off for a while so I'll prepost in anticipation of your response.

If you find the kernel in (hd0,5)/mt/boot, try manually booting with these commands issued at the grub prompt:

```

set prefix=(hd0,5)/mt/boot/grub
set root=(hd0,5)
insmod linux
linux /mt/boot/vmlinuz-3.2.0-27-generic-pae root=/dev/sda5 ro
initrd /mt/boot/initrd.img-3.2.0-27-generic-pae
boot
```
This is non-perisistent. If you have to boot again, you will have to repeat the procedure until you fix your system.

The normal fix would be to move the /mt/boot folder to /boot. If no /boot folder exists, just click /mt/boot and drag the 'boot' folder to /. 

If /boot exists but is empty, open /mt/boot, CTRL-a to highlight all the contents (folders and files) and either copy or drag them into the /boot folder. 

Run "sudo update-grub" and watch the terminal output to make sure the kernel is found and added to the grub menu.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> I'm going to be off for a while so I'll prepost in anticipation of your response.

If you find the kernel in (hd0,5)/mt/boot, try manually booting with these commands issued at the grub prompt:

```

set prefix=(hd0,5)/mt/boot/grub
set root=(hd0,5)
insmod linux
linux /mt/boot/vmlinuz-3.2.0-27-generic-pae root=/dev/sda5 ro
initrd /mt/boot/initrd.img-3.2.0-27-generic-pae
boot
```
This is non-perisistent. If you have to boot again, you will have to repeat the procedure until you fix your system.

The normal fix would be to move the /mt/boot folder to /boot. If no /boot folder exists, just click /mt/boot and drag the 'boot' folder to /. 

If /boot exists but is empty, open /mt/boot, CTRL-a to highlight all the contents (folders and files) and either copy or drag them into the /boot folder. 

Run "sudo update-grub" and watch the terminal output to make sure the kernel is found and added to the grub menu.

Sorry, was away for a bit myself.  I appreciate the quick responses.

So I looked and everything is in /boot/, not /mt/boot-- my best guess here was that I tried to change some path to /mnt/boot and made a fatal typo.  PEBKAC

So I tried to do everything you outline above but removing the /mnt/ part.  When I did, it hung at "Refusing to bind to secondary interface".  Above that a few lines it said "mmc0: no vmmc regulator found".  After it hung for 5-10 seconds, I got "Gave up waiting for root device", etc. etc.  It also said /dev/sda5/ does not exist, and it dropped me to a BusyBox shell.

```
(initramfs)
```

That's where I'm at now.  Again,  I have nothing critical, particularly on my Ubuntu partition.  Windows partition would be  a bitch.  I have an 11.10 Ubuntu Live drive and a Windows recovery disk, so I can restore the MBR.  I guess if I can't fix this easily, should my next step be removing all traces of GRUB, fixing the MBR, formatting over the ext4 and swap partitions, and then reinstalling Linux on that partition?

If so, how do I get rid of grub on /dev/sdb1 as well?

---

### Post by drs305 on 2012-07-26
You indicated that the system reported that sda5 did not exist. Did you get returns when running "ls (hd0,5)/mt/boot"? It's possible that your BIOS and GRUB initially treat that drive as sdb, in which case it would be "ls (hd1,5)/mt/boot".

I don't know what's happening with your system unless the above is part of the issue. Perhaps *darkod's* observation merits more investigation.

Reinstalling may be a quicker option than troubleshooting, but that is your decision of course. If your Windows files are intact, restoring the Windows bootloader should be very easy from a LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  # Don't run any of the lilo config commands

```
This assumes sda is still considered your Windows drive.

If you decide to partition or resize, any operations involving the Windows partitions should be done with a Windows partitioner.

I'm a bit at a loss regarding your comment about GRUB on sdb1, which I don't see. If you mean in the sdb MBR (not the sdb1 partition), you could perhaps use Windows software to install something there. As long as the BIOS doesn't boot to that device first, it won't cause any problems.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> You indicated that the system reported that sda5 did not exist. Did you get returns when running "ls (hd0,5)/mt/boot"? It's possible that your BIOS and GRUB initially treat that drive as sdb, in which case it would be "ls (hd1,5)/mt/boot".

I don't know what's happening with your system unless the above is part of the issue. Perhaps *darkod's* observation merits more investigation.

Reinstalling may be a quicker option than troubleshooting, but that is your decision of course. If your Windows files are intact, restoring the Windows bootloader should be very easy from a LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  # Don't run any of the lilo config commands

```
This assumes sda is still considered your Windows drive.


sda is the drive for both Windows 7 and Ubuntu on it.  That won't have any issues with the sda mbr, right?

> If you decide to partition or resize, any operations involving the Windows partitions should be done with a Windows partitioner.

I'm a bit at a loss regarding your comment about GRUB on sdb1, which I don't see. If you mean in the sdb MBR (not the sdb1 partition), you could perhaps use Windows software to install something there. As long as the BIOS doesn't boot to that device first, it won't cause any problems.

Sorry-- that was related to the error I kept getting, which was in the first link I provided in the OP.  update-grub kept looking for a grub drive on /sdb1, which was weird.  Ideally I want to completely get rid of anything Ubuntu-related, and grub, and keep Windows.  Then I want to reinstall.  I think instead of doing the automated install, I may make my own partitions for /, /home, and swap.  If I do that, do I make a separate one for boot, or should I just write boot to /sda/ like normal?

---

### Post by drs305 on 2012-07-26
The lilo commands will write to the MBR - it will point the system back to the sda partition with the boot flag on it (your Windows sda1 partition). This should restore your Windows bootloader and as long as the Windows boot files have not been altered your Windows should boot normally.

You could also try installing lilo on sdb (but not sdb1). This would wipe out any GRUB reference on the sdb drive. Whether it would allow you to boot your Windows OS I'm not sure. I don't know enough about lilo to know if it would seek out the sda1 boot flag or not. In either case, GRUB wouldn't exist on the sdb MBR any longer.

I wouldn't make a separate /boot folder for Ubuntu unless your system has BIOS issues which limit it to seeing the first 137GB of the drive. In that case you may need to place a /boot drive within that limit, but otherwise I believe a /boot partition is more hassle than it's worth.

I also don't know a lot about the SFS designation of your sdb drive. You can use TestDisk to work with formats and partition problems if the partition table is incorrect or not reporting the proper format.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> The lilo commands will write to the MBR - it will point the system back to the sda partition with the boot flag on it (your Windows sda1 partition). This should restore your Windows bootloader and as long as the Windows boot files have not been altered your Windows should boot normally.

You could also try installing lilo on sdb (but not sdb1). This would wipe out any GRUB reference on the sdb drive. Whether it would allow you to boot your Windows OS I'm not sure. I don't know enough about lilo to know if it would seek out the sda1 boot flag or not. In either case, GRUB wouldn't exist on the sdb MBR any longer.

I wouldn't make a separate /boot folder for Ubuntu unless your system has BIOS issues which limit it to seeing the first 137GB of the drive. In that case you may need to place a /boot drive within that limit, but otherwise I believe a /boot partition is more hassle than it's worth.

I also don't know a lot about the SFS designation of your sdb drive. You can use TestDisk to work with formats and partition problems if the partition table is incorrect or not reporting the proper format.

lilo worked great, Windows is back up, thank you!

So my problem before was straight-up formatting over what Linux install I had.  Should I just re-format swap and the ext4 partitions in Windows, and then reinstall normally from there?

Also:  what about my partitions?  Set up /, /home, swap, and the boot dropdown just point to /dev/sda/, the default device?

I think that's what I tried last time, so I'm trying to understand what I did wrong.

---

### Post by drs305 on 2012-07-26
> **amt897 said:**
> lilo worked great, Windows is back up, thank you!

So my problem before was straight-up formatting over what Linux install I had.  Should I just re-format swap and the ext4 partitions in Windows, and then reinstall normally from there?

Also:  what about my partitions?  Set up /, /home, swap, and the boot dropdown just point to /dev/sda/, the default device?

I think that's what I tried last time, so I'm trying to understand what I did wrong.

If the Windows partitions will remain the same size and location, you don't need to use Windows. You can create the other partitions using Gparted and the LiveCD. 

If you have already made the partitions before you start the installation:
When you install from the Ubuntu CD, for partitioning choose the "Something Else" option. Select the partition(s), then the mountpoint (/, /home, /swap). If you haven't made a swap partition Ubuntu should do it for you. 

After selecting the partition and mountpoint, tick the "format" box - this will format the partition and remove any existing data.

One of the last steps of the installation is to put Grub on the drive. It should default to sda. You want to install it on the drive, but not any particular partition. This should be the default installation. It will overwrite the existing MBR information, but GRUB should add Windows to the menu and you can boot both.

If by chance you are going to install Ubuntu only to the other drive, place GRUB only on the non-Windows drive and change the BIOS boot order to boot the Ubuntu drive first. This will allow you to have the Grub bootloader on your Ubuntu drive and (as backup) keep the Windows bootload on the other drive.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> If the Windows partitions will remain the same size and location, you don't need to use Windows. You can create the other partitions using Gparted and the LiveCD. 

If you have already made the partitions before you start the installation:
When you install from the Ubuntu CD, for partitioning choose the "Something Else" option. Select the partition(s), then the mountpoint (/, /home, /swap). If you haven't made a swap partition Ubuntu should do it for you. 

After selecting the partition and mountpoint, tick the "format" box - this will format the partition and remove any existing data.

Okay, one final question-- and I really appreciate you going through this with me.

Since I'm not making a /boot partition, is it necessary to make any of the partitions primary?  Or is logical fine for all?  I'm assuming the latter since that's default.

---

### Post by drs305 on 2012-07-26
> **amt897 said:**
> Okay, one final question-- and I really appreciate you going through this with me.

Since I'm not making a /boot partition, is it necessary to make any of the partitions primary?  Or is logical fine for all?  I'm assuming the latter since that's default.

Logical is fine, in fact there are definitely advantages to it.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> Logical is fine, in fact there are definitely advantages to it.

Okay, so the reinstall worked fine.  I'm on the update to Precise and I get the same damn error...

```
umount: /var/lib/os-prober/mount: not mounted
rmdir: failed to remove `/var/lib/os-prober/mount': Device or resource busy
rmdir: failed to remove `/var/lib/os-prober/mount': Device or resource busy
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
done
```

Ctrl+c threatens I'll leave the system in a broken state, so the upgrade is stuck here.

Edit:  used lilo on both sda and sdb.

---

### Post by drs305 on 2012-07-26
If you can, see what is contained in /boot/grub/device.map. Normally it doesn't exist in a default installation, but perhaps one was created during yours.

If you are on the LiveCD, mount your Ubuntu partition (I'll assume sda5) and then look at the contents:
```
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/device.map
```
If it doesn't exist or is empty, use nautilus to search for device.map on the Ubuntu partition.

Also, what do you mean when you say you used 'lilo' on sda and sdb? Had you installed grub?

Added: If you find device.map and it has two lines, make a backup copy but then delete the sdb entry in the original.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> If you can, see what is contained in /boot/grub/device.map. Normally it doesn't exist in a default installation, but perhaps one was created during yours.

If you are on the LiveCD, mount your Ubuntu partition (I'll assume sda5) and then look at the contents:
```
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/device.map
```
If it doesn't exist or is empty, use nautilus to search for device.map on the Ubuntu partition.

I'm on my Ubuntu Installation.  There's nothing in the file when I open it in gedit.

---

### Post by drs305 on 2012-07-26
On a normal installation, of course, it would be /boot/grub/device.map

If it is empty, try creating it (gksu gedit /boot/grub/device.map) with the following entry:
> (hd0) /dev/sda
Try saving the file and then running "sudo update-grub"
If it still fails, add a second line:
> (hd1) /dev/sdb
or let Grub try to build it itself:
```
sudo grub-mkdevicemap
```

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> On a normal installation, of course, it would be /boot/grub/device.map

If it is empty, try creating it (gksu gedit /boot/grub/device.map) with the following entry:

Try saving the file and then running "sudo update-grub"
If it still fails, add a second line:

Same error message on both tries.

---

### Post by drs305 on 2012-07-26
> **amt897 said:**
> Same error message on both tries.

If you still have the device.map, this is the other thing you can try. I've never seen this, and don't know if GRUB will accept it or not, but it won't hurt anything. Replace sdb with sdb1:
> 
(hd1) /dev/sdb1


---

### Post by amt897 on 2012-07-26
Same issue.  This what what I had after I went deleting partitions on Monday.

---

### Post by drs305 on 2012-07-26
What do you have on sdb1? The partition table, according to the info script, is messed up.

I can think of several things we could try:
Disconnect sdb temporarily and then running update-grub
Using TestDisk to repair the partition table
Writing Test Disk to the MBR and possibly sdb1
Reformatting the sdb drive completely.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> What do you have on sdb1? The partition table, according to the info script, is messed up.

All media files-- music, etc.  It's one big NTFS partition.  My only guess was that I tried to install one time without deleting the old Linux partition, but it didn't detect it was there, so it may have automatically partially installed some stuff to /sdb1 before I canceled it.

---

### Post by drs305 on 2012-07-26
> **amt897 said:**
> All media files-- music, etc.  It's one big NTFS partition.  My only guess was that I tried to install one time without deleting the old Linux partition, but it didn't detect it was there, so it may have automatically partially installed some stuff to /sdb1 before I canceled it.

Are you still able to access the contents of that partition, either via Ubuntu or with Windows?

Do you have so much data on it you can't copy it elsewhere and reformat it?

An option before doing that would be to disconnect it entirely and running the GRUB commands to see if you can get Grub to work without it being connected. If you do that and remove (hd1) from device.map I don't know if GRUB is going to complain or not.

---

### Post by amt897 on 2012-07-26
> **drs305 said:**
> Are you still able to access the contents of that partition, either via Ubuntu or with Windows?

Do you have so much data on it you can't copy it elsewhere and reformat it?

An option before doing that would be to disconnect it entirely and running the GRUB commands to see if you can get Grub to work without it being connected. If you do that and remove (hd1) from device.map I don't know if GRUB is going to complain or not.

As of earlier today, I could get it to work fine.  I was listening to music off of it.

I could reformat it, but I'd prefer not to.  There's no essential data on it, it would just take forever to copy back.  But if there are no other options I could do that.

Edit:  As for disconnecting it, it's an internal drive and it'd be very hard to remove-- it's in this weird cage in the optical drive slot.

---

### Post by drs305 on 2012-07-26
> **amt897 said:**
> As of earlier today, I could get it to work fine.  I was listening to music off of it.

I could reformat it, but I'd prefer not to.  There's no essential data on it, it would just take forever to copy back.  But if there are no other options I could do that.

I wouldn't do that yet, especially if it is usable. I would try unplugging it and seeing if GRUB will update.

If not, the next thing I would concentrate on is the sdb1 partition table. The script says sdb1 is SFS, but elsewhere it is identified as NTFS, which is more likely. Do you know why it is listed as SFS?

My thought is that the designation should be changed to NTFS (7). This can be done using fdisk with an umounted partition. I know how to change the partition type to NTFS but would feel more comfortable if you knew that it shouldn't be listed as SFS or know how it got changed.

---

### Post by amt897 on 2012-07-26
Sorry, I edited above.  The drive is in a weird contraption in the optical drive and it's difficult to remove.

I have no idea-- I haven't touched that disk, really.  Think I should try to convert it?

---

### Post by oldfred on 2012-07-26
As Darko mentioned above the SFS says it is dynamic not basic in Windows. Windows does not use extended partition when  you try to add more than 4 partitions but converts to a dynamic partition scheme which is like LVM in Linux. It will still be NTFS inside, but the Linux NTFS driver will not work with it. Even some Windows repair tools have issues with dynamic partitions, so I would remove it, but it is not without risk.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by drs305 on 2012-07-26
> **amt897 said:**
> Sorry, I edited above.  The drive is in a weird contraption in the optical drive and it's difficult to remove.

I have no idea-- I haven't touched that disk, really.  Think I should try to convert it?

I have to log off in a minute. I assume it's an NTFS partition. You can try to change it although I don't know if that is what is causing the issue. 

The other option would be to start a new post, including the section of RESULTS.txt which concerns sdb1. I'd mention that it shows SFS but you think it's NTFS. You might get some different opinions. The partition table looks like there are problems - it may be just the SFS designation that is causing it or something bigger. I hesitate to go messing with the actual partition table (other than the type) if you are still able to use it/get data off it.

If you want to try to change the type (only), which can be changed back:
```
sudo umount /dev/sdb1 # In case it is mounted.
sudo fdisk /dev/sdb

```
Then type the first character of each line:
t # 
1 # Partition number (that is numeral 1 )
7 # NTFS Partition type
w # Write
Then reboot.

---

### Post by drs305 on 2012-07-26
I'm logging off for the night. Whatever you decide to do, for the helpers it would probably be best to recap where you are at the moment regarding your system:

Did you try to fix the partition type?
Can you boot into Ubuntu? Using Grub? Lilo?
Which version (did it complete the upgrade)?  (uname -r)
What are the latest error messages?
Please run and post a new boot info script RESULTS content.

I'll check back tomorrow morning if work doesn't call me first.

---

### Post by amt897 on 2012-07-26
Oldfred, thanks for the links.

drs305, fdisk worked.  My problem was on 11.10 after I deleted 12.04 and reinstalled to 11.10 again.  fdisk exactly like you said fixed the type, so I don't know how SFS got enabled, but it did.

Again, thank you.  I'll figure out how to mark this solved now.

---

### Post by amt897 on 2012-07-27
> **drs305 said:**
> I'm logging off for the night. Whatever you decide to do, for the helpers it would probably be best to recap where you are at the moment regarding your system:

Did you try to fix the partition type?
Can you boot into Ubuntu? Using Grub? Lilo?
Which version (did it complete the upgrade)?  (uname -r)
What are the latest error messages?
Please run and post a new boot info script RESULTS content.

I'll check back tomorrow morning if work doesn't call me first.

Marked it solved, but it's only kinda solved.  Ubuntu works great, but that disk is now RAW instead of NTFS.  So Windows/Ubuntu can see it, but can't access it.  Tried to mount it, but I'm prompted to format it.  Marking unsolved...

Edit: Just ended up formatting it.  Thank you for all the help.  I'll mark it solved finally.

---

### Post by drs305 on 2012-07-27
> **amt897 said:**
> Marked it solved, but it's only kinda solved.  Ubuntu works great, but that disk is now RAW instead of NTFS.  So Windows/Ubuntu can see it, but can't access it.  Tried to mount it, but I'm prompted to format it.  Marking unsolved...

Edit: Just ended up formatting it.  Thank you for all the help.  I'll mark it solved finally.

Did you lose any data? If it was the sdb partition it's something we probably could have fixed with a command or two. Anyway, I'm sorry we didn't get you a better and quicker solution. Happy Ubuntu-ing !

---

### Post by oldfred on 2012-07-27
NTFS partition boot sector has to have a NTFS boot signature. In Windows when it is missing it is RAW.

I think the partition change did not fully convert it back from dynamic to NTFS like it should have. I still might try the solutions posted above. I have seen a variety of ways that users converted from dynamic, and one did say testdisk worked also. If testdisk does work then it may just be recoveringrecreating the NTFS partition boot sector.

---

