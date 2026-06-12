---
title: "Ubuntu installed from USB, won't boot"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by rl1 on 2011-07-10
Hi all,

I've been trying in vain to install Ubuntu 11.04 onto a brand new home server, using a bootable USB (created on Windows 7), since there's no CD drive.

What I've been doing is booting from the USB stick, selecting install onto HD which takes me through the install process. The installation runs fine and prompts me at the end to restart the machine, which I do. It then tells me to remove install media and hit enter. Optimistically I wait, and alas each time I get the network boot screen (which is after the HD in the BIOS), which fails and takes me to the black screen & cursor (telling me to reboot). I've also removed network boot in BIOS which just does the above without the network step.

I've played with a few BIOS settings but no joy and tried reinstalling/formatting etc several times (10 or so..).

I've tried the boot info script and my results are below

Here's my specs:

2GB DDR2 RAM 800Mhz
Intel D410 atom board 1.66GHz
Nexus 430 value PSU
Internet via ethernet
Samsung Ecogreen 2TB - actually have 2 but tried disconnecting one in case that makes a difference. It didn't.

I know this isn't an uncommon problem but I've searched through all similar threads and nothing seems to have worked for me. Any help really really appreciated!

Thanks in advance

Results:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......U..9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1603242 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34         1,987         1,954 BIOS Boot partition
/dev/sda2           1,988 3,902,869,175 3,902,867,188 Data partition (Windows/Linux)
/dev/sda3   3,902,869,176 3,907,029,118     4,159,943 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,905,278     7,905,247   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        c91321e0-33f3-450e-ae9f-ec49bf4e9f4f   ext4       
/dev/sdb1        00AA-0180                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root c91321e0-33f3-450e-ae9f-ec49bf4e9f4f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root c91321e0-33f3-450e-ae9f-ec49bf4e9f4f
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root c91321e0-33f3-450e-ae9f-ec49bf4e9f4f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c91321e0-33f3-450e-ae9f-ec49bf4e9f4f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root c91321e0-33f3-450e-ae9f-ec49bf4e9f4f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c91321e0-33f3-450e-ae9f-ec49bf4e9f4f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root c91321e0-33f3-450e-ae9f-ec49bf4e9f4f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root c91321e0-33f3-450e-ae9f-ec49bf4e9f4f
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=c91321e0-33f3-450e-ae9f-ec49bf4e9f4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=962b57b6-051e-42c9-97c8-2cdb6652c3a1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1570.134981155 = 1685.919598592 boot/grub/core.img                             1
1570.134988785 = 1685.919606784 boot/grub/grub.cfg                             1
   0.689760208 = 0.740624384    boot/initrd.img-2.6.38-8-generic               2
1570.133253098 = 1685.917743104 boot/vmlinuz-2.6.38-8-generic                  1
   0.689760208 = 0.740624384    initrd.img                                     2
1570.133253098 = 1685.917743104 vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-07-10
Welcome to UF.

