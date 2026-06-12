---
title: "Installed Ubuntu 11.10 now getting &quot;missing operating system&quot;."
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by Alternal on 2011-12-04
Hi all,

This is my first experience with linux, and so far it has not gone well. I just tried to install Ubuntu 11.10. It seemed to install fine, that was until I tried to boot it. Now I just get the message "missing operating system". I removed my previously installed windows7 upon installing Ubuntu. Right now I am running directly of the installation disk. As I have said I am new to linux so I really am lost as how to fix this. Any help would be appreciated.

Thanks everybody, I'm looking forward to giving Ubuntu a try, I don't want to give up on it so soon.

---

### Post by darkod on 2011-12-04
Do you have a single disk or maybe a RAID setup?

Looks like the bootloader didn't install from what ever reason. If you can, from live mode follow the link in my signature and follow the instructions to download and run the boot info script. Then post the results here, it should help.

---

### Post by Alternal on 2011-12-04
> **darkod said:**
> Do you have a single disk or maybe a RAID setup?

Looks like the bootloader didn't install from what ever reason. If you can, from live mode follow the link in my signature and follow the instructions to download and run the boot info script. Then post the results here, it should help.

Thanks Darkod,

Im not sure if I have a single disk or a RAID, but I have a Dell Dimension 9150 if that is any help.

I downloaded the boot info script. Is the "Try Ubuntu" from the installation disk the live mode you are talking about? I tried to follow the instructions, but I cannot find applications. I have a feeling it is because the "Try Ubuntu" is not the live mode you were talking about.

Sorry for not being more helpful.

---

### Post by Alternal on 2011-12-04
I figured out how to use the boot info script so here are the results:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_bjiafifbge_ARRAY 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks for  on this drive.

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bjiafifbge_ARRAY1: _________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

isw_bjiafifbge_ARRAY2: _________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bjiafifbge_ARRAY5: _________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 512   617,654,271   617,653,760  83 Linux
/dev/sdb2         617,654,782   624,990,719     7,335,938   5 Extended
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb

Drive: isw_bjiafifbge_ARRAY _____________________________________________________________________

Disk /dev/mapper/isw_bjiafifbge_ARRAY: 320.0 GB, 319995248640 bytes
255 heads, 63 sectors/track, 38903 cylinders, total 624990720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bjiafifbge_ARRAY1                512   617,654,271   617,653,760  83 Linux
/dev/mapper/isw_bjiafifbge_ARRAY2        617,654,782   624,990,719     7,335,938   5 Extended
/dev/mapper/isw_bjiafifbge_ARRAY5        617,654,784   624,990,719     7,335,936  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bjiafifbge_ARRAY1 a734ed88-4d62-4fef-83a5-52d6fe069bd6   ext4       
/dev/mapper/isw_bjiafifbge_ARRAY5 7b63bffb-588c-4406-a261-c5a0f8f1e59c   swap       
/dev/sda                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bjiafifbge_ARRAY
isw_bjiafifbge_ARRAY1
isw_bjiafifbge_ARRAY5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_bjiafifbge_ARRAY1 /media/a734ed88-4d62-4fef-83a5-52d6fe069bd6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================== isw_bjiafifbge_ARRAY1/boot/grub/grub.cfg: ===================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set=root a734ed88-4d62-4fef-83a5-52d6fe069bd6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root a734ed88-4d62-4fef-83a5-52d6fe069bd6
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root a734ed88-4d62-4fef-83a5-52d6fe069bd6
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a734ed88-4d62-4fef-83a5-52d6fe069bd6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root a734ed88-4d62-4fef-83a5-52d6fe069bd6
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a734ed88-4d62-4fef-83a5-52d6fe069bd6 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root a734ed88-4d62-4fef-83a5-52d6fe069bd6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root a734ed88-4d62-4fef-83a5-52d6fe069bd6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

======================= isw_bjiafifbge_ARRAY1/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bjiafifbge_ARRAY1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bjiafifbge_ARRAY5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=========== isw_bjiafifbge_ARRAY1: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on isw_bjiafifbge_ARRAY2



=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
hexdump: /dev/mapper/isw_bjiafifbge_ARRAY2: No such file or directory
hexdump: /dev/mapper/isw_bjiafifbge_ARRAY2: No such file or directory

