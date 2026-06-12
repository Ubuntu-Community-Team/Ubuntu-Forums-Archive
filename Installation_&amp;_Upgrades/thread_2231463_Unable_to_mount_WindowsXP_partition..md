---
title: "Unable to mount WindowsXP partition."
date: 2014-06-25
forum: Installation &amp; Upgrades
---

### Post by john255 on 2014-06-25
**Now that WindowsXP isn't supported anymore I decided to give Ubuntu a try. I have Ubuntu 12.04 installed and I decided to keep my windows partition with the ability to boot from it. I'm totally lost at this point, and I'm trying to figure out how to access my XP partition, but each time I click on the partition I get the following message**: 

                                                                                    Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
                                                                                    Failed to mount '/dev/sda1': Input/output error
                                                                                    NTFS is either inconsistent, or there is a hardware fault, or it's a
                                                                                    SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
                                                                                    then reboot into Windows twice. The usage of the /f parameter is very
                                                                                    important! If the device is a SoftRAID/FakeRAID then first activate
                                                                                    it and mount a different device under the /dev/mapper/ directory, (e.g.
                                                                                    /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
                                                                                    for more details.

**I'm not able to boot up the Windows partition for some reason to run chkdisk /f. Each time I try it takes me back to the screen where I select which partition to boot from**.

**When I type "sudo fdisk -l" into the terminal I get the following**:

                                                                                    Disk /dev/sda: 640.1 GB, 640133946880 bytes
                                                                                    255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
                                                                                    Units = sectors of 1 * 512 = 512 bytes
                                                                                    Sector size (logical/physical): 512 bytes / 512 bytes
                                                                                    I/O size (minimum/optimal): 512 bytes / 512 bytes
                                                                                    Disk identifier: 0x99a499a4

                                                                                       Device Boot      Start         End      Blocks   Id  System
                                                                                    /dev/sda1   *          63  1146438454   573219196    7  HPFS/NTFS/exFAT
                                                                                    /dev/sda2      1146439678  1250260991    51910657    5  Extended
                                                                                    /dev/sda5      1146439680  1241876479    47718400   83  Linux
                                                                                    /dev/sda6      1241878528  1250260991     4191232   82  Linux swap / Solaris

                                                                                    Disk /dev/mapper/cryptswap1: 4291 MB, 4291821568 bytes
                                                                                    255 heads, 63 sectors/track, 521 cylinders, total 8382464 sectors
                                                                                    Units = sectors of 1 * 512 = 512 bytes
                                                                                    Sector size (logical/physical): 512 bytes / 512 bytes
                                                                                    I/O size (minimum/optimal): 512 bytes / 512 bytes
                                                                                    Disk identifier: 0xd832aaef

                                                                                    Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
[B]
When I type "sudo blkid" I get this:[/B]

                                                                                    /dev/sda1: UUID="8A00E48F00E48393" TYPE="ntfs" 
                                                                                    /dev/sda5: UUID="11ae9b52-b008-4ac0-ac87-52bc61c6dd38" TYPE="ext4" 
                                                                                    /dev/sr0: LABEL="Data disc (11 Jun 14)" TYPE="iso9660" 
                                                                                    /dev/mapper/cryptswap1: UUID="32f0a70a-d75c-4827-8d60-42e9b5550f54" TYPE="swap"

**I'm not sure what that tells me. It just seems like in every post concerning a similar problem this was valuable info. Any help would be greatly appreciated!**

---

### Post by yancek on 2014-06-25
Where do you click on the xp partition.  You might need to create a mount point and then mount it, have you done that?   You could start by running:  sudo os-prober in a terminal.  Watch the output to see if xp is detected.  If it is, run:  sudo update-grub.  If that doesn't help, go oneline and google 'bootinfoscript', go to the site, read the instructions then download and run the script.  It will produce more information which should help someone answer your question.  It will output a file called result.txt which you can post here.

---

### Post by john255 on 2014-06-25
> **yancek said:**
> Where do you click on the xp partition.  You might need to create a mount point and then mount it, have you done that?   You could start by running:  sudo os-prober in a terminal.  Watch the output to see if xp is detected.  If it is, run:  sudo update-grub.  If that doesn't help, go oneline and google 'bootinfoscript', go to the site, read the instructions then download and run the script.  It will produce more information which should help someone answer your question.  It will output a file called result.txt which you can post here.

**Thanks for the reply! I usually just click the home folder and click the 587 GB Filesystem under devices that I assume is the XP partition. I did the "sudo os-prober" and it detected XP. I then updated grub and got this message: **

Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

[B]When I try clicking the partition again by going through home folder -> devices, the same message comes up as before. Did I create a mount point by updating the grub?

Here's the results of my result.txt file:[/B]

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,146,438,454 1,146,438,392   7 NTFS / exFAT / HPFS
/dev/sda2       1,146,439,678 1,250,260,991   103,821,314   5 Extended
/dev/sda5       1,146,439,680 1,241,876,479    95,436,800  83 Linux
/dev/sda6       1,241,878,528 1,250,260,991     8,382,464  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 32f0a70a-d75c-4827-8d60-42e9b5550f54   swap       
/dev/sda1        8A00E48F00E48393                       ntfs       
/dev/sda5        11ae9b52-b008-4ac0-ac87-52bc61c6dd38   ext4       
/dev/sr0                                                iso9660    Data disc (11 Jun 14)

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Data disc (11 Jun 14) iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root 11ae9b52-b008-4ac0-ac87-52bc61c6dd38
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 11ae9b52-b008-4ac0-ac87-52bc61c6dd38
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
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
menuentry 'Ubuntu, with Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 11ae9b52-b008-4ac0-ac87-52bc61c6dd38
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=11ae9b52-b008-4ac0-ac87-52bc61c6dd38 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.11.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 11ae9b52-b008-4ac0-ac87-52bc61c6dd38
    echo    'Loading Linux 3.11.0-15-generic ...'
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=11ae9b52-b008-4ac0-ac87-52bc61c6dd38 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 11ae9b52-b008-4ac0-ac87-52bc61c6dd38
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 11ae9b52-b008-4ac0-ac87-52bc61c6dd38
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 8A00E48F00E48393
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
UUID=11ae9b52-b008-4ac0-ac87-52bc61c6dd38 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=3322d7d1-2a0d-4f5f-bbd3-eb9f43eb4b5a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.11.0-15-generic              1
               =                boot/vmlinuz-3.11.0-15-generic                 1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by Mark Phelps on 2014-06-25
IF you can't get into Windows, then a way to run chkdsk is to download the ISO of the Minitool Partition Wizard Boot CD, burn it to CD, boot from it -- and select the option to Check the partition (they will likely call it a "drive").

---

### Post by grahammechanical on 2014-06-25
I notice from the boot repair report that sda6 (swap) has the same mount failed message as sda1 (XP) and then there is this:

/dev/mapper/cryptswap1 none swap sw 0 0

Have you encrypted the swap partition? Is the Xp partition also encrypted or part of a RAID setup?

> [COLOR=#000000]it's a [/COLOR][COLOR=#000000]SoftRAID/FakeRAID hardware[/COLOR]

That is the message you get when trying to mount the partition. Did you install Ubuntu and during the process set up RAID or LVM and include the Windows partition in it?

Regards.

---

### Post by john255 on 2014-06-25
> **grahammechanical said:**
> I notice from the boot repair report that sda6 (swap) has the same mount failed message as sda1 (XP) and then there is this:

/dev/mapper/cryptswap1 none swap sw 0 0

Have you encrypted the swap partition? Is the Xp partition also encrypted or part of a RAID setup?



That is the message you get when trying to mount the partition. Did you install Ubuntu and during the process set up RAID or LVM and include the Windows partition in it?

Regards.

If I did it was on accident. Is there any way to check if that's what I did? And if I did end up doing that... what does that even mean?

---

### Post by mastablasta on 2014-06-26
i am not sure how to check it bu tif you encrypted it means you scrambled all files and locked them under a certain passcode.

---

### Post by yancek on 2014-06-26
> **Did I create a mount point by updating the grub?**

No.  Those commands were meant to create an entry in the grub.cfg menu file.  Did you try rebooting to see if you can now boot xp to run chkdsk?

---

### Post by john255 on 2014-06-26
> **yancek said:**
> No.  Those commands were meant to create an entry in the grub.cfg menu file.  Did you try rebooting to see if you can now boot xp to run chkdsk?

I tried to boot XP normally, in safe mode, and with the last working configuration and none of them worked. I found out that I did encrypt the partition, but I don't know if that matters? 

On the start up screen I also get the message: 

"*The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present*"

I did some research on that to see if it was linked to my problem and found this as a solution: [http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html](http://punygeek.blogspot.com/2012/10/ubuntu-1204-how-to-solve-disk-drive-for.html)

However, I'm worried about step: "*re-format swap partition with gparted as linux-swap*" Is that going to erase everything on my partition? I have 587 GB of data on there. Also, could the two problems be related?

---

### Post by mastablasta on 2014-06-27
/swap partition should be only a few GB in size (it's kind of like pagefile.sys in Windows) and is used for hibernation. if you made your Windows paritition into swap partition then you did it wrong. it doesn't seem like you did that.

your Linux swap partition is on /dev/sda6     

and the part the guide is askign you to format is  this one i believe /dev/mapper/cryptswap1: 4291 MB which is 4 GB in size. so htis is not your data.

if you dont' have any important stuff on Uubntu it might be easier to just reinstall it.

what i am not sure is how all these things are affected if one uses encryption. as i do not use it. it only causes issues and unless you have a laptop & move arround a lot or are paranoid abotu your data it maybe shouldnt' be used. it brings all sort of difficulties with it.

---

### Post by oldfred on 2014-06-27
If reinstalling only use Something Else. 
Ubuntu may say with an auto install that it will overwrite Ubuntu install, but overwrites entire hard drive.

 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You should run chkdsk first. If XP you should also have the original install CD and can use that.

Only if chkdsk does not work, testdisk can try a mft repair.
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