You appear to have a GUID partition table (or at least it's being flagged as having GUID data on the drive). This may be a problem and could complicate things.
The boot script also reports a BIOS boot partition in sda1 and, for some reason, your sda3 partition (which is a swap partition) is not mounting.

Has this hard drive been used in a different machine?
Does your system have a boot booster of some kind?

---

### Post by dabl on 2011-07-10
You have the boot flag set on /dev/sdb.  Try clearing that one, and set it on /dev/sda.

You can do that with Gparted from the Live session.

---

### Post by rl1 on 2011-07-10
Thanks both. 

I'm in gparted, both sda1 and 3 have red exclamation marks, is that a problem? 

I've removed the boot flag from the pen drive but not sure which to add it to on sda. Sda1 is bios grub, 2 is ext 4 and fills 1.8 tb. Sda3 is 1.98gb. 

Thanks a lot

---

### Post by oldfred on 2011-07-10
The error on the bios boot partition is probably not a problem as it is unformated, but it issue on swap probably is.

You should leave the boot flag on sdb. Each drive can have one.

Intel motherboards seem to usually have a BIOS that requires a boot flag. The definition of gpt does not specify a boot flag, so Intel does not follow spec and has to have a boot flag. Or it expects a windows system which requires a boot flag.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.
Many Intel BIOSes, though, have a bug that requires that at least one MBR partition be marked as bootable, so you'll need to use fdisk (not gdisk, parted, or GParted) to mark the 0xEE partition as bootable/active. Note this is an Intel-specific bug; 

With large drives I prefer to make smaller system partitions and larger /home or /data partitions so the part of the system most often used does not reequire the drive to search all over to load system files. Note that some of your system files are at the beginning of the drive & others at the end.

> 1570.134981155 = 1685.919598592 boot/grub/core.img                             1
1570.134988785 = 1685.919606784 boot/grub/grub.cfg                             1
   0.689760208 = 0.740624384    boot/initrd.img-2.6.38-8-generic               2
1570.133253098 = 1685.917743104 boot/vmlinuz-2.6.38-8-generic                  1
   0.689760208 = 0.740624384    initrd.img                                     2
1570.133253098 = 1685.917743104 vmlinuz                                        1



---

### Post by srs5694 on 2011-07-10
Since you've got an Intel board, my best guess is that you're running into a bug that's known to exist on some Intel BIOSes that prevents them from booting if there's no *MBR* partition that has an *MBR* "boot flag" set. Note the emphasis on *MBR*, though. Doing as dabl suggests and setting a "boot flag" on a /dev/sda partition using GParted will do no good, and could even cause problems, since GParted maps the "boot flag" on GPT disks to the partition type code for an EFI System Partition (ESP). Setting a partition to use this type code would not affect the protective MBR and so will do no good. Furthermore, the partition will then have the wrong GPT type code, which could confuse installers or other disk utilities in the future.

Instead, use *fdisk* to set the boot flag on the type-ee partition in the protective MBR. The interaction would look something like this:

```
$ **sudo fdisk /dev/sdc**

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Command (m for help): **p**

Disk /dev/sdc: 2038 MB, 2038431744 bytes
18 heads, 44 sectors/track, 5026 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     3981311     1990655+  ee  GPT

Command (m for help): **a**
Partition number (1-4): **1**

Command (m for help): **p**

Disk /dev/sdc: 2038 MB, 2038431744 bytes
18 heads, 44 sectors/track, 5026 cylinders, total 3981312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1     3981311     1990655+  ee  GPT

Command (m for help): **w**
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.

```

I did this on a USB flash drive (/dev/sdc), but you'd presumably do it on /dev/sda. I checked the partition table before and after making the change to verify that I was working on the right disk and to check that the boot flag was set. The "w" command causes fdisk to write its changes to disk. This is very important; if you don't use this command, the changes will stay in memory and do you no good.

One important caveat: libparted-based tools (GParted, parted, Palimpsest Disk Utility, etc.) have a tendency to rewrite the protective MBR whenever they do anything. Thus, you may need to repeat this fix after you use such tools.

Another option might be to convert from BIOS-style booting to UEFI-style booting. That would require more changes, though, and I'm not sure that your firmware supports this option. (Most recent Intel boards do, though.) OTOH, libparted-based tools' habitual rewriting of the protective MBR won't be a problem if you go this route. If you want advice on how to make this transition, post back.

---

### Post by oldfred on 2011-07-10
I just checked my gpt drive. Gparted does not like the bios-grub partition but my swap is normal.

---

### Post by srs5694 on 2011-07-10
> **oldfred said:**
> I just checked my gpt drive. Gparted does not like the bios-grub partition but my swap is normal.

GParted doesn't *recognize* the BIOS Boot Partition's *contents*, but that's both normal and unimportant. Your screen shot clearly shows that GParted does recognize the type code (that's what the "bios_grub flag" is.

---

### Post by rl1 on 2011-07-11
Adding the boot flag did the trick, thanks a lot all!

---

### Post by Raquen on 2011-11-08
I know this is kind of a n00b question but what are you using to boot to make these changes. I have been trying this with execute shell commands option from the Ubuntu server installer and I am unable to execute fdisk.

I just need to know what will work for making the changes to the mbr.

thanks!

---