```

I hope that is of some help,
Thanks.

---

### Post by darkod on 2011-12-04
It is, usually some people call it live mode because you are running it from the cd.

The instructions are little outdated I guess. You are right, in the new interface there is no applications.

When you look at the toolbar on the left edge of the screen, the Unity bar, you need to click the first icon, the ubuntu logo. That will open the so called Dashboard (you can also open it by pressing the Windows logo key on the keyboard).
In its search bar just start typing Terminal and it will find it for you. In Terminal you can run the command to execute the script but be careful and look carefully where have you put the extracted script, the .sh file.

The command to execute will depend because you need to have the correct path, like:

sudo bash /path/boot_info_script*.sh

If the .sh file is in your Home folder, the whole path is just ~/ because the ~ sign replaces your Home folder. If the .sh is in Downloads, the path part would be ~/Downloads/ etc. You get the idea. The path needs to be correct so that the command can find the .sh file.

Also you should know that linux makes difference between small letters and capitals in the path, unlike windows. In linux /Downloads is not the same as /downloads. So you need to type exactly at it says. :)

---

### Post by darkod on 2011-12-04
Yeap, you either have a raid array but one disk is failing because /dev/sda should also be discovered by the script and it's not. Or you have single disk with raid meta data remains.

Are you interested in running a raid or not? Under assumption you have 2 disks at all. Any chance to have a quick peek if you have 2 HDDs inside? You would know to recognize the HDD I assume?

If you can't take a look, no problem. It's not necessary but we need to know if you want to run raid or not.

---

### Post by Alternal on 2011-12-04
I am not too sure what a raid is, so I don't know if I am interested in running a raid or not. There are 2 HDDs in this computer, I assume that means I want to run a raid. Is there any other information I could give you that would help?

Thanks again.

---

### Post by darkod on 2011-12-04
Since you already said you deleted windows and are not sure if you are running raid, I'm gonna go ahead and assume the meta data on the disk is a remain of older installation.

From live mode in terminal you can remove the meta data with:
sudo dmraid -E -r /dev/sdb

Just confirm when it asks you and it will remove it. After that repeat the install, that's easier than saving it. It's a new install with no data anyway.

It should work fine once the meta data is removed.

---

### Post by Alternal on 2011-12-04
Ok, followed your instruction so hopefully it is removed. Now, to install Ubuntu... again. Hopefully this time it will work.

Thanks for all the help, I will be back if It doesn't work again.

---

### Post by darkod on 2011-12-04
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

With two disks you could implement a software RAID1 if it sounds like a good idea to you. In short, you get additional redundancy of your data but the usable space is cut in half (like you have only one of the disks).

One HowTo for software raid I have at hand:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Don't forget, you will need to download and use the Alternate Install CD for implementing software raid.

If you need more advice either someone else can jump in or wait until tomorrow coz it's really late in my time zone and I gotta go. Got to get up for work tomorrow. :)

---

### Post by Alternal on 2011-12-04
I tried to install it again and... didn't work. But at least it didn't work in a different way. This time instead of the "Missing operating system" I get:

error: no such device: 17ff8c86-25f6-4257-93c0-b1f83d87aad4
grub rescue>

The first thing I noticed was that instead of Ubuntu installing to 320GB as it had last time, it installed to 160GB. After the installation didn't work this time, I went into the installer and went to "something else" and it only showed 160GB, instead of the 320GB it had before.

If you don't get a chance to read this until tomorrow thats ok, but I won't have free time until Tuesday afternoon to work on getting this working again, and then after that not until the weekend. If someone else wants to jump into the middle of this problem of mine thats fine with me.

Thanks for all the help.

---

### Post by darkod on 2011-12-05
OK. You seem to have two disks of 160GB. It was showing 320GB the first time because I suppose RAID0 was configured. You can read about different raid levels in the link I provided earlier.
Now the choice is up to you. RAID0 is not really recommended because the data is written half on one disk and half on the other. If one disk dies you can't recover the data, all is lost. This is because you can't recover from only half.
RAID1 for example is writing the same data on both disks, like a mirror. So if one disk dies the other continues working because it has all the data available. When you replace the faulty disk with a new one it synchronizes with the first one and the system continues working again as a mirror. But the downside is that only 160GB will be available for use because the other 160GB disk has the same data.

Or you can use the computer without any raid, which means you can use both 160GB disks for what ever you want. In this case you would install ubuntu on one disk and the other would serve as data disk.

If you want to continue without raid you also need to enter the BIOS and turn off the raid setting, this is very important. Usually you will need to change the SATA Configuration from RAID to AHCI. But depending on the bios the options might be called slightly different. Then you just go ahead with the install and make sure in bios you are booting from the disk you installed ubuntu on.

If you want to continue with raid the procedure is slightly different and we can discuss it.

---

