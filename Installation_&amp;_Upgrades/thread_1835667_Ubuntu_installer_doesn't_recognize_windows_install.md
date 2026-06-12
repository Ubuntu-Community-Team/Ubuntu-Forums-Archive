---
title: "Ubuntu installer doesn't recognize windows installation"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by bJob on 2011-08-29
Hello everyone
yesterday I tried to dual boot windows and ubuntu.
But the ubuntu installer (windows was installed first) only shows 2 options earase hwole drive and install ubuntu or choose manualy (sorry but I forgot the English name for this thing) I clicked the second thing and the intaller only shows My 1tb hard drive as an unformated drive with no partitions.
Please help me.

Thanks.





Sorry for my crappy English.(I speak dutch)

---

### Post by garvinrick4 on 2011-08-29
Is it a basic drive or dynamic drive?

---

### Post by zeroseven0183 on 2011-08-29
Which version of Ubuntu are you trying to install? Please give us more information.

Here's the link to dual booting Ubuntu and Windows to guide you. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by bJob on 2011-08-30
These are my Hard drives specs

---

### Post by Mark Phelps on 2011-08-30
If you're running Win7, you could try the following:
1) Boot into Win7, use the Disk Management feature to shrink the Win7 OS partition to make some room for Ubuntu.
2) Reboot, but using the Ubuntu CD.

NOW, see if Ubuntu can see the unformatted space.

IF it can, you can install to that space and let the installer format it.  Just don't allow the installer to shrink your Windows install.

Also, BEFORE you do that, would be a good idea to boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 boot loader or restore the original MBR.

---

### Post by YesWeCan on 2011-08-30
Hi. If the Ubuntu installer sees no partitions on your Windows drive then something is obviously wrong. There are a few things that can cause this. For example, if your disk has a GPT header on it or if it has dmraid superblocks.

First, would you post the output of:
sudo sfdisk -luM

---

### Post by bJob on 2011-08-30
> **YesWeCan said:**
> Hi. If the Ubuntu installer sees no partitions on your Windows drive then something is obviously wrong. There are a few things that can cause this. For example, if your disk has a GPT header on it or if it has dmraid superblocks.

First, would you post the output of:
sudo sfdisk -luM

Here are the results

[COLOR=Lime]
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     1    100    100     102400    7  HPFS/NTFS
/dev/sda2       101  953866  953766  976656384    7  HPFS/NTFS
/dev/sda3         0      -      0          0    0  Empty
/dev/sda4         0      -      0          0    0  Empty

Disk /dev/sdb: 487 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdb1   *     0+  3820-  3821-   3911796    c  W95 FAT32 (LBA)
/dev/sdb2         0      -      0          0    0  Empty
/dev/sdb3         0      -      0          0    0  Empty
/dev/sdb4         0      -      0          0    0  Empty[/COLOR]

---

### Post by YesWeCan on 2011-08-30
Wow - really GREEN! :P

Yes, the issue is that your drive has a GPT format header on it and you need to remove it. Windows does not use it, it uses the MBR format and ignores the GPT header but the Ubuntu installer gets confused.

Run EXACTLY this command, copy & paste it. If you make a typo you could trash your Windows installation.

[COLOR="Navy"]sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda[/COLOR]

Then try the Ubuntu installer again.

---

### Post by srs5694 on 2011-08-30
> **bJob said:**
> Here are the results

[COLOR=Lime]
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.[/COLOR]

The green text makes that hard to read. For future reference, when posting output from text-mode programs, it's best to:


