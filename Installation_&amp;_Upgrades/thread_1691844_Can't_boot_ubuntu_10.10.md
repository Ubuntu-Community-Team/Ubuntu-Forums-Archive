---
title: "Can't boot ubuntu 10.10"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by LePresident on 2011-02-20
Hello,   I decided last saturday I wanted to start learning backtrack 4 so I installed it on my laptop. Previously, I had both Tiny XP and Ubuntu 10.10.  However, right after installing backtrack I noticed I could boot both backtrack and xp but I couldn't get into ubuntu.  Each time I try to boot ubuntu I get the following message: &quot;Error 15: File not found.  Press any key to continue...&quot;  What happened?  How can I fix this issue?  Please, I would REALLY appreciate your help, since all of my work and school jobs are in ubuntu! :S

---

### Post by kansasnoob on 2011-02-20
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by LePresident on 2011-02-20
Here is the output... 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8ecd49b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,181,524   104,181,462   7 HPFS/NTFS
/dev/sda2         104,194,047   312,580,095   208,386,049   5 Extended
/dev/sda5         104,194,048   216,829,304   112,635,257  83 Linux
/dev/sda6         216,829,368   304,014,059    87,184,692  83 Linux
/dev/sda7         304,021,504   312,580,095     8,558,592  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8E4C73B24C7393A5                       ntfs                                     
/dev/sda6        e2dd783f-fba9-4bb9-9275-fb86a550ffe9   ext3                                     
/dev/sda7        fe7bff26-b39b-44c6-ac66-9a1695cc11cf   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=FO76V0 /Kernel=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=FO76V0-BAK

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e2dd783f-fba9-4bb9-9275-fb86a550ffe9

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=e2dd783f-fba9-4bb9-9275-fb86a550ffe9/boot/grub/splash.xpm.gz

title        BackTrack 4 R2, kernel 2.6.35.8
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro vga=0x317 
initrd        /boot/initrd.img-2.6.35.8
quiet

title        BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro  single
initrd        /boot/initrd.img-2.6.35.8

title        BackTrack 4 R2, memtest86+
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-25-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-22-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=fe7bff26-b39b-44c6-ac66-9a1695cc11cf none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/menu.lst
 128.7GB: boot/grub/stage2
 128.8GB: boot/initrd.img-2.6.35.8
 128.8GB: boot/vmlinuz-2.6.35.8
 128.8GB: initrd.img
 128.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory

