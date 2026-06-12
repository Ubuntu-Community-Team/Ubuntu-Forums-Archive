---
title: "cannot uninstall or upgrade or delete Ubuntu 11.04?"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by iBradleyAllen on 2011-11-25
hi

The computer runs a dual boot Windows Vista 64b and Ubuntu, apparently version 11.04 installed April 2011

Had problems where it reported to be out of disk space.  Went to windows and deleted files, then ran the partition resize utility and made the windows part smaller..  Ubuntu installation started but firefox would error out and not start.  Decided to uninstall the Ubuntu and start again.  tried uninstall from windows add/remove programs.  still there.  tried to download wubi again, it says must run uninstall first, did that but it was uninstalled in 2 seconds? didnt seem right.  still boots up and Ubuntu is there. tried may many things and the linux will not uninstall no matter what.  Deleted the /ubuntu folder from Windows.  still boots up and all the files are still there.

had downloaded Kubuntu 2 times and ran the wubi installer for it (or vice versa), no kubuntu. there is an entry in the boot loader but its regular ubuntu and it gets to the login screen, i put the username/pwd and it blanks the screen and starts to load then goes back to the login.  went into recovery console, typed X and it started but then errored out.  somehow got the old Ubuntu to start, and firefox now works.  am there now.  i had tried to upgrade, that starts out then fails saying not enough disk space.

want to just have a 25Gb installation thats fresh and working.  wubi installer does not uninstall, something wrong and its ok to fully get rid of linux and start over, lots of time trying to fix it... thanks

---

### Post by bcbc on 2011-11-25
Please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by iBradleyAllen on 2011-11-25
> **bcbc said:**
> Please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

very interesting, thanks.  i downloaded and extracted this and will run it when linux boots next (now on windows).  ive also tried installing kubuntu on another drive in the system, it crashed on startup saying some message that it should be bootable 'now';  booting it gets the kubuntu screen for 1second then goes to a command line, it doesnt know 'sudo' says command not found.  

its mid way on installing another kubuntu on another drive, why does it insist in downloading for 22 minutes some big .iso file? why doesnt it just use what's there? (as in the same exact .iso file i already downloaded a few times?)

ran the windows control panel admin. tools computer management, disk manager and it does not show any partition thats blank, just NTFS ones.  tried making an unallocated disk of 20Gb but the wubi installer didnt see it.  put that back into C and now its doing the install process.  VERY interested to see the results of the bootinfoscript and will post here
thanks

---

### Post by darkod on 2011-11-25
I see you mentioned the wubi installer and in your first post a dual boot. So lets get this straight first.
Wubi IS NOT a dual boot. Wubi is ubuntu installed virtually inside windows, similar to windows programs.
You have only NTFS partitions because you never had a dual boot. And even if you create unallocated space on your hdd, wubi will ignore it because it installs on NTFS.
If you boot with the ubuntu cd instead, and start the install process, that should install fine into any unallocated space.

And one more thing, I wouldn't recommend installing 2 or 3 times without knowing what you actually have. Sort it out first.

PS. I don't use wubi but from what I remember you need to put wubi.exe and the ISO for the same version together in the same folder, and then it will use that ISO. In all other cases it starts downloading from the internet even if you have the ISO on the disk (if it's not in the same folder).

---

### Post by iBradleyAllen on 2011-11-25
> **bcbc said:**
> Please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")
ok just ran it,

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/mapper/isw_cgheacfdce_MYRAID5.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdd1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdd2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

isw_cgheacfdce_MYRAID51: ____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   625,151,999   625,149,952   7 NTFS / exFAT / HPFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   567,175,167   567,173,120   7 NTFS / exFAT / HPFS
/dev/sdd2         567,175,168   976,771,071   409,595,904   7 NTFS / exFAT / HPFS


Drive: isw_cgheacfdce_MYRAID5 _____________________________________________________________________

