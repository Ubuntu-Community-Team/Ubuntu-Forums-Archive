---
title: "Win7/Ubuntu 64-bit EFI - Ubuntu Won't Boot &amp; I Have to Go Through BIOS to change Boot"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by vm_boy on 2011-09-01
I have a 64-bit UEFI machine with Windows 7 currently installed. I'm trying to install Ubuntu 11.04.

My partitions are like so:
sda1 = Windows (100 GB) (ntfs)
sda2 = Linux partition (Installed)(60 GB) (ext4)
sda3 = EFI (don't know how it got to sda3, but it did) (100 MB) (fat)
sda4 = Swap (4GB) (swap)
sda5 = Programs (~336 GB) (ntfs)

sdb = Documents (NTFS) (1.5TB) (ntfs)

sdc = External HDD (1.0 TB) (ntfs)

So last night I got my computer backed up using Window's backup/restore program.  I also copied the EFI partition to the external drive for later use.  I then installed Ubuntu from a USB drive by mounting / at sda2 and then setting sda3 as an "EFI partition" so that grub would install there.  After it installed, it gave me the option to keep working or reboot.  I decided to keep working and I copied the Windows boot files back into the EFI partition.

I then restarted and it booted right into Ubuntu.  I then started Update Manager and installed all of the updates.  I restarted and it hung while shutting down.  So I hit the "reset" button and it restarted.  Upon restart, I got the Ubuntu splash screen (not even the GRUB menu), and then it gave me a long script of stuff, hung up and wouldn't continue on to Ubuntu.  I tried this a couple of times and finally decided to give up on that.

Next, I returned to the BIOS and changed the boot priority so that "Windows Boot Manager" would come first and "ubuntu" would come second.  I then restarted and it booted right into Windows (so copying the boot files into the EFI partition actually worked!!!).

So what should I do now?  It seems like I have a GRUB issue trying to use UEFI/EFI/GUID/GPT.  What I would like to have happen upon boot up is for GRUB to come up and give me the option of Ubuntu or Windows 7 (from what I've read online, I think this requires a chainloader).

I feel like I'm so close now that Win7 and Ubuntu are both installed and I can nearly boot into both of them.  I have the computer backed up with several restore points along the way so whatever I attempt, I can always restore back to the point before it was messed up so I'm willing to try several options.

---

### Post by srs5694 on 2011-09-01
> **vm_boy said:**
> I have a 64-bit UEFI machine with Windows 7 currently installed. I'm trying to install Ubuntu 11.04.

My partitions are like so:
sda1 = Windows (100 GB) (ntfs)
sda2 = Linux partition (Installed)(60 GB) (ext4)
sda3 = EFI (don't know how it got to sda3, but it did) (100 MB) (fat)
sda4 = Swap (4GB) (swap)
sda5 = Programs (~336 GB) (ntfs)


From your partition layout, this sounds like a GPT setup with UEFI-style booting.

> I then restarted and it booted right into Ubuntu.  I then started Update Manager and installed all of the updates.  I restarted and it hung while shutting down.  So I hit the "reset" button and it restarted.  Upon restart, I got the Ubuntu splash screen (not even the GRUB menu), and then it gave me a long script of stuff, hung up and wouldn't continue on to Ubuntu.  I tried this a couple of times and finally decided to give up on that.

There have been several reports that Ubuntu's update manager tries to replace grub-efi (the EFI/UEFI-enabled version of GRUB) with grub-pc (the BIOS version of GRUB). If this is what happened to you, it could be that critical GRUB files have been replaced with BIOS versions, thus rendering the system unbootable. I'll proceed under the assumption that this is what happened, but if that assumption is incorrect, you may need to do something entirely different to fix the problem. There are several ways to recover from an improper replacement of grub-efi with grub-pc (see below).

> So what should I do now?  It seems like I have a GRUB issue trying to use UEFI/EFI/GUID/GPT.  What I would like to have happen upon boot up is for GRUB to come up and give me the option of Ubuntu or Windows 7 (from what I've read online, I think this requires a chainloader).

In theory, GRUB in EFI mode can chainload to the Windows EFI boot loader. Another option is to install [rEFIt,](http://refit.sourceforge.net) which is an EFI chain-loader. (It can't load either Linux or Windows directly.) You'd set rEFIt as the default boot loader, and it then shows a GUI or text-mode menu displaying other boot loader options. (The GUI menu is messed up on some UEFI-based systems, unfortunately.) One caveat is that you probably need a pure 64-bit version of rEFIt. Most binaries are mixed-mode 32-/64-bit and won't work on UEFI-based PCs. The Ubuntu refit package includes a 64-bit binary (/usr/lib/refit/x64/refit.efi), which you can copy to its own directory in the EFI System Partition (ESP) along with the contents of /usr/lib/refit/refit.

> I feel like I'm so close now that Win7 and Ubuntu are both installed and I can nearly boot into both of them.  I have the computer backed up with several restore points along the way so whatever I attempt, I can always restore back to the point before it was messed up so I'm willing to try several options.

If you can restore Ubuntu to its state prior to running your system update, the simplest recovery procedure may be to do that. You can then run the update again, but be sure to deselect any GRUB "updates," since they're likely to break your ability to boot.

Another option is to start from the computer's current state and install a boot loader outside of the package system, or by booting the installer and using advanced dpkg options to manually install the relevant packages. The two most likely candidates are:


[list]
[*][GRUB 2,](https://help.ubuntu.com/community/UEFIBooting) which you can compile locally (presumably on another computer or using an emergency system with the relevant compilers installed) or install from the package system.
[*][ELILO,](http://elilo.sourceforge.net/) which you can install via binary or using the package system. ELILO cannot chainload to Windows, though, so if you use ELILO, you'll need to use rEFIt, too. Personally, I find that ELILO is more reliable than GRUB 2 on UEFI-based systems, but that could well vary from one computer to another. Note that ELILO works best with the kernel on the ESP, and your ESP is only 100 MB, which will fill up quickly if you want to have multiple kernel options.
[/list]

---

### Post by vm_boy on 2011-09-09
I finally got around to working on the computer and then around to posting an update...

I tried reinstalling Ubuntu 11.04 from the USB disk and then running through the steps on the GRUB2 website for UEFI booting.  I tried it before and after running updates, and neither way worked.  Also, if you just install Ubuntu, restart, and then restart again without installing any updates, I still get the same issue of Ubuntu not booting so I don't think it's an issue with the updates.

When I get time, I'll try some of the other options (ELILO and rEFIt), but I also just might wait until 11.10 comes out next month and see if they fix the issue in that version.  Until then, I can be happy just booting into Windows.

---

### Post by srs5694 on 2011-09-09
Could you please boot the installer to "try it now" mode and run the following command:

```

dmesg | grep EFI

```

If you get many lines of output like the following, then the installer is booted in EFI mode and will treat the computer as such:

```

[    0.000000] EFI: mem132: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] EFI: mem133: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] Kernel command line: BOOT_IMAGE=atapi0:\EFI\ELILO\bzImage-2.6.39 root=/dev/seeker/u1104  reboot=a,w ro
[    2.547087] fb0: EFI VGA frame buffer device
[    4.074484] EFI Variables Facility v0.08 2004-May-17
[   15.869853] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver

```

If you get little or no output, then the computer is booted in BIOS mode and it will probably install a BIOS version of GRUB from the start. This might require reconfiguring your firmware to boot in BIOS mode or manually installing GRUB or some other boot loader.

You can also learn more by running the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) which collects various diagnostic information. Unfortunately, most of it's geared toward BIOS booting, but it could still produce some useful clues in your case. Post the RESULTS.txt file that Boot Infor Script produces, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to preserve legibility.

---

### Post by vm_boy on 2011-09-13
I ran the dmesg... and got a bunch of lines.  Most or all had EFI within the lines.

I then ran the Boot Info Script and got the following Results.txt

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    220765388 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30510 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34   195,312,499   195,312,466 Data partition (Windows/Linux)
/dev/sda2     195,312,500   312,499,999   117,187,500 Data partition (Windows/Linux)
/dev/sda3     312,500,224   312,705,023       204,800 EFI System partition
/dev/sda4     312,705,024   312,967,167       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5     312,967,168   320,779,667     7,812,500 Swap partition (Linux)
/dev/sda6     320,779,668   976,773,134   655,993,467 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 2,930,277,167 2,930,277,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34 2,930,277,134 2,930,277,101 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F0A45DA1A45D6B5C                       ntfs       
/dev/sda2        c5efedb5-6216-474f-b308-e28773be339d   ext4       
/dev/sda3        CC07-522C                              vfat       
/dev/sda5        8adf77e5-38f1-47c8-86d5-2aab2607a336   swap       
/dev/sda6        7C8BC03557FFF3E5                       ntfs       Programs
/dev/sdb1        588D57D532A0149A                       ntfs       Documents
/dev/sdc1        0CDE-2D4A                              vfat       PENDRIVE
/dev/sdd1        CA54D88654D87723                       ntfs       Expansion Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/Programs          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###

insmod efi_gop
insmod efi_uga
insmod font

if loadfont ${prefix}/unicode.pf2
then
    insmod gfxterm
    set gfxmode=auto
    set gfxpayload=keep
    terminal_output gfxterm
fi

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

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root c5efedb5-6216-474f-b308-e28773be339d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root c5efedb5-6216-474f-b308-e28773be339d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    search --no-floppy --fs-uuid --set=root c5efedb5-6216-474f-b308-e28773be339d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c5efedb5-6216-474f-b308-e28773be339d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root c5efedb5-6216-474f-b308-e28773be339d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c5efedb5-6216-474f-b308-e28773be339d ro single 
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
    search --no-floppy --fs-uuid --set=root c5efedb5-6216-474f-b308-e28773be339d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root c5efedb5-6216-474f-b308-e28773be339d
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

menuentry "Windows x86_64 UEFI-GPT" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
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
UUID=c5efedb5-6216-474f-b308-e28773be339d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=CC07-522C  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda5 during installation
UUID=8adf77e5-38f1-47c8-86d5-2aab2607a336 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 133.272890091 = 143.100676096  boot/grub/grub.cfg                             1
  95.061944962 = 102.071986176  boot/initrd.img-2.6.38-8-generic               2
 133.265073776 = 143.092283392  boot/vmlinuz-2.6.38-8-generic                  1
  95.061944962 = 102.071986176  initrd.img                                     2
 133.265073776 = 143.092283392  vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

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

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by srs5694 on 2011-09-13
> **vm_boy said:**
> I ran the dmesg... and got a bunch of lines.  Most or all had EFI within the lines.

That means that the computer is booting whatever Linux version you were running (I'm guessing this was the Ubuntu installer) in EFI mode.

> I then ran the Boot Info Script and got the following Results.txt

```

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    220765388 of the same hard drive for core.img, but core.img can not be 
    found at this location.
```

This means that something has attempted to install the BIOS version of GRUB 2 to the disk, but some subsequent step has overwritten the GRUB 2 core.img data. Since you're now booting in UEFI mode, this BIOS version of GRUB is useless. AFAIK, leaving the boot loader in the MBR won't do any harm, aside from perhaps being a red herring in this or future troubleshooting attempts, so I don't recommend removing it.

> ```
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34   195,312,499   195,312,466 Data partition (Windows/Linux)
/dev/sda2     195,312,500   312,499,999   117,187,500 Data partition (Windows/Linux)
/dev/sda3     312,500,224   312,705,023       204,800 EFI System partition
/dev/sda4     312,705,024   312,967,167       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5     312,967,168   320,779,667     7,812,500 Swap partition (Linux)
/dev/sda6     320,779,668   976,773,134   655,993,467 Data partition (Windows/Linux)

```

This layout is peculiar but legal.

My recommendation at this time is to install or re-install an EFI-capable Linux boot loader, such as the EFI version of GRUB 2 or ELILO. If you use ELILO, you'll need to either use your firmware's option to select the boot OS or also install rEFIt to choose between OSes, since ELILO can't chainload to another EFI boot loader. My personal experience has been that ELILO is significantly more reliable on UEFI-based PCs than is GRUB 2; however, my sample size is limited, and the opposite is true on Macs.

If you want to gather more diagnostic data, you could look at what files exist on your ESP (/dev/sda3). That partition should have an EFI directory with subdirectories for each boot loader -- probably BOOT (the default boot loader), Microsoft (for Windows), and perhaps ubuntu (for Ubuntu's GRUB 2). This information won't change my recommendation, though -- whether or not the ubuntu directory and associated files are present, you need a new EFI-enabled boot loader, since whatever you've got there now isn't working.

---

### Post by vm_boy on 2011-09-22
I decided I would try to install rEFIt as you described in this thread ([HTML]http://ubuntuforums.org/showthread.php?p=11272267#post11272267[/HTML]).  I ended up reinstalling Ubuntu from the LiveUSB.  Once it restarted from there, I went to the Ubuntu Software Center and installed grub-efi-amd64.  I then rebooted and at that time, I ran through your install method for rEFIt.

It didn't seem to have much of an effect since I haven't seen anything that specifically says rEFIt or acts differently than what I'm used too.  It's possible I did something wrong.  The good news, however, is that I was able to boot into Ubuntu from a grub list.  I think I tried booting into the particular GRUB 2 from the BIOS (I have two GRUB2 options).  I think that if the GRUB2 option hangs, I can CTRL+ALT+DELETE twice in a row, go back to the BIOS, select the same GRUB2 option and it will give me the GRUB boot list.  It's not ideal, but it at least gets me into the hard drive version of Ubuntu rather than the LiveUSB version.

Since I did a bunch of stuff, I'm not sure how it might have changed the RESULTS from earlier, so I'm just going to repost here In case you see any significant changes from before.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    220765388 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34   195,312,499   195,312,466 Data partition (Windows/Linux)
/dev/sda2     195,312,500   312,499,999   117,187,500 Data partition (Windows/Linux)
/dev/sda3     312,500,224   312,705,023       204,800 EFI System partition
/dev/sda4     312,705,024   312,967,167       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5     312,967,168   320,779,667     7,812,500 Swap partition (Linux)
/dev/sda6     320,779,668   976,773,134   655,993,467 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 2,930,277,167 2,930,277,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34 2,930,277,134 2,930,277,101 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F0A45DA1A45D6B5C                       ntfs       
/dev/sda2        bce6cfcf-f84f-4384-9996-d2ad93d014e3   ext4       
/dev/sda3        CC07-522C                              vfat       
/dev/sda5        8adf77e5-38f1-47c8-86d5-2aab2607a336   swap       
/dev/sda6        7C8BC03557FFF3E5                       ntfs       Programs
/dev/sdb1        588D57D532A0149A                       ntfs       Documents
/dev/sdc1        CA54D88654D87723                       ntfs       Expansion Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /boot/efi                vfat       (rw)
/dev/sdc1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=bce6cfcf-f84f-4384-9996-d2ad93d014e3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=bce6cfcf-f84f-4384-9996-d2ad93d014e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bce6cfcf-f84f-4384-9996-d2ad93d014e3 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=bce6cfcf-f84f-4384-9996-d2ad93d014e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root bce6cfcf-f84f-4384-9996-d2ad93d014e3
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
UUID=bce6cfcf-f84f-4384-9996-d2ad93d014e3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=CC07-522C  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda5 during installation
UUID=8adf77e5-38f1-47c8-86d5-2aab2607a336 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 109.344820023 = 117.408106496  boot/grub/grub.cfg                             1
  95.891588211 = 102.962808832  boot/initrd.img-2.6.38-11-generic              2
  95.386682510 = 102.420670464  boot/initrd.img-2.6.38-8-generic               2
  95.468507767 = 102.508529664  boot/vmlinuz-2.6.38-11-generic                 1
 141.265073776 = 151.682217984  boot/vmlinuz-2.6.38-8-generic                  1
  95.891588211 = 102.962808832  initrd.img                                     2
  95.386682510 = 102.420670464  initrd.img.old                                 2
  95.468507767 = 102.508529664  vmlinuz                                        1
 141.265073776 = 151.682217984  vmlinuz.old                                    1


```

---

### Post by srs5694 on 2011-09-22
Unfortunately, the Boot Info Script provides very little information about EFI boot options. I recommend you look for some more EFI-specific information...

First, post the output of the following command:

```

find /boot/efi -name "*efi"

```

This will reveal what EFI boot loaders are installed in your ESP.

Next, when you boot Ubuntu *in EFI mode*, type the following command:

```

sudo efibootmgr -v

```

If the program isn't installed, install it by typing "sudo apt-get install efibootmgr". Post the results here. This command shows which boot loaders are registered with your EFI.

If you can't get Linux booted at all in EFI mode, running efibootmgr won't be possible -- or at least, it won't produce useful output. If so, the "find" command's output will have to do for this round of diagnostics.

---

### Post by vm_boy on 2011-09-24
The results to:

find /boot/efi -name "*efi"

are

```
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi
```The results to:

sudo efibootmgr -v

are

```
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0004,0005,0002,0003
Boot0000* Windows Boot Manager    HD(3,12a06000,32000,7399db94-6e27-4b01-ac8f-51665ba3b479)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu    HD(3,12a06000,32000,7399db94-6e27-4b01-ac8f-51665ba3b479)File(\EFI\ubuntu\grubx64.efi)
Boot0002* Hard Drive    BIOS(2,0,00)Seagate Desktop 0130.
Boot0003* CD/DVD Drive    BIOS(3,0,00)P5: HL-DT-ST DVDRAM GH24NS70  .
Boot0004* GRUB2    HD(3,12a06000,32000,7399db94-6e27-4b01-ac8f-51665ba3b479)File(\EFI\grub\grub.efi)
Boot0005* GRUB2    HD(1f,0,1,00000000-0000-0000-0000-000000000000)File(\EFI\grub\grub.efi)
```

---

### Post by srs5694 on 2011-09-24
> **vm_boy said:**
> The results to:

find /boot/efi -name "*efi"

are

```
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi
```The results to:

sudo efibootmgr -v

are

```
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0004,0005,0002,0003
Boot0000* Windows Boot Manager    HD(3,12a06000,32000,7399db94-6e27-4b01-ac8f-51665ba3b479)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu    HD(3,12a06000,32000,7399db94-6e27-4b01-ac8f-51665ba3b479)File(\EFI\ubuntu\grubx64.efi)
Boot0002* Hard Drive    BIOS(2,0,00)Seagate Desktop 0130.
Boot0003* CD/DVD Drive    BIOS(3,0,00)P5: HL-DT-ST DVDRAM GH24NS70  .
Boot0004* GRUB2    HD(3,12a06000,32000,7399db94-6e27-4b01-ac8f-51665ba3b479)File(\EFI\grub\grub.efi)
Boot0005* GRUB2    HD(1f,0,1,00000000-0000-0000-0000-000000000000)File(\EFI\grub\grub.efi)
```

First, try editing your /etc/grub.d/40_custom file and adding an entry like this:

```

menuentry "Windows 7" {
        set root='(hd0,gpt3)'
        chainloader EFI/Microsoft/Boot/bootmgfw.efi
}

```

Once you've done that, type "sudo update-grub" in Linux. This should add an entry for Windows to your GRUB configuration. If you're lucky, this will work, and you'll be able to select Windows from your GRUB configuration.

If that doesn't work, I'll need more information again. Please show me the contents of the ESP's EFI/BOOT directory ("ls /boot/efi/EFI/BOOT" if you're booted in Linux).

You might also want to peruse a new set of Web pages I've put up, [Managing EFI Boot Loaders for Linux.](http://www.rodsbooks.com/efi-bootloaders/index.html) I realize it's a lot to take in, but my thought, if my suggested GRUB 2 tweak doesn't work, is to get rEFIt working as a boot selector and either leave GRUB 2 for booting Linux only or (if GRUB 2 proves troublesome) replace it with ELILO. Thus, I recommend concentrating on the [EFI Boot Loader Installation](http://www.rodsbooks.com/efi-bootloaders/installation.html) and [Using rEFIt](http://www.rodsbooks.com/efi-bootloaders/refit.html) pages on my site.

---

### Post by vm_boy on 2011-09-24
I added the menu entry into 40_custom and restarted.  It still didn't give me an option to switch between Ubuntu and Windows.

I tried booting from both GRUB2 options and they both hung while trying to boot up.  Only the "ubuntu" option actually boots into Ubuntu, which tells me the grubx64.efi file works but \EFI\grub\grub.efi has some issues.

The results for 

ls /boot/efi/EFI/BOOT

are

```
bootx64.efi  icons  refit.conf  refit.efi  refit.vollabel
```

---

### Post by srs5694 on 2011-09-24
> **vm_boy said:**
> I added the menu entry into 40_custom and restarted.  It still didn't give me an option to switch between Ubuntu and Windows.

Did you type "sudo update-grub", too? If you're not sure, please try that.

> I tried booting from both GRUB2 options and they both hung while trying to boot up.  Only the "ubuntu" option actually boots into Ubuntu, which tells me the grubx64.efi file works but \EFI\grub\grub.efi has some issues.

To avoid confusion, you might want to create a tarball of EFI/grub and delete the original. That'll make it easy to restore if that becomes desirable in the future, but it'll be out of the way in the meantime.

> The results for 

ls /boot/efi/EFI/BOOT

are

```
bootx64.efi  icons  refit.conf  refit.efi  refit.vollabel
```

You could try adding the refit.efi file to the EFI's list of boot loaders as follows (typed in Linux):

```

sudo efibootmgr -c -l \\EFI\\BOOT\\refit.efi -L rEFIt -p 3

```

If you want to make it the default, you'll need to type "sudo efibootmgr" to find the list of registered boot loaders and their numbers. Given what you've posted, if you do this, rEFIt will probably be #6. In theory, you can then make rEFIt the default boot loader as follows:

```

sudo efibootmgr -o 6,1,0

```

This sets the order of boot loaders that the computer tries to use to 6 (rEFIt, if in fact that's the number it's given), followed by 1 (ubuntu, according to your earlier output), followed by 0 (Windows).

I don't recommend mucking with efibootmgr if you can get a Windows entry in GRUB to work, so try that first.

---

