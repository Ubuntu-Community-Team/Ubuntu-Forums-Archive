---
title: "Grub Loading Error 17"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by DapperDrakeNewbieDR on 2006-09-26
Hi, since I deleted one of my "windows" partions in order to make more room for ubuntu, I'm getting this "Error 17". I've modified the menu.lst file and nothing. I've fallowed the instrucions on this thread [http://ubuntuforums.org/showthread.php?t=235044&highlight=error+17](http://ubuntuforums.org/showthread.php?t=235044&highlight=error+17) and nothing.

This is the output of the "sudo fdisk -lu" command

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40981814    20490876    7  HPFS/NTFS
/dev/sda2       112663845   152826344    20081250   83  Linux
/dev/sda3       152826345   153356489      265072+  82  Linux swap / Solaris
/dev/sda4        40981815   112663844    35841015   83  Linux

Partition table entries are not in disk order
```

Is the "(*)" at the Boot HPFS/NTFS partion part of the problem?

And this is the output of my "menu.lst" file.

```
ubuntu@ubuntu:~$ cat /media/ubuntu/boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=7

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-26-686
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:~$


```


Does anybody know what I'm doing wrong? 
Thanks in advance.

---

### Post by mitch.c on 2006-09-26
> **DapperDrakeNewbieDR said:**
> Hi, since I deleted one of my "windows" partions in order to make more room for ubuntu, I'm getting this "Error 17".

This is the output of the "sudo fdisk -lu" command

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40981814    20490876    7  HPFS/NTFS
/dev/sda2       112663845   152826344    20081250   83  Linux
/dev/sda3       152826345   153356489      265072+  82  Linux swap / Solaris
/dev/sda4        40981815   112663844    35841015   83  Linux

Partition table entries are not in disk order
```

Is the "(*)" at the Boot HPFS/NTFS partion part of the problem?

No, that just means the partition is active. I think the key here is "Partition table entries are not in disk order". If you look at the Start block on /dev/sda4, you'll see it comes before /dev/sda2. If linux is on /dev/sda4, then your entry in menu.lst should read:
```
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot
```
Do you know for sure which partition linux is on? Can you post the full grub error message?

---

### Post by DapperDrakeNewbieDR on 2006-09-26
Ok, my File System is at /dev/sda2. And the grub error message is:

```
GRUB Loading stage1.5

GRUB loading, please wait....
Error 17
```

---

### Post by pradeepadapa on 2006-09-26
hi man,

          actually ur active linux partition must not be pointed to NTFS partition it must point to sda2 or sda4, u just reinstall the grub by using the foll commands, no need much to edit the menu.lst file

at the $ prompt from the UBUNTU LIVE cd

type $sudo -i

#grub
grub> find /boot/grub/stage1

u will get the ans like (hd0,1) or (hdx,x), then in the next line
grub> root (hd0,1)      instead of hd0,1 u type the ans u got in the above line nd press enter

grub> setup (hd0,1)    then press enter,

now restart the system, ur grub will work, if u hav any problm u can again contact us.

bye.hope this works.

---

### Post by DapperDrakeNewbieDR on 2006-09-26
Hi pradeepadapa,

This is what I got...I restarted the computer but unfortunatly didn't work:

```
grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub>

```


Oh, by the way I'm still getting the same output after I run the "sudo fdisk -lu"

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40981814    20490876    7  HPFS/NTFS
/dev/sda2       112663845   152826344    20081250   83  Linux
/dev/sda3       152826345   153356489      265072+  82  Linux swap / Solaris
/dev/sda4        40981815   112663844    35841015   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

```

---

### Post by DapperDrakeNewbieDR on 2006-09-26
Hi again pradeepadapa, I just fixed the problem, I got the answer from [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli) [GRUB Page]

What you were telling me to do was correct, but instead of writing "setup (hd0,1)" I had to write the following:

```
grub> setup (hd0)
```

And It worked perfectly fine.

Well, thanks for your assistance! see you around.

---

