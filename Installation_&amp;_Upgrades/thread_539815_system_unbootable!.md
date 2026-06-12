---
title: "system unbootable!"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Lary Grant on 2007-08-31
I had installed Dapper at (hd0,2) and (much later) Feisty on (hd0,5).   If I understand correctly, the Feisty install configured the MBR to load grub from (hd0,5).  In an attempt to go back to booting Dapper, I did the following:

grub> root (hd0,2)
grub> setup (hd0)
grub> quit

However, once I shut down, the system no longer boots!   All the BIOS says is "Floppy failure", which I presume is because the hard disk boot is failing, so it's trying the floppy.

I can still boot from the CD (which I'm doing now) and see all my files (in both the Dapper and Feisty partitions)

How do I get my system to boot Dapper, i.e. (hd0,2) ?

---

### Post by Pumalite on 2007-08-31
In the Live CD Terminal:
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdax /media/ubuntu (x represents a partition you know)
cat /boot/grub/menu.lst
sudo fdisk -l (small L)
Post them..

---

### Post by Lary Grant on 2007-08-31
```

ubuntu@ubuntu:/media/ubuntu$ cat /media/ubuntu/boot/grub/menu.lst
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
# kopt=root=/dev/hda3 ro

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
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-29-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-29-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-29-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-29-386
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:/media/ubuntu$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1829    14651280    7  HPFS/NTFS
/dev/sda3            1830        8351    52387965   83  Linux
/dev/sda4            8352        9726    11044687+   5  Extended
/dev/sda5            9539        9726     1510078+  82  Linux swap / Solaris
/dev/sda6   *        8352        9481     9076662   83  Linux
/dev/sda7            9482        9538      457821   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14187   113957046   83  Linux
/dev/sdb3           14188       14593     3261195    5  Extended
/dev/sdb5           14188       14593     3261163+  82  Linux swap / Solaris


```

---

### Post by Lary Grant on 2007-08-31
In case this helps, the end of the "mount" output is:
```
/dev/sda3 on /media/ubuntu type ext3 (rw)
```

---

### Post by Pumalite on 2007-08-31
According to this Ubuntu is on sda3. I need sudo fdisk -l (small L). Lets see if it's true.

---

### Post by Lary Grant on 2007-08-31
I already posted it, after the menu.lst output

---

### Post by Lary Grant on 2007-08-31
sda3 is partion 2, right?  In that case, my grub commands should have been right.

---

### Post by Pumalite on 2007-08-31
Well check your system and your hard drive in particular with rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Let us know what you find.

---

### Post by Pumalite on 2007-08-31
Change menu.lst: Below Ubuntu, where it says 'root (hd0.2)' to 'root (hd0,1)' If that doesn't work, try (hd0,5)
First backup menu.lst:
cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
I hope it works.

---

### Post by merlinus on 2007-08-31
Looks like you have a boot flag set on sda6.  Try removing it with gparted, and see if that makes a difference after restarting..

-merlin

---

### Post by Pumalite on 2007-08-31
You are a good teacher, Merlin.

---

### Post by merlinus on 2007-08-31
Thanks for the compliment, Pumalite, but most of the time I am flying with the seat of my pants.

:)

-merlin

---

### Post by Lary Grant on 2007-09-02
> **Pumalite said:**
> Change menu.lst: Below Ubuntu, where it says 'root (hd0.2)' to 'root (hd0,1)' If that doesn't work, try (hd0,5)
First backup menu.lst:
cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
I hope it works.

I don't understand why it would help to edit menu.lst.  I am not even getting to the point where I see the boot menu.

---

### Post by Pumalite on 2007-09-02
You have Windows in sda2; menu.lst correctly sets it to (hd0,1). You have 2 Linux systems: sda6 and sdb1 ( they are probably your Dapper and Feisty); your menu.lst doesn't point to either one of them, it's pointing to (hd0,2)(sda3), so if you want to boot your system, you will have to change Ubuntu in menu.lst to either (hd0,5) or (hd1,0)(bootflags are in both of them)

---

### Post by meierfra on 2007-09-02
I don't believe this is the case, but maybe computer is trying to boot from your second hard drive ( which is just  for  storage?) ? Can you change the boot order in the bios?

---

### Post by Lary Grant on 2007-09-02
Well, I've made my system bootable again by re-installing feisty in the same place (/dev/sda6).

While I am breathing easier, this is still not the optimum situation... I am essentially back to where I started... I really do not want the feisty installation (due to feisty's inability to recognize my DVD/CD drive).  However, I am relying on the Feisty installation just to boot me into Dapper!  Grub is still going into the Feisty partition to read the menu.lst from Feisty and I have to select the Dapper installation from the "Other Operating Systems" section.

Besides for being weird and wasteful, this setup prevents me from getting Dapper kernel updates easily because the Dapper Update Manager will only update the menu.lst that's under the Dapper instalation, which in my weird case, is not being used at all.

How do I get grub to point to the correct (Dapper) partition?

---

### Post by meierfra on 2007-09-02
> grub> root (hd0,2)
grub> setup (hd0)
grub> quit

This really should have done it.  But maybe there is a mix-up between your  drives. Could you post  your   menu.lst from your feisty install  and the output of

```
cat /boot/grub/device.map
```

---

### Post by Lary Grant on 2007-09-03
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

---

### Post by logos34 on 2007-09-03
> **Lary Grant said:**
> ...Grub is still going into the Feisty partition to read the menu.lst from Feisty and I have to select the Dapper installation from the "Other Operating Systems" section.

Besides for being weird and wasteful, this setup prevents me from getting Dapper kernel updates easily because the Dapper Update Manager will only update the menu.lst that's under the Dapper instalation, which in my weird case, is not being used at all.

I agree you ought to be able to boot directly to Dapper, but just so you don't have to edit the Feisty menu.lst after kernel updates in Dapper you might want to use the[ 'configfile' option]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").

---