Disk /dev/mapper/isw_cgheacfdce_MYRAID5: 320.1 GB, 320079134720 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625154560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cgheacfdce_MYRAID51   *          2,048   625,151,999   625,149,952   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       95dcdaa0-a143-44e0-a26d-f62e42ff161e   ext4       
/dev/mapper/isw_cgheacfdce_MYRAID5p1 D0CAD651CAD63386                       ntfs       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc                                                isw_raid_member 
/dev/sdd1        7804A24404A2056A                       ntfs       
/dev/sdd2        92F44A07F449EE53                       ntfs       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cgheacfdce_MYRAID5
isw_cgheacfdce_MYRAID5p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /tmp/BootInfo0/sdd1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sdd1/Wubi/boot/grub/grub.cfg: =========================

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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sdd,msdos2)'
search --no-floppy --fs-uuid --set=root 92F44A07F449EE53
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 92F44A07F449EE53
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=92F44A07F449EE53 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 92F44A07F449EE53
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=92F44A07F449EE53 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_cgheacfdce_MYRAID5p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set=root D0CAD651CAD63386
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

============================= sdd1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdd1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   9.320316315 = 10.007613440   boot/grub/grub.cfg                             1
   3.062500000 = 3.288334336    boot/initrd.img-2.6.38-8-generic               2
   6.371402740 = 6.841241600    boot/vmlinuz-2.6.38-8-generic                  1
   3.062500000 = 3.288334336    initrd.img                                     2
   6.371402740 = 6.841241600    vmlinuz                                        1

======================== sdd2/Wubi/boot/grub/grub.cfg: =========================

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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sdd,msdos2)'
search --no-floppy --fs-uuid --set=root 92F44A07F449EE53
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 92F44A07F449EE53
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=92F44A07F449EE53 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdd,msdos2)'
    search --no-floppy --fs-uuid --set=root 92F44A07F449EE53
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=92F44A07F449EE53 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_cgheacfdce_MYRAID5p1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set=root D0CAD651CAD63386
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

============================= sdd2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdd2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   9.320316315 = 10.007613440   boot/grub/grub.cfg                             1
   3.062500000 = 3.288334336    boot/initrd.img-2.6.38-8-generic               2
   6.371402740 = 6.841241600    boot/vmlinuz-2.6.38-8-generic                  1
   3.062500000 = 3.288334336    initrd.img                                     2
   6.371402740 = 6.841241600    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on isw_cgheacfdce_MYRAID51



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/mapper/isw_cgheacfdce_MYRAID51: No such file or directory
hexdump: /dev/mapper/isw_cgheacfdce_MYRAID51: No such file or directory

---

### Post by iBradleyAllen on 2011-11-25
hi
Thanks so much for clarifying this, i was certainly mixing "dual boot" with "wubi based install" because its a machine that has both OS's, its very different if wubi is only existing within the Windows partition.

This is really what I prefer, to have it contained within Windows; At some point when there is a new hard drive the machine can be either way

after 3 install attempts today of uninstalling kubuntu then re-installing, have it reboot only to come up to the same old 11.04, no kubuntu mentioned anywhere, no disk space to upgrade or do much.

could I add an external backup drive and install kubuntu to and boot from that?  dont care about space right now as much as just making the thing WORK




> **darkod said:**
> I see you mentioned the wubi installer and in your first post a dual boot. So lets get this straight first.
Wubi IS NOT a dual boot. Wubi is ubuntu installed virtually inside windows, similar to windows programs.
You have only NTFS partitions because you never had a dual boot. And even if you create unallocated space on your hdd, wubi will ignore it because it installs on NTFS.
If you boot with the ubuntu cd instead, and start the install process, that should install fine into any unallocated space.

And one more thing, I wouldn't recommend installing 2 or 3 times without knowing what you actually have. Sort it out first.

PS. I don't use wubi but from what I remember you need to put wubi.exe and the ISO for the same version together in the same folder, and then it will use that ISO. In all other cases it starts downloading from the internet even if you have the ISO on the disk (if it's not in the same folder).

---

### Post by darkod on 2011-11-25
1. You seem to have a fakeraid RAID5 array consisting of three disks, /dev/sda, /dev/sdb and /dev/sdc. Is that right?

2. You also seem to have 2 different wubi installs on the fourth disk, on partitions /dev/sdd1 and /dev/sdd2.

Do you want to continue using wubi or you want to create a proper dual boot? What is your goal?

---

### Post by iBradleyAllen on 2011-11-25
> **darkod said:**
> 1. You seem to have a fakeraid RAID5 array consisting of three disks, /dev/sda, /dev/sdb and /dev/sdc. Is that right?

