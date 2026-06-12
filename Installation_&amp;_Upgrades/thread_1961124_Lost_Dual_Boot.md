---
title: "Lost Dual Boot"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by deemasaurus on 2012-04-18
Hey guys,

I have a Dell XPS 17 laptop almost a year ago a dual booted ubuntu 10.4 using Wubi on my windows 7 machine. Everything was A ok and over time for some reason I stopped using Ubuntu (bad idea). Recently I decided to boot it up because windows was pissing me off again (original reason I dual booted) so i went to update ubuntu to 11.04 but it wasn't working so i bought a linux magazine that had a linux cd and installed that way. I saw the option to replace windows I choose no, left the house came back and everything was fine i rebooted my system and now when I boot I don't see an option to boot my windows. Any ideas on what could have happened?

---

### Post by strask on 2012-04-18
So it sounds like linux is working, right?

Try ```
sudo parted
```
Then at the parted prompt type ```
print
```
Look at the list and see if your NTFS partition is still there, for starters.
Type ```
quit
``` to get out of parted.

So assuming you didn't somehow replace windows, it seems like grub probably just needs to be reconfigured to give you the dual boot choice again. Paste in the output from the print command here so that we know what your disk layout is and someone can probably help you with specific grub commands.

---

### Post by darkod on 2012-04-18
Run the boot info script from the link in my signature and post the results as explained there. It will show more details.

---

### Post by deemasaurus on 2012-04-18
> **strask said:**
> So it sounds like linux is working, right?

Try ```
sudo parted
```Then at the parted prompt type ```
print
```Look at the list and see if your NTFS partition is still there, for starters.
Type ```
quit
``` to get out of parted.

So assuming you didn't somehow replace windows, it seems like grub probably just needs to be reconfigured to give you the dual boot choice again. Paste in the output from the print command here so that we know what your disk layout is and someone can probably help you with specific grub commands.

here are the results 

Number    Start             End            Size         Type         File system    Flags
 1                 32.3kB    65.8MB    65.8MB     primary   fat16                     diag
 2                 66.1MB   13.4GB    13.4GB     primary   ext4
 3                 13.4GB    500GB      487GB       primary
 4                 500GB      500GB     1065kB     primary     ntfs                       boot, hidden

---

### Post by Petkus on 2012-04-18
HI!

I have similar problem, but in opposite way. I installed Win7 on my Ubuntu and now I can't boot it. Only Win7. So I got angry and formated Win7 partition (you can destroy evil only from it's root) and started to install Ubuntu once more, but installation shows me, that Ubuntu is still on my PC.

How can I boot my good, old Ubuntu?

---

### Post by darkod on 2012-04-18
> **Petkus said:**
> HI!

I have similar problem, but in opposite way. I installed Win7 on my Ubuntu and now I can't boot it. Only Win7. So I got angry and formated Win7 partition (you can destroy evil only from it's root) and started to install Ubuntu once more, but installation shows me, that Ubuntu is still on my PC.

How can I boot my good, old Ubuntu?

You didn't need to delete windows. You only needed to restore the grub2 bootloader to the MBR since the windows installation overwrote it with the windows bootloader.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Petkus on 2012-04-18
> **darkod said:**
> You didn't need to delete windows. You only needed to restore the grub2 bootloader to the MBR since the windows installation overwrote it with the windows bootloader.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Thanks for the fast answer!
Have a nice day, good sir! :)

---

### Post by strask on 2012-04-18
> **deemasaurus said:**
> here are the results 

Number    Start             End            Size         Type         File system    Flags
 1                 32.3kB    65.8MB    65.8MB     primary   fat16                     diag
 2                 66.1MB   13.4GB    13.4GB     primary   ext4
 3                 13.4GB    500GB      487GB       primary
 4                 500GB      500GB     1065kB     primary     ntfs                       boot, hidden

Do you (I hope) have more than one hard disk?

What this is showing us is 

1) A tiny dos-formatted partition likely with some (not likely useful) recovery tools on it.
2) A 13-gb linux partition.
3) A 487-gb partition *without a filesystem*.
4) Another tiny windows partition that is not likely useful.

It's #3 that worries me, as that looks a lot like where I would expect your main windows ntfs partition to be, but it's showing up without a filesystem on it.

If at all possible, go get and run the boot info script linked above, it looks like that will give us a ton more info.

---