[list]
[*]Leave the color scheme alone.
[*]Start the text you've cut-and-pasted with a [noparse]```
[/noparse] tag and end it with a [noparse]
```[/noparse] tag. This preserves column alignment and improves legibility.
[/list]


[quote=YesWeCan]Yes, the issue is that your drive has a GPT format header on it and you  need to remove it. Windows does not use it, it uses the MBR format and  ignores the GPT header but the Ubuntu installer gets confused.

Run EXACTLY this command, copy & paste it. If you make a typo you could trash your Windows installation.

[COLOR=Navy]sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda[/COLOR]

Then try the Ubuntu installer again.[/quote]

YesWeCan's analysis is correct, but the command he recommends does only half the job. GPT includes, by design, both primary and backup data, the primary being at the end of the disk and the backup being at the end of the disk. The dd command that YesWeCan recommends only deletes the primary GPT header, leaving the backup GPT header in place. Under some circumstances, this can result in problems down the line, since some utilities do check for backup GPT data and it's conceivable that its presence will cause confusion.

There are several ways to deal with this, but the simplest and safest, AFAIK, is to run my [FixParts](http://www.rodsbooks.com/fixparts/) utility, which will delete both the primary and the backup GPT headers. Unfortunately, FixParts isn't yet included with Ubuntu, so you'll need to download it ([here's](http://www.rodsbooks.com/gdisk/download.html#obs) a download matrix for several distributions) or run it from an emergency disc such as [PartedMagic,](http://partedmagic.com/doku.php) which includes the tool.

---

### Post by bJob on 2011-08-30
so ubuntu is installed now but grub doesn't load and the computer boots automatically in to windows.

---

### Post by Hakunka-Matata on 2011-08-30
Please download [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/), run, and post resulting RESULTS.txt file in code tags.

---

### Post by YesWeCan on 2011-08-30
> **bJob said:**
> so ubuntu is installed now but grub doesn't load and the computer boots automatically in to windows.
Glad Ubuntu is installed now. The booting will probably be a different issue. Please post bootinfoscript output as Hakunka-Matata recommends.

And I agree with srs5694's post and how he has worded it. My personal judgement is that leaving the backup GPT header is very unlikely to cause you any problems but it obviously doesn't hurt to remove it with Fixparts and this tool may come in handy for other purposes in the future. :)

---

### Post by bJob on 2011-08-30
this are the results 
 ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
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
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2618598 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   976,863,231   976,656,384   7 NTFS / exFAT / HPFS
/dev/sda3         976,865,278 1,953,523,711   976,658,434   5 Extended
/dev/sda5         976,865,280 1,936,785,407   959,920,128  83 Linux
/dev/sda6       1,936,787,456 1,953,523,711    16,736,256  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4011 MB, 4011851776 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7835648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,823,654     7,823,592   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AEE8B8F0E8B8B843                       ntfs       Door systeem gereserveerd
/dev/sda2        1E70E59570E57445                       ntfs       
/dev/sda5        b600e037-9291-4ca5-9709-c5b93865e085   ext4       
/dev/sda6        0bbdc82c-9093-4da5-90a8-6f99f76d4efc   swap       
/dev/sdb1        17DF-4269                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b600e037-9291-4ca5-9709-c5b93865e085
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b600e037-9291-4ca5-9709-c5b93865e085
set locale_dir=($root)/boot/grub/locale
set lang=nl_BE
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
menuentry 'Ubuntu, met Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b600e037-9291-4ca5-9709-c5b93865e085
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b600e037-9291-4ca5-9709-c5b93865e085 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, met Linux 2.6.38-8-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b600e037-9291-4ca5-9709-c5b93865e085
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b600e037-9291-4ca5-9709-c5b93865e085 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b600e037-9291-4ca5-9709-c5b93865e085
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b600e037-9291-4ca5-9709-c5b93865e085
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root AEE8B8F0E8B8B843
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b600e037-9291-4ca5-9709-c5b93865e085 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0bbdc82c-9093-4da5-90a8-6f99f76d4efc none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 771.967761993 = 828.894072832  boot/grub/grub.cfg                             1
 467.610351562 = 502.092791808  boot/initrd.img-2.6.38-8-generic               2
 803.972354889 = 863.258742784  boot/vmlinuz-2.6.38-8-generic                  1
 467.610351562 = 502.092791808  initrd.img                                     2
 803.972354889 = 863.258742784  vmlinuz                                        1

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by srs5694 on 2011-08-30
It looks like GRUB (Linux's boot loader) wasn't installed on your system. There are several ways to correct this problem. One is to boot the Ubuntu installer in "live CD" mode and issue a grub-install command with certain parameters, but I don't recall precisely what those are, offhand. (Somebody may post that command.) Another option, and what I generally do, is to use the [Super GRUB 2 Disk](http://www.supergrubdisk.org/) to boot the computer. You'll see a series of options and you may need to try several of them until the utility finds your GRUB configuration files and boots the computer. Once Ubuntu is booted, you can start a Terminal window and type the following command:

```

sudo grub-install /dev/sda

```

This will install GRUB in the MBR of the disk. The next time you boot (with nothing in the optical drive), you should be greeted by a GRUB menu showing various boot options, including one for Windows and two for Ubuntu (judging by the Boot Info Script output).

---

### Post by Hakunka-Matata on 2011-08-30
Someone will probably post the commands in a short list of how to install Grub2 to the MBR of sda, which is what you want to do.  Actually, you can install Grub2 to the MBR of both sda and sdb, which will give you the option of booting from either drive and getting your grub menu to choose from.

I prefer to show you where to read the official instructions yourself, and you can better learn how to do it in future if necessary.  

Here it is: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by YesWeCan on 2011-08-30
At the risk of repeating what's been mentioned, I'd do this from live CD:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by bJob on 2011-08-31
Everything is okay now

Thanks to evryone

---

### Post by YesWeCan on 2011-08-31
You are welcome. Don't forget to mark the thread as solved in [COLOR=Red]Thread Tools[/COLOR].

---

### Post by vpharry on 2011-08-31
1. Use [iboot]("http://www.iboot.org/")  2 boot into ubuntu.

2. Change grub settings(i think u hav 2 change the grub2 timeout). [Heres]("http://sernaonubuntu.wikidot.com/changing-grub-settings")  an article on how to do it.

---