```

---

### Post by kansasnoob on 2011-02-20
NOTE: I quickly had to change "XY" to "a5" in the first command. Sorry if you caught that before the edit.

I assume you ran the Boot Info Script using backtrack. Is that correct?

I can see that Ubuntu is, or should be, on sda5 so **[COLOR="Red"]only if 10.10 is known to use grub2[/COLOR]** I'd be tempted to try this:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

---

### Post by LePresident on 2011-02-20
Exactly, I used boot info script at backtrack.  Give me a break and I'll be back in a few minutes to try what you propose.

---

### Post by deconstrained on 2011-02-20
Bear in mind, grub2 does some automagic system configuration parsing, so if your /etc/fstab is improperly configured, it's G.I.G.O. If that's not the problem, then you could try [chrooting and rebuilding your Linux image](http://ubuntuforums.org/showpost.php?p=10475387&postcount=2).

---

### Post by LePresident on 2011-02-20
> **deconstrained said:**
> Bear in mind, grub2 does some automagic system configuration parsing, so if your /etc/fstab is improperly configured, it's G.I.G.O. If that's not the problem, then you could try [chrooting and rebuilding your Linux image]("http://ubuntuforums.org/showpost.php?p=10475387&postcount=2").

What did you mean? Is there any danger if I try kansasnoob's method?

---

### Post by deconstrained on 2011-02-20
> **LePresident said:**
> What did you mean? Is there any danger if I try kansasnoob's method?
No, just that grub will only work correctly if you've configured your /etc/fstab correctly. You can try his method, and I'd have advocated it too if it hadn't already been posted. Just make sure everything else is in order as well, because when a system won't boot, it's not always the fault of grub being improperly installed/configured.

Also, I only recommended rebuilding your initramfs because "file not found" can be indicative of a missing Linux image. It may not be worth your trouble; try to find/diagnose the problem by looking at the simpler stuff first.

---

### Post by LePresident on 2011-02-20
Cool! I tried what kansasnoob told me to do and now I got ubuntu 10.10 back!!.... but can't access to backtrack lol

Any idea? XD

---

### Post by kansasnoob on 2011-02-20
Run the Boot Info Script from Ubuntu now and post the new results.

I've been working with the developers to improve this:

[http://ubuntuforums.org/showthread.php?t=1676235](http://ubuntuforums.org/showthread.php?t=1676235)

Ultimately I need to install backtrack myself and do some testing :D

I need to know just what version of backtrack you're using so I can track what versions of gawk and mawk are being used:

[http://distrowatch.com/table.php?distribution=backtrack](http://distrowatch.com/table.php?distribution=backtrack)

It's not something I'll get done within hours, or even days .............. more likely months :(

I tend to think backtrack needs some major updating to keep up with the times.

---

### Post by LePresident on 2011-02-20
> **kansasnoob said:**
> Run the Boot Info Script from Ubuntu now and post the new results.

I've been working with the developers to improve this:

[http://ubuntuforums.org/showthread.php?t=1676235](http://ubuntuforums.org/showthread.php?t=1676235)

Ultimately I need to install backtrack myself and do some testing :D

I need to know just what version of backtrack you're using so I can track what versions of gawk and mawk are being used:

[http://distrowatch.com/table.php?distribution=backtrack](http://distrowatch.com/table.php?distribution=backtrack)

It's not something I'll get done within hours, or even days .............. more likely months :(

I tend to think backtrack needs some major updating to keep up with the times.

Guess what... I've booted into ubuntu 10.10 and then I did "sudo update-grub" and now I can boot every single OS in my laptop without problems! :D.  Anyways, I'll post the new results from the boot info script.  If you need anything else I'll be very happy to give you a hand! ;)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros 'crypto_LUKS' desconocido

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,181,524   104,181,462   7 HPFS/NTFS
/dev/sda2         104,194,047   312,580,095   208,386,049   5 Extended
/dev/sda5         104,194,048   216,829,304   112,635,257  83 Linux
/dev/sda6         216,829,368   304,014,059    87,184,692  83 Linux
/dev/sda7         304,021,504   312,580,095     8,558,592  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 3926 MB, 3926949888 bytes
121 cabezas, 62 sectores/pista, 1022 cilindros, 7669824 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,667,043     7,666,982   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/udisks-luks-uuid-135070c0-f0f8-40de-a74e-6cc26b393110-uid1000 F645-0213                              vfat       Mi USB                        
/dev/sda1        8E4C73B24C7393A5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1a7b0d01-96b2-4841-a485-54262fd0640a   ext4                                     
/dev/sda6        e2dd783f-fba9-4bb9-9275-fb86a550ffe9   ext3                                     
/dev/sda7        fe7bff26-b39b-44c6-ac66-9a1695cc11cf   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        135070c0-f0f8-40de-a74e-6cc26b393110   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
udisks-luks-uuid-135070c0-f0f8-40de-a74e-6cc26b393110-uid1000

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/mapper/udisks-luks-uuid-135070c0-f0f8-40de-a74e-6cc26b393110-uid1000 /media/Mi USB            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=FO76V0 /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=FO76V0-BAK 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
set locale_dir=($root)/boot/grub/locale
set lang=es
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8e4c73b24c7393a5
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e2dd783f-fba9-4bb9-9275-fb86a550ffe9
    linux /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro vga=0x317
    initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e2dd783f-fba9-4bb9-9275-fb86a550ffe9
    linux /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro single
    initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e2dd783f-fba9-4bb9-9275-fb86a550ffe9
    linux /boot/memtest86+.bin 
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1a7b0d01-96b2-4841-a485-54262fd0640a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=fe7bff26-b39b-44c6-ac66-9a1695cc11cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  53.5GB: boot/grub/core.img
  75.4GB: boot/grub/grub.cfg
  63.2GB: boot/initrd.img-2.6.35-22-generic
  69.4GB: boot/initrd.img-2.6.35-22-generic-pae
  61.1GB: boot/initrd.img-2.6.35-24-generic
  68.4GB: boot/initrd.img-2.6.35-25-generic
  69.9GB: boot/initrd.img-2.6.35-25-generic-pae
  62.6GB: boot/vmlinuz-2.6.35-22-generic
  68.4GB: boot/vmlinuz-2.6.35-22-generic-pae
  62.6GB: boot/vmlinuz-2.6.35-24-generic
  61.5GB: boot/vmlinuz-2.6.35-25-generic
  68.4GB: boot/vmlinuz-2.6.35-25-generic-pae
  69.9GB: initrd.img
  69.4GB: initrd.img.old
  68.4GB: vmlinuz
  68.4GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e2dd783f-fba9-4bb9-9275-fb86a550ffe9

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=e2dd783f-fba9-4bb9-9275-fb86a550ffe9/boot/grub/splash.xpm.gz

title        BackTrack 4 R2, kernel 2.6.35.8
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro vga=0x317 
initrd        /boot/initrd.img-2.6.35.8
quiet

title        BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro  single
initrd        /boot/initrd.img-2.6.35.8

title        BackTrack 4 R2, memtest86+
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-25-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-22-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=fe7bff26-b39b-44c6-ac66-9a1695cc11cf none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/menu.lst
 128.7GB: boot/grub/stage2
 128.8GB: boot/initrd.img-2.6.35.8
 128.8GB: boot/vmlinuz-2.6.35.8
 128.8GB: initrd.img
 128.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  6d 47 2a 8c 3a 5d 99 8b  85 11 c4 61 a6 3e d9 f2  |mG*.:].....a.>..|
00000080  18 42 e9 5b d0 fd 1b 0d  b0 46 81 d0 1d 5f 7b 52  |.B.[.....F..._{R|
00000090  25 b6 70 cb 2a fa 4e 50  6e aa 85 f4 c2 ea 5a 52  |%.p.*.NPn.....ZR|
000000a0  62 c4 8f 71 00 00 5d 43  31 33 35 30 37 30 63 30  |b..q..]C135070c0|
000000b0  2d 66 30 66 38 2d 34 30  64 65 2d 61 37 34 65 2d  |-f0f8-40de-a74e-|
000000c0  36 63 63 32 36 62 33 39  33 31 31 30 00 00 00 00  |6cc26b393110....|
000000d0  00 ac 71 f3 00 01 75 d8  ba 75 37 6f 41 11 04 ba  |..q...u..u7oA...|
000000e0  b3 94 2f 82 ec a2 6b 5c  1e 65 30 62 ae d1 0c da  |../...k\.e0b....|
000000f0  fb d1 fa 74 ec df 96 52  00 00 00 08 00 00 0f a0  |...t...R........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

```