### Post by jadtech on 2012-04-18
hmm seems just like microsoft , try to install a decent OS on your hard drive and it packs up it os and filing system and goes home, i'll bet the recovery CD has took off too..

---

### Post by deemasaurus on 2012-04-18
> **strask said:**
> Do you (I hope) have more than one hard disk?

What this is showing us is 

1) A tiny dos-formatted partition likely with some (not likely useful) recovery tools on it.
2) A 13-gb linux partition.
3) A 487-gb partition *without a filesystem*.
4) Another tiny windows partition that is not likely useful.

It's #3 that worries me, as that looks a lot like where I would expect your main windows ntfs partition to be, but it's showing up without a filesystem on it.

If at all possible, go get and run the boot info script linked above, it looks like that will give us a ton more info.

lol oh man #3 is scaring me, im at work right now during my next break ill post up the info that the script gave me

---

### Post by deemasaurus on 2012-04-18
i tried running the bootinfoscript but nothing happens when i click run in teminal or just run

---

### Post by lisanels47 on 2012-04-18
There's a bootable linux ISO (if I could find it now, I'd tell you where it is...), that has a "Boot Repair" utility..  

You can create a bootable USB flash with Ubuntu 11.10 on it, and then add the Boot Repair utility.  It works really well, and can fix broken boot records.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by strask on 2012-04-18
> **deemasaurus said:**
> i tried running the bootinfoscript but nothing happens when i click run in teminal or just run

You need to use sudu to run it so that it has root permissions. 

1) Boot ubuntu from the install cd, click "try ubuntu" rather than install.
2) Download the bootinfoscript. Decompress the .gz and unpack the .tar
3) Open a terminal to get a bash prompt
4) cd to the directory where the script is.
5) type ```
sudu ./bootinfoscript
```
6) It should complete pretty quickly; once it is done look for a file called RESULTS.txt and paste the contents into the forums here for us.

---

### Post by al111 on 2012-04-19
Download and burn [Super Grub Disk]("http://www.supergrubdisk.org/")

Use Super Grub Disk to boot into Ubuntu-

To reinstall Grub2:

Open terminal (sda if boot partition):

```
sudo grub:install /dev/sda
```

Reboot

Fixed

---

### Post by Shazaam on 2012-04-19
> **al111 said:**
> Download and burn [Super Grub Disk]("http://www.supergrubdisk.org/")

Use Super Grub Disk to boot into Ubuntu-

To reinstall Grub2:

Open terminal (sda if boot partition):

```
sudo grub:install /dev/sda
```

Reboot

Fixed
BAD idea. If he has wiped Windows off of his drive any additional writing to it could reduce the chance that he could restore it using tools like testdisk.

---

### Post by al111 on 2012-04-19
I wouldn't necessarily call it a 'bad' idea, but an even better idea would be to boot into Ubuntu with the Super Grub Disk and just update grub:


@deemasaurus:

```
sudo update-grub2
```

---

### Post by deemasaurus on 2012-04-19
> **al111 said:**
> I wouldn't necessarily call it a 'bad' idea, but an even better idea would be to boot into Ubuntu with the Super Grub Disk and just update grub:


@deemasaurus:

```
sudo update-grub2
```

is it safe im a lil hesitant now

---

### Post by al111 on 2012-04-19
> **deemasaurus said:**
> is it safe im a lil hesitant now

I say yes, I dual-boot my laptop, and triple-boot my desktop...

I recall, everytime I installed a different linux, I'd have to update grub for windows to show...

If windows was left intact after installing linux, it should show and boot after updating grub-

Updating grub wouldn't do any harm-

```
sudo update-grub
```

or  

```
sudo update-grub2
```

---

### Post by darkod on 2012-04-19
> **al111 said:**
> Download and burn [Super Grub Disk]("http://www.supergrubdisk.org/")

Use Super Grub Disk to boot into Ubuntu-

To reinstall Grub2:

Open terminal (sda if boot partition):

```
sudo grub:install /dev/sda
```Reboot

Fixed

I would rather that people here are advised to use ubuntu tools. There is nothing Super Grub can do that the ubuntu live cd can not, when reinstalling grub is concerned. On top of that, with the ubuntu cd you are sure to get the same version of grub.

I have seen threads here with installation messed up by Super Grub.

Try again running the script as advised. It's not difficult, just make sure where you download it, and that you need to execute the command to run it from the same folder.

