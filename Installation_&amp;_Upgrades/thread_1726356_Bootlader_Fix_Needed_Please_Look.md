---
title: "Bootlader Fix Needed Please Look"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by hepyack on 2011-04-11
hi i installed ubuntu and when i start it just load from ubuntu i cant start any os. here is my info.

my fdisk -l result
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1876    15066112   27  Unknown
/dev/sda2            1876       29505   221923744+   7  HPFS/NTFS
/dev/sda3           29505       48642   153719809    f  W95 Ext'd (LBA)
/dev/sda5           48246       48642     3176448   82  Linux swap / Solaris
/dev/sda6           39073       48245    73679872   83  Linux
/dev/sda7           29505       39073    76855296   83  Linux

```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 745447856 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 745447544 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 745447544 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    30,134,271    30,132,224  27 Hidden HPFS/NTFS
/dev/sda2          30,134,272   473,981,760   443,847,489   7 HPFS/NTFS
/dev/sda3         473,982,974   781,422,591   307,439,618   f W95 Ext d (LBA)
/dev/sda5         775,069,696   781,422,591     6,352,896  82 Linux swap / Solaris
/dev/sda6         627,695,616   775,055,359   147,359,744  83 Linux
/dev/sda7         473,982,976   627,693,567   153,710,592  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b6910cc1-46f3-4d82-86d8-721ca7e19320   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        1c31a17d-c708-4871-b22a-95c085b003dd   swap                                     
/dev/sda6        af0db2ef-ec9e-4047-8d85-2987913efdb2   ext4                                     
/dev/sda7        a30417d6-cb1d-4ffe-9423-245055d3b097   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# root        (hd0,2)
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
# kopt=root=UUID=af0db2ef-ec9e-4047-8d85-2987913efdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=af0db2ef-ec9e-4047-8d85-2987913efdb2

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        af0db2ef-ec9e-4047-8d85-2987913efdb2
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=af0db2ef-ec9e-4047-8d85-2987913efdb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        af0db2ef-ec9e-4047-8d85-2987913efdb2
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=af0db2ef-ec9e-4047-8d85-2987913efdb2 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Chainload into GRUB 2
root        af0db2ef-ec9e-4047-8d85-2987913efdb2
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        af0db2ef-ec9e-4047-8d85-2987913efdb2
kernel        /boot/memtest86+.bin


title Vista
rootnoverify (hd0,2)
chainloader +1
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set af0db2ef-ec9e-4047-8d85-2987913efdb2
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set af0db2ef-ec9e-4047-8d85-2987913efdb2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set af0db2ef-ec9e-4047-8d85-2987913efdb2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=af0db2ef-ec9e-4047-8d85-2987913efdb2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set af0db2ef-ec9e-4047-8d85-2987913efdb2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=af0db2ef-ec9e-4047-8d85-2987913efdb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set af0db2ef-ec9e-4047-8d85-2987913efdb2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set af0db2ef-ec9e-4047-8d85-2987913efdb2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=af0db2ef-ec9e-4047-8d85-2987913efdb2 /               ext4    errors=remount-ro 0       1
/dev/sda7       /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 381.6GB: boot/grub/core.img
 351.6GB: boot/grub/grub.cfg
 351.6GB: boot/grub/menu.lst
 381.6GB: boot/grub/stage2
 381.6GB: boot/initrd.img-2.6.32-21-generic
 321.5GB: boot/vmlinuz-2.6.32-21-generic
 381.6GB: initrd.img
 321.5GB: vmlinuz
```

---

### Post by hepyack on 2011-04-11
still waitin

---

### Post by coffeecat on 2011-04-11
You only have one bootable OS.

The fact that you have an entry for Vista in your legacy grub menu.lst (except that (hd0,2) in the rootnoverify (hd0,2)line is wrong) and that fdisk shows NTFS for sda2 suggest that you had Vista on that machine at one time.

However, this part of your boot script output:

```

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 745447856 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

```... tells us that something has gone seriously wrong with both sda1 and sda2. Elsewhere in your boot script sda1 appears as "Hidden HPFS/NTFS" which makes me think it was once your hidden recovery partition. But now it appears as ext4 with a bad superblock. Partition sda2, which I suspect was once your Windows C: partition shows no evidence of Windows being there at all and it is contaminated with grub code, as are most of the other partitions including, bizarrely, your extended partition.

How did you get to this position? It doesn't look good.

---

### Post by hepyack on 2011-04-12
i dont know mate i just tried to install ubuntu then i did. but i lost windows this time. what can i do? if i recover windows; ubuntu will be lost?

---

### Post by coffeecat on 2011-04-12
> **hepyack said:**
> i dont know mate i just tried to install ubuntu then i did. but i lost windows this time. what can i do? if i recover windows; ubuntu will be lost?

Not necessarily. But how will you recover Windows? It looks as though your original recovery partition is gone. Do you have install or restore DVDs? If you have a Microsoft install DVD it is possible to install Vista without losing Ubuntu, although this would need a bit of thought in your situation. If you are relying on OEM maunfacturer's restore discs, then you may very well lose Ubuntu. Some are more flexible than others, but most try to restore you to the way the machine left the factory.

---

### Post by hepyack on 2011-04-12
i have restore discs but its my last choice. dont you think i can save windows without using recover discs?

---

### Post by sikander3786 on 2011-04-12
> **hepyack said:**
> i have restore discs but its my last choice. dont you think i can save windows without using recover discs?
Hi. ***Coffeecat*** seems away at the moment so I thought I would jump in here.

It is good to know that you've got the recovery discs. I don't think there is any other choice besides using your recovery disc to restore Windows. Your recovery partition doesn't seem intact and you might not be able to use it now.

As a simple solution, I would suggest to restore Windows from discs then run the bootinfoscript once more and let us see the output. Then we will try to guide you step-by-step through the installation of Ubuntu.

With Ubuntu, there is not much to lose as you can re-install it any time later unless there is some important data on your HDD.

---

### Post by oldfred on 2011-04-12
I have never seen grub installed to the swap partition, not sure if that is an issue. The grub installed to the extended is not an issue as that area is not used for anything anyway.

You can try using test disk to recover the windows boot sector on sda2. Windows cannot have grub in its boot sector as it has to have windows code there. But you may have to run chkdsk on both sda1 & sda2 for windows to even see the partitions.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot 

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

