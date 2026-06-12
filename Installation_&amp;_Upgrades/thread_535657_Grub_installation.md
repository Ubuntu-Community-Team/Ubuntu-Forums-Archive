---
title: "Grub installation"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by gramsyn on 2007-08-26
I have the Ubuntu OS working properly. However, when I formatted the Windows drive, there was no grub and I cannot choose to load Ubuntu. How can I install the Grub without having to install Ubuntu again?

---

### Post by merlinus on 2007-08-26
Boot to a terminal from the live cd, and try this:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y).

-merlin

---

### Post by gramsyn on 2007-08-26
The command root (hdx,dy) and setup (hdx) returns "error while parsing number". Maybe a mistyping?

---

### Post by Pumalite on 2007-08-26
The 'x' and 'y' are to be replaced by your findings in 'find'.

---

### Post by gramsyn on 2007-08-26
Sorry, I cannot understand what you mean by: "Substitute results from find for (hdx,y)."

---

### Post by bake7221 on 2007-08-26
I did this ... and restored Grub and the ability to boot Kubuntu, but how do I boot into my windows install now? I need to use it but I don't want to delete Kubuntu and VMWare can't handle what I need to do ...

---

### Post by merlinus on 2007-08-26
Enter the commands one at a time, and subsitute the results from find in the next two commands.

For example, root (hd0,0} and setup (hd0).

-merlin

---

### Post by merlinus on 2007-08-26
> **bake7221 said:**
> I did this ... and restored Grub and the ability to boot Kubuntu, but how do I boot into my windows install now? I need to use it but I don't want to delete Kubuntu and VMWare can't handle what I need to do ...

Post results of:

```

cat /boot/grub/menu.lst
sudo fdisk -l

```

-merlin

---

### Post by bake7221 on 2007-08-26
Thanks in advance for your help Merlin ...

simon@simon-desktop:~$ cat /boot/grub/menu.lst
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
timeout         3

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
# kopt=root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=076edb4d-9f8f-4fb5-80a2-9e37dcade02d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
simon@simon-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       27732   222757258+  83  Linux
/dev/sda2   *       27733       29644    15358140    7  HPFS/NTFS
/dev/sda3           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

---

### Post by merlinus on 2007-08-26
Try adding this after

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Microsoft Windows XP
rootnoverify        (hd0,1)
makeactive
chainloader    +1

-merlin

---

### Post by bake7221 on 2007-08-26
Merlinus,

You're the man ... thanks so very much

- Bake

---

### Post by merlinus on 2007-08-26
You are most welcome!  Glad it is working.

Post back if you need more assistance.

-merlin

---

### Post by gramsyn on 2007-08-26
I did what you said and retrieved the Grub when restarted the system. I chose Ubuntu at the list but then a message came: "Error 15 File not found". What should I do?

---

### Post by merlinus on 2007-08-26
Can you boot into Recovery Mode?

-merlin

---

### Post by gramsyn on 2007-08-26
No, the same message appears

---

### Post by merlinus on 2007-08-26
You might supergrub.

d/l here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Info on use here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by gramsyn on 2007-08-26
I boot from the CD of supergrub, but I still retrieve the same message

---

### Post by merlinus on 2007-08-26
Did you get to the supergrub menu?  It would not seem so.

Did you burn the download correctly?  If so, your computer would have booted from the cd.

-merlin

---

### Post by gramsyn on 2007-08-26
Yes. It boots from CD. I choose the proper menus (as written in the link you gave me). I receive a message of success, but then, the same message appears.

(I downloaded the demo version). But I don't think that this is the problem

---

### Post by merlinus on 2007-08-26
OK.  I just wanted to check and be sure.

You will have to boot from the live cd and manually mount your ubuntu partition.

```

sudo fdisk -l

```will show which partition this is.

Then

```

sudo mkdir /media/ubuntu
sudo mount  -[SIZE=3]t ext3 /dev/sda2 /media/ubuntu
[/SIZE]
```[SIZE=3]
(substitute the ubuntu partition from fdisk -l for sda2)

Then post results of:

```

cat /media/ubuntu/boot/grub/menu.lst

```Also post output of sudo fdisk -l

-merlin
[/SIZE]

---

### Post by gramsyn on 2007-08-26
Where should I write this code?

I realized that when I choose windows there is a message :"Invalid Device Requested"

---

### Post by merlinus on 2007-08-26
Open a terminal from the live cd desktop:

Applications/Accessories

Also best to copy-and-paste commands.  Use Shift-Insert in the terminal window to paste.

-merlin

---

### Post by gramsyn on 2007-08-26
I received the following output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        1275    10233405    f  W95 Ext'd (LBA)
/dev/hda2            1276        3707    19535040   83  Linux
/dev/hda3   *        3708        9541    46861605    b  W95 FAT32
/dev/hda4            9542        9729     1510078+  82  Linux swap / Solaris
/dev/hda5               2        1275    10233373+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    b  W95 FAT32
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount  -t ext3 /dev/hda2 /media/ubuntu
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
# kopt=root=UUID=ab13e529-3173-4b72-8605-2286b26f1f5f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ab13e529-3173-4b72-8605-2286b26f1f5f ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ab13e529-3173-4b72-8605-2286b26f1f5f ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ab13e529-3173-4b72-8605-2286b26f1f5f ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ab13e529-3173-4b72-8605-2286b26f1f5f ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by merlinus on 2007-08-26
[SIZE=3]```

gksudo gedit /media/ubuntu/boot/grub/menu.lst

```

Change all ubuntu root references to (hd0,1) from hd(0,2) and windows root to (hd0,2).

Remove cd, reboot and see what happens.

-merlin
[/SIZE]

---

### Post by gramsyn on 2007-08-26
I found somewhere the following:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

Should I change groot to hd0,1?

I changed the others at the end of .lst text.

---

### Post by merlinus on 2007-08-26
Yes.  That way, when there are kernel upgrades, grub will be unaffected.

-merlin

---

### Post by gramsyn on 2007-08-26
It worked. Thanks a lot

---

### Post by merlinus on 2007-08-26
Great news!  Post back with any other issues.

-merlin

---