Post the results which will show if you have a recognizable win7 install at all.

---

### Post by deemasaurus on 2012-04-20
figured it out here are the results 

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    26,224,639    26,095,616  83 Linux
/dev/sda3          26,224,640   976,771,071   950,546,432  82 Linux swap / Solaris
/dev/sda4    *    976,771,072   976,773,151         2,080  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07DB-0105                              vfat       DellUtility
/dev/sda2        ca979460-54e6-4d23-a9b8-31c19de7577e   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ca979460-54e6-4d23-a9b8-31c19de7577e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
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
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=ca979460-54e6-4d23-a9b8-31c19de7577e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    echo    'Loading Linux 3.0.0-17-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=ca979460-54e6-4d23-a9b8-31c19de7577e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=ca979460-54e6-4d23-a9b8-31c19de7577e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    echo    'Loading Linux 3.0.0-17-generic ...'
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=ca979460-54e6-4d23-a9b8-31c19de7577e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ca979460-54e6-4d23-a9b8-31c19de7577e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ca979460-54e6-4d23-a9b8-31c19de7577e ro recovery nomodeset 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root ca979460-54e6-4d23-a9b8-31c19de7577e
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=ca979460-54e6-4d23-a9b8-31c19de7577e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=9ae83c29-2bc3-4398-a0ba-56d7a3aa62f9 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sda2   /media/Windows7_OS  ntfs-3g defaults,user,locale=en_US.utf8 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-17-generic               2
               =                boot/initrd.img-3.0.0-17-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-17-generic                  2
               =                boot/vmlinuz-3.0.0-17-generic-pae              1
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 38 3a  |........?....X8:|
00000020  00 00 00 00 80 00 80 00  1f 08 00 00 00 00 00 00  |................|
00000030  82 00 00 00 00 00 00 00  f3 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  8a 14 6c 9a dd e6 6c cb  |..........l...l.|
00000050  00 00 00 00 fa 31 c0 8e  d0 bc 00 7c fb 0e 1f 0e  |.....1.....|....|
00000060  07 66 60 88 16 00 7e c6  06 04 7e 1e b4 48 be 04  |.f`...~...~..H..|
00000070  7e cd 13 b0 50 0f 82 71  01 83 2e 13 04 14 a1 13  |~...P..q........|
00000080  04 c1 e0 06 a3 02 7e 83  ec 0e 6a 10 89 e5 be ed  |......~...j.....|
00000090  7d b9 05 00 66 31 db e8  f7 00 ff 36 02 7e 07 8c  |}...f1.....6.~..|
000000a0  46 06 8c 5e 04 e8 08 00  83 c4 10 66 61 06 1e cb  |F..^.......fa...|
000000b0  66 60 57 66 ff 36 14 7e  66 8f 46 08 66 ff 36 18  |f`Wf.6.~f.F.f.6.|
000000c0  7e 66 8f 46 0c 66 8b 45  10 66 40 66 29 46 08 66  |~f.F.f.E.f@f)F.f|
000000d0  19 5e 0c 8b 45 14 89 46  02 b4 42 8a 16 00 7e 89  |.^..E..F..B...~.|
000000e0  ee cd 13 b0 52 0f 82 01  01 31 c0 ba 04 04 be 4c  |....R....1.....L|
000000f0  7c 88 9f 42 7e fe c3 75  f8 8a 8f 42 7e 02 04 e8  ||..B~..u...B~...|
00000100  7e 00 46 fe ce 75 04 29  d6 88 d6 fe c3 75 ea 31  |~.F..u.).....u.1|
00000110  c0 89 c3 8b 56 02 c1 e2  09 8b 76 04 fe c3 8a 8f  |....V.....v.....|
00000120  42 7e e8 5b 00 00 e9 30  ed 89 cf 8a 8d 42 7e 26  |B~.[...0.....B~&|
00000130  30 0c 46 4a 75 e6 5f 66  8b 4d 18 66 0f b7 56 04  |0.FJu._f.M.f..V.|
00000140  81 f9 ff 7f b0 53 0f 87  a0 00 66 ff 75 1c 66 31  |.....S....f.u.f1|
00000150  c0 66 89 45 1c 66 f7 d0  26 67 32 02 66 42 b3 08  |.f.E.f..&g2.fB..|
00000160  66 d1 e8 73 06 66 35 20  83 b8 ed fe cb 75 f1 e2  |f..s.f5 .....u..|
00000170  e7 66 f7 d0 66 5b 66 39  d8 b0 43 75 6d 66 61 c3  |.f..f[f9..Cumfa.|
00000180  00 c8 89 c7 8a ad 42 7e  88 af 42 7e 88 8d 42 7e  |......B~..B~..B~|
00000190  c3 66 60 bf 42 7f 8c 4e  06 89 7e 04 66 89 d8 40  |.f`.B..N..~.f..@|
000001a0  89 45 14 66 a1 38 7c 66  89 45 10 b8 20 00 e8 ff  |.E.f.8|f.E.. ...|
000001b0  fe 8b 7e 04 8b 55 18 fc  60 f3 a6 83 7d fe 5c 74  |..~..U..`...}.\t|
000001c0  0d e3 0d 61 01 c7 29 c2  77 ee b0 4e eb 1c 41 4e  |...a..).w..N..AN|
000001d0  5f 83 c4 0e 60 89 fe bf  22 7e 59 57 89 c1 f3 a4  |_...`..."~YW....|
000001e0  61 e3 02 eb c9 59 57 66  61 c3 f4 eb fd 5c 62 6f  |a....YWfa....\bo|
000001f0  6f 74 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |ot............U.|
00000200


=============================== StdErr Messages: ===============================

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

---

### Post by strask on 2012-04-20
> **deemasaurus said:**
> 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    26,224,639    26,095,616  83 Linux
/dev/sda3          26,224,640   976,771,071   950,546,432  82 Linux swap / Solaris
/dev/sda4    *    976,771,072   976,773,151         2,080  17 Hidden NTFS / HPFS


That's not at all good. Looks like you somehow ended up using your main windows partition as swap space.

If you have a lot of memory maybe the swap space hasn't been used, however, so it's possible the data is still there... I don't know what kind of tools exist or would be required to recover it though.

---

### Post by darkod on 2012-04-20
You should be able to recover it with testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Run it from live mode. DO NOT boot your hdd, save your windows partition first.

Be careful with testdisk, it can save the partition but it can also destroy it. Note the warning NOT to write the partition table until you can see your windows ntfs partition detected.

You will probably have to do it with the deeper scan.

---

### Post by deemasaurus on 2012-04-20
how do i save my partion?

---

### Post by darkod on 2012-04-21
Are you asking about the exact instructions?

That link I gave you has the details how to do it.

Basically, testdisk will scan your hdd for all partitions it can detect even if some of them were recently deleted. Then you will have to select which one you want to recover, and change the letter in front of it from L into * or P. For windows partition, it probably should be *.

Then you tell testdisk to write a new partition table and that should recover the partition.

If you feel unsure get a friend to help you. It is very difficult to tell you what to do exactly with testdisk like this because it depends on what you see on the screen.

---

### Post by deemasaurus on 2012-04-24
I think i found the partion with testdisk but when i hit P to add to the list of partions so i could save it. It gave me an error message saying it was damaged

---

### Post by strask on 2012-04-24
Are you sure that P is the right thing? In his last post, Darkod suggested that you would use * instead of P.

I don't know, as I've never used testdisk. I'll go take a look at the docs to see if I get any ideas for you though.

---

### Post by darkod on 2012-04-24
If I remember correctly you use P to display the content (files). But it's a good idea to try and list the files to make sure it's the correct partition and it can be read.

If there is another similar partition in the deep search, try listing the files on that one and see if it works. Testdisk can find a few similar partitions and you only need to recover one.

Otherwise, when you are ready to try and recover it, you use the left and right arrows to change the letter in front of the partition. Most probably the letter will be L which means deleted (there is explanation of the codes at the bottom). You will have to use the left and right arrows to change the L into *. The * means primary bootable partition and your windows is the primary with the boot flag on it. So, you will need to change to *.

After that write the partition table but only after you are sure you have all partitions listed as you want them.

EDIT: There is a difference between hitting P and using the arrows to change the "code" for the partition into P. As I said above, I think P is for listing files and if it says it's damaged, it means you are trying on a wrong partition, or that it can't recover it.
Changing the code to P is a different thing.

---

### Post by ph4nt0m117 on 2012-04-24
> **deemasaurus said:**
> Hey guys,

I have a Dell XPS 17 laptop almost a year ago a dual booted ubuntu 10.4 using Wubi on my windows 7 machine. Everything was A ok and over time for some reason I stopped using Ubuntu (bad idea). Recently I decided to boot it up because windows was pissing me off again (original reason I dual booted) so i went to update ubuntu to 11.04 but it wasn't working so i bought a linux magazine that had a linux cd and installed that way. I saw the option to replace windows I choose no, left the house came back and everything was fine i rebooted my system and now when I boot I don't see an option to boot my windows. Any ideas on what could have happened?

Hold F8?  :|

---

### Post by strask on 2012-04-24
> **ph4nt0m117 said:**
> Hold F8?  :|
Looks like *someone* forgot to scroll down and read the rest of the thread... :shock:

---

### Post by darkod on 2012-04-24
Here is the relevant screenshot from the testdisk manual attached after the deeper search.

Notice at the bottom, it says * is primary bootable, P - primary, L - logical, D - deleted.
It also says use left/right arrows to change partition characteristics. That is the first letter in the list of partitions.
Under that it says P: list files. You use the P key to list files on the selected partition.

So, what you will need to do, list the files on the partition you think is correct, if that works use the left/right to change its letter from D into *.

Take a good look at the partitions list, the three numbers for start and end are cylinder/head/sector. Look at the cylinders and see if the start/end match more or less, where one partition ends the next should continue, etc.

After you are sure it looks good to you, hit Enter to proceed. Write the table and that's it.

---

### Post by BruceHayter on 2012-04-24
Could this be a problem with the 11.04 release I have been searching and there seem to be a lot of threads related to this problem. I like to blame ms for the problems, but nothing seems to be wrong with my win7 and the problem does not exist when using Ubuntu10.10.I have tried many things like updating BIOS, reformatting clean installs on different machines and the only common core seems to be 11.04. Fixing the boot seems to exacerbate the problem.

---

### Post by darkod on 2012-04-24
> **BruceHayter said:**
> Could this be a problem with the 11.04 release I have been searching and there seem to be a lot of threads related to this problem. I like to blame ms for the problems, but nothing seems to be wrong with my win7 and the problem does not exist when using Ubuntu10.10.I have tried many things like updating BIOS, reformatting clean installs on different machines and the only common core seems to be 11.04. Fixing the boot seems to exacerbate the problem.

I don't know how you view the problem, but this is not a boot problem. From data posted it seems the win7 partition was changed into a swap partition, whether by the user or some unexplained situation.
We are trying to recover it as ntfs at which point I expect it to work fine. Right now, the issue is there is no windows ntfs partition, so obviously nothing to dual boot.

---

### Post by strask on 2012-04-25
> **deemasaurus said:**
> I think i found the partion with testdisk but when i hit P to add to the list of partions so i could save it. It gave me an error message saying it was damaged
deemasaurus -- any further update? Success I hope?

---

### Post by deemasaurus on 2012-04-25
i dont want to pick the wrong one this is what i see [http://s13.postimage.org/kf7exdpdz/Screenshot_1.png](http://s13.postimage.org/kf7exdpdz/Screenshot_1.png)

---

### Post by darkod on 2012-04-25
Unfortunately I don't see a recoverable NTFS partition there.

I am not sure if fixparts can help, if this is some small stupid error in the partition table. In lots of cases it can help fix errors in the partition table.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by deemasaurus on 2012-04-25
> **darkod said:**
> Unfortunately I don't see a recoverable NTFS partition there.

I am not sure if fixparts can help, if this is some small stupid error in the partition table. In lots of cases it can help fix errors in the partition table.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Aww man im going to try this when i get home, thanks for all your help so far!

---

### Post by deemasaurus on 2012-04-26
im still a noob with ubuntu so the intructions are really confusing for me and idk if it makes it difference but i was apparently on 11.10 and not 11.04

---

### Post by darkod on 2012-04-26
> **deemasaurus said:**
> im still a noob with ubuntu so the intructions are really confusing for me and idk if it makes it difference but i was apparently on 11.10 and not 11.04

From live mode just download the .deb file, either 32bit or 64bit depending on the ubuntu version you are running in live mode. Right click on the .deb file and install it.

Then simply launch it in terminal with:
sudo fixparts /dev/sda

If it finds errors it can repair, it will usually ask you if you want to repair them. I haven't used the program myself so don't know too many details.

---

### Post by deemasaurus on 2012-04-27
anyone else have any ideas?

---