---

### Post by kansasnoob on 2011-02-21
> **LePresident said:**
> Guess what... I've booted into ubuntu 10.10 and then I did "sudo update-grub" and now I can boot every single OS in my laptop without problems! :D.  Anyways, I'll post the new results from the boot info script.  If you need anything else I'll be very happy to give you a hand! ;)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros 'crypto_LUKS' desconocido

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,181,524   104,181,462   7 HPFS/NTFS
/dev/sda2         104,194,047   312,580,095   208,386,049   5 Extended
/dev/sda5         104,194,048   216,829,304   112,635,257  83 Linux
/dev/sda6         216,829,368   304,014,059    87,184,692  83 Linux
/dev/sda7         304,021,504   312,580,095     8,558,592  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 3926 MB, 3926949888 bytes
121 cabezas, 62 sectores/pista, 1022 cilindros, 7669824 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,667,043     7,666,982   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/udisks-luks-uuid-135070c0-f0f8-40de-a74e-6cc26b393110-uid1000 F645-0213                              vfat       Mi USB                        
/dev/sda1        8E4C73B24C7393A5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1a7b0d01-96b2-4841-a485-54262fd0640a   ext4                                     
/dev/sda6        e2dd783f-fba9-4bb9-9275-fb86a550ffe9   ext3                                     
/dev/sda7        fe7bff26-b39b-44c6-ac66-9a1695cc11cf   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        135070c0-f0f8-40de-a74e-6cc26b393110   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
udisks-luks-uuid-135070c0-f0f8-40de-a74e-6cc26b393110-uid1000

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/mapper/udisks-luks-uuid-135070c0-f0f8-40de-a74e-6cc26b393110-uid1000 /media/Mi USB            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=FO76V0 /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=FO76V0-BAK 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
set locale_dir=($root)/boot/grub/locale
set lang=es
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 1a7b0d01-96b2-4841-a485-54262fd0640a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8e4c73b24c7393a5
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e2dd783f-fba9-4bb9-9275-fb86a550ffe9
    linux /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro vga=0x317
    initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e2dd783f-fba9-4bb9-9275-fb86a550ffe9
    linux /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro single
    initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set e2dd783f-fba9-4bb9-9275-fb86a550ffe9
    linux /boot/memtest86+.bin 
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1a7b0d01-96b2-4841-a485-54262fd0640a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=fe7bff26-b39b-44c6-ac66-9a1695cc11cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  53.5GB: boot/grub/core.img
  75.4GB: boot/grub/grub.cfg
  63.2GB: boot/initrd.img-2.6.35-22-generic
  69.4GB: boot/initrd.img-2.6.35-22-generic-pae
  61.1GB: boot/initrd.img-2.6.35-24-generic
  68.4GB: boot/initrd.img-2.6.35-25-generic
  69.9GB: boot/initrd.img-2.6.35-25-generic-pae
  62.6GB: boot/vmlinuz-2.6.35-22-generic
  68.4GB: boot/vmlinuz-2.6.35-22-generic-pae
  62.6GB: boot/vmlinuz-2.6.35-24-generic
  61.5GB: boot/vmlinuz-2.6.35-25-generic
  68.4GB: boot/vmlinuz-2.6.35-25-generic-pae
  69.9GB: initrd.img
  69.4GB: initrd.img.old
  68.4GB: vmlinuz
  68.4GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e2dd783f-fba9-4bb9-9275-fb86a550ffe9

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=e2dd783f-fba9-4bb9-9275-fb86a550ffe9/boot/grub/splash.xpm.gz