I havent heard of fakeraid, it might be, its the raid system from the motherboard, Asus p5wdh and there are 3 physical drives to make one "disk"

those are 160Gb each so its 2 x 160 = 320Gb and the 3rd disk is for the error correction.


Then there is a Hitachi 500Gb but its not showing up as I expected... no problems until now with disks/installs

2. You also seem to have 2 different wubi installs on the fourth disk, on partitions /dev/sdd1 and /dev/sdd2.

Do you want to continue using wubi or you want to create a proper dual boot? What is your goal?
the goal is to have the os contained within the windows framework so there is less risk to windows files being accidentally changed;  make the wubi work if possible.  Then in about a month or so make a proper dual boot system from scratch.
thanks

---

### Post by bcbc on 2011-11-25
> **iBradleyAllen said:**
> hi
Thanks so much for clarifying this, i was certainly mixing "dual boot" with "wubi based install" because its a machine that has both OS's, its very different if wubi is only existing within the Windows partition.

This is really what I prefer, to have it contained within Windows; At some point when there is a new hard drive the machine can be either way

after 3 install attempts today of uninstalling kubuntu then re-installing, have it reboot only to come up to the same old 11.04, no kubuntu mentioned anywhere, no disk space to upgrade or do much.

could I add an external backup drive and install kubuntu to and boot from that?  dont care about space right now as much as just making the thing WORK
Wubi is a dual boot. If you want to run Ubuntu contained within Windows you need a virtual machine.  Wubi Ubuntu uses a virtual partition, but it boots completely separate from Windows.

From the bootinfoscript, there appear to be two installs, but they are identical - even the physical location of the boot files. So either it's a straight copy or the bootinfoscript is confused by the RAID. Also, if you've deleted the \ubuntu directory then the wubi install is gone. If it magically reappeared then you probably have something messed up with the RAID and it's 'recovering' the data.

I don't know a lot about RAID, but [manually uninstalling the Wubi install]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F") should be permanently fatal for Wubi.

---

### Post by iBradleyAllen on 2011-11-25
I have ubuntu installed on 3 other machines where they got installed from running in windows, downloading the thing to let them run alongside windows or whatever its termed;  they all ran just fine, but i do not have access to any of these and need to get one running again.

All I expect is that whatever installed this is able to change whatever it needs or give me the option to delete the installation.  So far its not able to do this or I have not found the right program to launch to delete the install and start over.  




> **bcbc said:**
> Wubi is a dual boot. If you want to run Ubuntu contained within Windows you need a virtual machine.  Wubi Ubuntu uses a virtual partition, but it boots completely separate from Windows.

From the bootinfoscript, there appear to be two installs, but they are identical - even the physical location of the boot files. So either it's a straight copy or the bootinfoscript is confused by the RAID. Also, if you've deleted the \ubuntu directory then the wubi install is gone. If it magically reappeared then you probably have something messed up with the RAID and it's 'recovering' the data.

I don't know a lot about RAID, but [manually uninstalling the Wubi install]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F") should be permanently fatal for Wubi.

---

### Post by darkod on 2011-11-25
Not to repeat things, but that link to manually deinstall wubi should get you going to delete both installs on /dev/sdd1 and /dev/sdd2.

And I have to address what you mentioned about wubi being a way to avoid touching the windows files by error. Actually my belief is that the dual boot is much better at that because unless you mount your windows partitions on purpose, you are never touching them. They don't exist for ubuntu.
The only thing to watch out would be messing with the partitions but that is a risk in any kind of setup. :)

But of course you are free to install and use whatever works best for you and you are most comfortable with. We are not trying to get you use one thing or the other.

Remove both wubi installs you have and just make another one.

And since you mentioned the possibility in the future to install dual boot on the raid, DO NOT FORGET that you need to use the alternate install cd to install on raid, not the standard desktop cd. Most people ignore this recommendation and get in all sorts of trouble.

PS. The message you were seeing about wubi not having enough space is probably related to the size you allocate for wubi during the install. Linux in general is not space consuming but don't forget to allocate wubi at least 15-20GB or even more if you have the free space, to make sure it has enough to breathe.

---

