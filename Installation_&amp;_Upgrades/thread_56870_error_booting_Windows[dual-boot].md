---
title: "error booting Windows[dual-boot]"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by ultima2k on 2005-08-14
I have bought a WD Raptor 36GB harddrive to use as system disk. I first installed Windows and then went over to Ubuntu. The grub thing does something with the MBR on my first IDE-drive (have three of them) to make it able to boot ubuntu.

Booting ubuntu works perfect, but the bad thing is that when I try to boot windows it just says that it's an unknown filesystem or something and that NTLDR couldn't be found...

When I unplug all my IDE-drives windows boot normally, so there's nothing screwed up with it...

What should I do? Unplugging disks to be able to access windows/linux isn't funny :(

---

### Post by h4rdc0d3 on 2005-08-16
Do you have a floppy in the floppy drive? I used to get the missing NTLDR msg all the time and that's what it was.

---

### Post by al7kz on 2005-08-16
Need more info to help. With all drives plugged in what is results of 
$ sudo fdisk -l
What is the windows entry in menu.lst?
Which drive/partition has the Windows OS?

---

### Post by al7kz on 2005-08-17
Corrected fdisk command in previous post.

---

### Post by ultima2k on 2005-08-18
h4rdc0d3: nope, don't even have one :p (only using one when I need to read sata-drivers at windows-install)

al7kz: posting the whole thing :P
"/dev/sda1" is the windows-partition...it only boot when I unplug both IDE-cables. Tryed changing what drive to boot från in BIOS, thought if you choose the sata-drive that windows whould work, but nope :S

btw...i'm using swedish as language in ubuntu :P

**menu.lst**
```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd3,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
chainloader	+1


```

**fdisk**
```
Disk /dev/sda: 37,0 GB, 37019566080 byte
255 huvuden, 63 sektorer/spÃ¥r, 4500 cylindrar
Enheter = cylindrar av 16065 Ã— 512 = 8225280 byte

    Enhet Start     BÃ¶rjan        Slut     Block    Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        4468     5172930   83  Linux
/dev/sda3            4469        4500      257040    5  UtÃ¶kad
/dev/sda5            4469        4500      257008+  82  Linux vÃ¤xling / Solaris

Disk /dev/hda: 122,9 GB, 122942324736 byte
255 huvuden, 63 sektorer/spÃ¥r, 14946 cylindrar
Enheter = cylindrar av 16065 Ã— 512 = 8225280 byte

    Enhet Start     BÃ¶rjan        Slut     Block    Id  System
/dev/hda1   *           1        9847    79095996    7  HPFS/NTFS
/dev/hda2            9848       14946    40957717+   7  HPFS/NTFS

Disk /dev/hdb: 122,9 GB, 122942324736 byte
255 huvuden, 63 sektorer/spÃ¥r, 14946 cylindrar
Enheter = cylindrar av 16065 Ã— 512 = 8225280 byte

    Enhet Start     BÃ¶rjan        Slut     Block    Id  System
/dev/hdb1               1       14946   120053713+   7  HPFS/NTFS

Disk /dev/hdc: 200,0 GB, 200049647616 byte
16 huvuden, 63 sektorer/spÃ¥r, 387621 cylindrar
Enheter = cylindrar av 1008 Ã— 512 = 516096 byte

    Enhet Start     BÃ¶rjan        Slut     Block    Id  System
/dev/hdc1   *           1      387618   195359440+   7  HPFS/NTFS

Disk /dev/sdb: 513 MB, 513802240 byte
16 huvuden, 32 sektorer/spÃ¥r, 1960 cylindrar
Enheter = cylindrar av 512 Ã— 512 = 262144 byte

    Enhet Start     BÃ¶rjan        Slut     Block    Id  System
/dev/sdb1   *           1        1960      501744    b  W95 FAT32

```

---

### Post by ultima2k on 2005-08-18
Seems like if I boot with SCSI instead of HD-(0-3) I boot windows, so now I can at least use both systems without unplugging anything, but it's still not anything I wanna change all the time...

btw, this is what it says when I try to boot windows throught GRUB:
```
  Booting 'Microsoft Windows XP Professional'
root (hd3,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```

---

### Post by al7kz on 2005-08-18
I'm not sure which drive you installed grub to but you could try this: change the windoze entry in grub to:

title windowze
rootnoverify (hd3,0)
map (hd3) (hd0)
map (hd0) (hd3)
makeactive
chainloader +1

This assumes you have set ide drives to boot before scsi in bios.

---

### Post by ev0l on 2005-08-18
i had the same problem and fixed it by using the map command (like al7kz wrote)

maybe this will help you:
[http://wiki.archlinux.org/index.php/Grub_configure_examples#Linux_and_Windows_in_Grub.2C_with_windows_on_a_hard_drive_other_then_the_first_one](http://wiki.archlinux.org/index.php/Grub_configure_examples#Linux_and_Windows_in_Grub.2C_with_windows_on_a_hard_drive_other_then_the_first_one)

---

### Post by ultima2k on 2005-08-19
Tried the mapping thing and got an error message, found out now I spelled noverify wrong :p
Then I just tryed booting the normal way which didn't work before and for some strange reason it works....sick :S

---

### Post by bela on 2005-08-19
Hi,
The grub file is generated automatiquely, this is strange because the third disk is normally hd2, and not hd3 ( the fisrt is hd0), since you have only 3 disks, hd0, hd1,hd2

do you have hot plug disk ? have you add a disk after installation ?


best regards
bela

---

