---
title: "Dual Boot Ubuntu 9.10 with Windows 7"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by choosemyfate on 2010-02-09
I can't for the life of me get my GRUB whatever version I have to dual boot these.
I've spent over 3 weeks on it and then finally gave up.

But It would be really nice since I have so much software that is solely devoted to windows. Not to mention with my photography stuff it's just a whole lot easier to run everything through windows. But for the general census I do prefer Linux.

I'm running these two operating systems. (although I can't access my Windows 7 because of the boot menu problem) I think that's all that needs fixed but I'm not sure.

Ubuntu 9.10 ( I believe it's 64bit although the "about" doesn't specify)
Windows 7 64bit is installed.

Currently I only have access to Ubuntu.

Any other info you may need please ask. As well as how to get it to you.
Thanks.

---

### Post by raymondh on 2010-02-09
Hi and welcome.

What is the 'boot menu problem" you were referring to?

What GRUB are you using ... legacy or 2? Have you update GRUB?  In terminal (applications > accessories), type:

sudo update-grub

See if that helps.

Sorry for so many questions.  Let's see what you HD contains.  You'll need a liveCD for this.  [Instructions here]("http://ubuntuforums.org/showpost.php?p=8104352&postcount=1").  Paste the results.txt file back here.  As a favor, when you paste, highlight the results.txt file and wrap them in codes (click the # icon amongst the tools in your reply box).  That'll make it easier to read.

regards,

raymond

---

### Post by choosemyfate on 2010-02-09
> **raymondh said:**
> Hi and welcome.

What is the 'boot menu problem" you were referring to?

What GRUB are you using ... legacy or 2? Have you update GRUB?  In terminal (applications > accessories), type:

sudo update-grub

See if that helps.

Sorry for so many questions.  Let's see what you HD contains.  You'll need a liveCD for this.  [Instructions here]("http://ubuntuforums.org/showpost.php?p=8104352&postcount=1").  Paste the results.txt file back here.  As a favor, when you paste, highlight the results.txt file and wrap them in codes (click the # icon amongst the tools in your reply box).  That'll make it easier to read.

regards,

raymond

First I want to thank you for your time.
I already tried updating grub before along with thousands of other random things which is why I feared I would have to make yet another post. But thanks I tried it again. No dice.

Okay so here are the answers to all your questions to further help me.

I can boot Ubuntu 9.10 but not windows. It doesn't even appear in the GRUB boot menu. I'm Pretty sure I have GRUB 2 since I updated it like a million times already.
Windows is installed correctly and I can see the partition while booted in Ubuntu.

Here is the results from the results.txt file

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /IO.SYS 
                       /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a0a81d8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   488,263,544   283,466,925   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c5f75

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   476,375,444   476,375,382  83 Linux
/dev/sdb2         476,375,445   488,375,999    12,000,555  82 Linux swap / Solaris
/dev/sdb3         488,376,320   976,771,071   488,394,752   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f9c798a

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE52E5C952E5A70D                       ntfs       My Documents                  
/dev/sda2        725ACC5B5ACC1E2B                       ntfs       Windows and Program Files     
/dev/sdb1        db2bcf60-7823-4707-a674-2b3dd4ed0f1e   ext4                                     
/dev/sdb2        734000e3-ad60-4955-a37f-4c4854693cb6   swap                                     
/dev/sdb3        7C000C7B000C3EA0                       ntfs                                     
/dev/sdd1        4A65-E2BB                              vfat       MATTHEW250G                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/MATTHEW250G       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=db2bcf60-7823-4707-a674-2b3dd4ed0f1e

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        db2bcf60-7823-4707-a674-2b3dd4ed0f1e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set db2bcf60-7823-4707-a674-2b3dd4ed0f1e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=db2bcf60-7823-4707-a674-2b3dd4ed0f1e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=734000e3-ad60-4955-a37f-4c4854693cb6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by presence1960 on 2010-02-09
```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```
Here is a problem - sda2. It says boot sector type is XP, but you also have windows 7 on sdb3 with bootmgr & /boot/BCD missing from the windows 7 boot files. I assume you installed windows 7 after XP and your your windows bootfiles were combined with XP. You want to run chkdsk C: /f from the XP install disk. Boot from the XP install disk and when you reach the window with the option"Repair windows" choose that and you will get a command prompt. Type ```
chkdsk C: /f
``` You may have to run it twice. See if that fixes it. If it does not you can try booting your Windows 7 install DVD and choose Repair. Choose "fix problem that is keeping windows from booting" That is paraphrased but I think you get the meaning. it should be either the first or second in the list of options.

P.S. you do not have GRUB2. sda2 will never boot until you run chkdsk on it and windows7 will never boot because bootmgr & /boot/BCD are most likely on sda2. You have to fix that situation with sda2 before you can boot either windows.

---

### Post by choosemyfate on 2010-02-09
> **presence1960 said:**
> ```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```Here is a problem - sda2. It says boot sector type is XP, but you also have windows 7 on sdb3 with bootmgr & /boot/BCD missing from the windows 7 boot files. I assume you installed windows 7 after XP and your your windows bootfiles were combined with XP. You want to run chkdsk C: /f from the XP install disk. Boot from the XP install disk and when you reach the window with the option"Repair windows" choose that and you will get a command prompt. Type ```
chkdsk C: /f
``` You may have to run it twice. See if that fixes it. If it does not you can try booting your Windows 7 install DVD and choose Repair. Choose "fix problem that is keeping windows from booting" That is paraphrased but I think you get the meaning. it should be either the first or second in the list of options.

P.S. you do not have GRUB2. sda2 will never boot until you run chkdsk on it and windows7 will never boot because bootmgr & /boot/BCD are most likely on sda2. You have to fix that situation with sda2 before you can boot either windows.

Okay so you may want to disregard anything from the XP partition on the other hard drive I am simply using that drive to pull files from aka music/pictures etc. You probably only want to focus on the hard drive with Ubuntu and Windows 7

---

### Post by Mark Phelps on 2010-02-10
> **choosemyfate said:**
> Okay so you may want to disregard anything from the XP partition on the other hard drive I am simply using that drive to pull files from aka music/pictures etc. You probably only want to focus on the hard drive with Ubuntu and Windows 7

You can't ignore the XP drive because that is most likely the one with your Win7 boot loader files!  As you've already been told, you have to repair that before you can boot back into Win7.

---

### Post by choosemyfate on 2010-02-10
> **Mark Phelps said:**
> You can't ignore the XP drive because that is most likely the one with your Win7 boot loader files!  As you've already been told, you have to repair that before you can boot back into Win7.

That's impossible since I plugged the other drive in months after installing Windows 7 on the same hard drive I had ubuntu 9.10 on.

---

### Post by zach.detton on 2010-02-10
The reason Windows isn't showing is because after you've followed the maethod with the Live CD, you need to then boot to the Linux OS and run Update-Grub again. The Live CD meathod will only find what you have mounted at the time.

---

### Post by choosemyfate on 2010-02-11
> **zach.detton said:**
> The reason Windows isn't showing is because after you've followed the maethod with the Live CD, you need to then boot to the Linux OS and run Update-Grub again. The Live CD meathod will only find what you have mounted at the time.

I never used the LIVE cd method you are referring to.
I ran that script without it. 
Because on the page that had the script on it it did not say anything about running the LIVE cd. Besides I'm not sure what version or what not to use the live cd for or even the reasoning for doing so. Maybe I'll try repairing windows 7 like u ask. I no longer have a windows xp cd since i'm not planning on using xp. Maybe I should remove that drive from the computer so it doesn't confuse this process.

---

### Post by palenekim on 2010-02-11
Best bet when upgrading from Windows Vista or XP to Win 7 is to remember to completely wipe-out the hard drive prior to installing Win 7. You might want to back up any files you may need on an external hard drive or you could move those files to a flash drive if they are not too big. Microsoft Windows tends to be a tricky beast when ever a full OS install is concerned as an upgrade so wiping out your hard drive before the install is the safest bet (assuming you have the full proprietary software). There are tutorials online for doing this as well which I would recommend investigating prior to doing this.

---

### Post by presence1960 on 2010-02-11
> **zach.detton said:**
> The reason Windows isn't showing is because after you've followed the maethod with the Live CD, you need to then boot to the Linux OS and run Update-Grub again. The Live CD meathod will only find what you have mounted at the time.

Sudo update-grub will not detect any windows OSs because the XP partition is unmountable and the windows 7 boot files (bootmgr & /boot/BCD) are missing. update-grub looks for the presence of boot files in order to detect an OS. The OP has 2 choices: repair the XP partition by running chkdsk C: /f or using the windows 7 install DVD to add the boot files to his windows 7 installation.

If you need clarification look over the results of the boot info script that were posted earlier. If you need help interpreting that ask- someone will be glad to help you.

---

### Post by presence1960 on 2010-02-11
> **choosemyfate said:**
> That's impossible since I plugged the other drive in months after installing Windows 7 on the same hard drive I had ubuntu 9.10 on.

Well what happened to your boot files- they obviously are missing. Without them (bootmgr & /boot/BCD) windows 7 will never boot regardless of what bootloader you use including windows' bootloader. You need to repair that installation's boot files.

---