title        BackTrack 4 R2, kernel 2.6.35.8
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro vga=0x317 
initrd        /boot/initrd.img-2.6.35.8
quiet

title        BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 ro  single
initrd        /boot/initrd.img-2.6.35.8

title        BackTrack 4 R2, memtest86+
uuid        e2dd783f-fba9-4bb9-9275-fb86a550ffe9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-25-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-22-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=1a7b0d01-96b2-4841-a485-54262fd0640a ro single 
initrd        /boot/initrd.img-2.6.35-22-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e2dd783f-fba9-4bb9-9275-fb86a550ffe9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=fe7bff26-b39b-44c6-ac66-9a1695cc11cf none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 128.8GB: boot/grub/menu.lst
 128.7GB: boot/grub/stage2
 128.8GB: boot/initrd.img-2.6.35.8
 128.8GB: boot/vmlinuz-2.6.35.8
 128.8GB: initrd.img
 128.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  6d 47 2a 8c 3a 5d 99 8b  85 11 c4 61 a6 3e d9 f2  |mG*.:].....a.>..|
00000080  18 42 e9 5b d0 fd 1b 0d  b0 46 81 d0 1d 5f 7b 52  |.B.[.....F..._{R|
00000090  25 b6 70 cb 2a fa 4e 50  6e aa 85 f4 c2 ea 5a 52  |%.p.*.NPn.....ZR|
000000a0  62 c4 8f 71 00 00 5d 43  31 33 35 30 37 30 63 30  |b..q..]C135070c0|
000000b0  2d 66 30 66 38 2d 34 30  64 65 2d 61 37 34 65 2d  |-f0f8-40de-a74e-|
000000c0  36 63 63 32 36 62 33 39  33 31 31 30 00 00 00 00  |6cc26b393110....|
000000d0  00 ac 71 f3 00 01 75 d8  ba 75 37 6f 41 11 04 ba  |..q...u..u7oA...|
000000e0  b3 94 2f 82 ec a2 6b 5c  1e 65 30 62 ae d1 0c da  |../...k\.e0b....|
000000f0  fb d1 fa 74 ec df 96 52  00 00 00 08 00 00 0f a0  |...t...R........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 01 08 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

```

Cool! If you do happen to still be reading this you'd be doing me a huge favor if you'd post the output of these two commands while you're booted into BackTrack:

```
gawk -W version
```

```
mawk -W version
```

Then maybe we can figure out why the Boot Info Script doesn't detect things properly when run from BackTrack.

---

### Post by Gert Hulselmans on 2011-02-21
Backtrack probably doesn't have ext4 support.

@ LePresident
Can you run the last development version (see my signature).

The mount error for the  crypto_LUKS partition should be gone:
```
sdb1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros 'crypto_LUKS' desconocido
```

---

