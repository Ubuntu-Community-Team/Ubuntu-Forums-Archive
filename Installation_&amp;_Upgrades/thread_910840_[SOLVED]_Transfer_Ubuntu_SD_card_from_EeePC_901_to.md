---
title: "[SOLVED] Transfer Ubuntu SD card from EeePC 901 to 1000"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-09-04
(long post, get some coffee first!)

I had first a 901 and installed Ubuntu 8.04.1, upgraded it to the EeePC kernel and ran the script to fix all the function buttons, ... 
Added some programs so that everything as I like.

Now I got a 1000 and wanted to use the installed SD card there, but it did not work. I know it is a long post, but I hope that we can therefore solve it without asking for additional details ;-)

I would appreciate if you can help me to:
1. fix the installation on 901, so that it works without SD card again and the SD card becomes portable
2. help me to get it ported to the 1000 (including how to make the SD card copy)


Here are the data, I think you need:

**EeePC 901** (Ubuntu on SD /dev/sdc1, Xandros on /dev/sda1):

BIOS
====
> Boot Device Priority
1. removable Dev.
2. HDD:SM-Asus-PHISON
3. USB:HUAWEI Mass St  without Huawei modem:    3. ATAPI CD-ROM

Hard Disk Drives
1. HDD:SM-ASUS-PHISON
2. HDD:SS-ASUS-PHISON
3. USB:Single Flash R





 sudo fdisk -l
[sudo] password for ronald:

> Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         400     3212968+  83  Linux
/dev/sda2             401         488      706860   83  Linux
/dev/sda3             489         489        8032+   c  W95 FAT32 (LBA)
/dev/sda4             490         490        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59c459c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux


Disk /dev/sdc: 8204 MB, 8204058624 bytes
108 heads, 6 sectors/track, 24727 cylinders
Units = cylinders of 648 * 512 = 331776 bytes
Disk identifier: 0x000b4885

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              13       24728     8007680   83  Linux



cat /boot/grub/menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-21-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-eeepc
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-21-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro single
initrd        /boot/initrd.img-2.6.24-21-eeepc

title        Ubuntu 8.04.1, kernel 2.6.24-20-eeepc
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-20-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro quiet splash
initrd        /boot/initrd.img-2.6.24-20-eeepc
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-20-eeepc (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-20-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro single
initrd        /boot/initrd.img-2.6.24-20-eeepc

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd2,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Normal Boot (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1
initrd        /boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Perform Disk Scan (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y
initrd        /boot/initramfs-eeepc.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Restore Factory Settings (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y
initrd        /boot/initramfs-eeepc.img
savedefault
boot




ronald@ronald-901:~$ sudo mount /dev/sda1 /mnt/sda1
ronald@ronald-901:~$ cat /mnt/sda1/boot/grub/menu.lst
> #
# Configured by Xandros Configuration system.
#
hiddenmenu
# default boot entry
default=0

# Boot automatically after 1 second.
timeout=0

# Fallback to Configure.
fallback=2

title Normal Boot
    root (0x80,0)
    kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1
    initrd /boot/initramfs-eeepc.img

title Perform Disk Scan
    root (0x80,0)
    kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y
    initrd /boot/initramfs-eeepc.img

title Restore Factory Settings
    root (0x80,0)
    kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y
    initrd /boot/initramfs-eeepc.img



**EeePC 1000** (Xandros - nothing else installed yet):

BIOS
====
> Boot Device Priority
1. Removable Dev.
2. HDD:SM-ASUS-PHISON
3. ATAPI CD-ROM

Hard Disk Drives
1. HDD:SM-ASUS-PHISON
2. HDD:SS-ASUS-PHISON


/home/user> cat /boot/grub/menu.lst
> #
# Configured by Xandros Configuration system.
#
hiddenmenu
# default boot entry
default=0

# Boot automatically after 1 second.
timeout=0

# Fallback to Configure.
fallback=2

title Normal Boot
        root (0x80,0)
        kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/s
da1
        initrd /boot/initramfs-eeepc.img

title Perform Disk Scan
        root (0x80,0)
        kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/s
da1 XANDROSSCAN=y
        initrd /boot/initramfs-eeepc.img

title Restore Factory Settings
        root (0x80,0)
        kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpo
ll root=/dev/sda1 XANDROSRESTORE=y
        initrd /boot/initramfs-eeepc.img





**Boot of 901 without SD card (Ubuntu)**
> GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21


Change BIOS to:
BIOS
====
> Boot Device Priority
1. HDD:SM-ASUS-PHISON
2. ATAPI CD-ROM
3. Removable Dev.

Hard Disk Drives
1. HDD:SM-ASUS-PHISON
2. HDD:SS-ASUS-PHISON

results in:

> GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

===> Can only boot if SD card available!!!!







**Boot of 1000 with SD card (Ubuntu)**

Change BIOS to:
BIOS
====
> Boot Device Priority
1. removable Dev.
2. HDD:SM-Asus-PHISON
3. ATAPI CD-ROM

Hard Disk Drives
1. USB:Single Flash R
2. HDD:SM-ASUS-PHISON
3. HDD:SS-ASUS-PHISON


stops without an error and black screen and flashing courser on the top

 
Thanks for reading, ... any thoughts how to fix it?

bye

R.

---

### Post by falcon61102 on 2008-09-05
As far as the 901 goes, it sounds like you have the GRUB installed to the SD and not to the internal.  If you boot back up with the SD in, you should be able to fix this with the GRUB:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
quit
```

When you run the find command, it may find two different entries for (hdX,Y).  Make sure that you use the internal driver for the root and the setup commands.

If you run into problems with that, you could give the Super GRUB Disk a try, get it at:
[www.supergrubdisk.org](www.supergrubdisk.org)

Once you get that complete I think you need to reinstall the GRUB on the SD because right now you only have a partial GRUB installation on there.  For the GRUB on the SD, go back through the steps above, but use the other result of the find command, the one for your SD card. 

I'm going to make an example to clarify:
```
sudo grub
grub>find /boot/grub/stage1
(hd0,0) #Internal Debian Install
(hd1,0) #SD Card Ubuntu install
grub>root (hd1,0)
grub>setup (hd1)
grub>quit
```
It is important that you use the right (hdX) otherwise you'll end up right back where you were in the beginning.

Once that successfully completes, try booting with it again in the 1000.

Hope this helps.

---

### Post by ELMIT on 2008-09-05
Thank you very much, but I am still a little bit scared to complete all at once.

I started with:
sudo grub
find /boot/grub/stage1


and the answer was:
  (hd0,0)
  (hd2,0)


What does that mean?
(My guess: hd0 is the internal Xandros SD card, while hd2 is the Ubuntu SD card)

I would then just continue with:
root (hd0,0)
setup (hd0)
quit


With that I would have then two equal stages of EeePC 901 and EeePC 1000.


I tried on the EeePC 1000
sudo grub
grub>find /boot/grub/stage1
  (hd0,0)



How do I install Grub on the SD card again????

Thank you very much for your help.

bye

R.

---

### Post by falcon61102 on 2008-09-05
Before you continue with the GRUB install.  Run:
```
sudo fdisk -l
```
-l being a lower case L

And post the results here.  That will tell us for sure which drive is which.

And hold off on reinstalling the GRUB to the Ubuntu SD card for now.  Lets get your 901 booting by itself first.

---

### Post by ELMIT on 2008-09-05
sudo fdisk -l
[sudo] password for ronald:

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         400     3212968+  83  Linux
/dev/sda2             401         488      706860   83  Linux
/dev/sda3             489         489        8032+   c  W95 FAT32 (LBA)
/dev/sda4             490         490        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59c459c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux

Disk /dev/sdc: 8204 MB, 8204058624 bytes
108 heads, 6 sectors/track, 24727 cylinders
Units = cylinders of 648 * 512 = 331776 bytes
Disk identifier: 0x000b4885

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              13       24728     8007680   83  Linux

---

### Post by falcon61102 on 2008-09-05
Yes, you were correct earlier.  To reinstall the GRUB to the internal you need:
```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

That should do it.

---

### Post by ELMIT on 2008-09-05
Thanks, that worked, now they both ignore the SD card and run right away Xandros.

Two steps are still to do:
1. How can I install GRUB now on the SD card?
2. How can I duplicate the SD card?

bye

R.

---

### Post by falcon61102 on 2008-09-05
To install the GRUB to the SD card, run the GRUB steps over again except using:
```
sudo grub
root (hd2,0)
setup (hd2)
quit
```

---

### Post by ELMIT on 2008-09-05
I did:

sudo grub
root (hd2,0)
setup (hd2)
quit

and rebooted. Xandros boots up.

I changed the boot sequence to use first the SD-Ubuntu card and it comes up with the Grub menu, but choosing the EeePC kernel shows then:

Error 15: File not found
Press any key to continue...

I can also NOT move down and use "Normal Boot (on /dev/sda1)

How can I fix that?

bye

R.

---

### Post by falcon61102 on 2008-09-05
That's typically generated when the GRUB can't find the kernal path.  Take a look at the settings for the root (hdX,Y) and for the kernal path to see if their correct.  Also run:
```
sudo blkid
```
and compare the UUID for your partition for the one listed on the menu.lst

If you want another set of eyes, post that info up here and I'll take a look at it.

---

### Post by ELMIT on 2008-09-05
I booted with Xandros (no other choice yet) and it mounts the SD card. Have a look at these two commands:

/boot/grub> sudo blkid  (before adding the card)
/dev/sda1: LABEL="SYSTEM" UUID="15fb1bc0-1a9d-448f-8f49-e01dcc163a24" TYPE="ext2"
/dev/sda2: LABEL="USER" UUID="9d390460-af39-4d0b-9d49-abff7b07b93f" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: SEC_TYPE="msdos" LABEL="BIOS" UUID="4896-F157" TYPE="vfat"
/dev/sdb1: LABEL="HOME" UUID="0f0fcc7d-8352-42fd-b4d6-4fc88f7753ba" SEC_TYPE="ext2" TYPE="ext3"


/boot/grub> sudo blkid   (after adding the card)
/dev/sda1: LABEL="SYSTEM" UUID="15fb1bc0-1a9d-448f-8f49-e01dcc163a24" TYPE="ext2"
/dev/sda2: LABEL="USER" UUID="9d390460-af39-4d0b-9d49-abff7b07b93f" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: SEC_TYPE="msdos" LABEL="BIOS" UUID="4896-F157" TYPE="vfat"
/dev/sdb1: LABEL="HOME" UUID="0f0fcc7d-8352-42fd-b4d6-4fc88f7753ba" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc1: UUID="895df0d5-ad36-49c4-9f68-2fda8b590e32" TYPE="ext2"



/boot/grub> cat /etc/mtab
rootfs / rootfs rw 0 0
/dev/sda1 / ext2 ro 0 0
none / aufs rw,xino=/.aufs.xino,br:/=rw:/=ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
tmpfs /tmp tmpfs rw 0 0
/dev/sdb1 /home ext3 rw,noatime,data=ordered 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/sda1 /ro ext2 ro 0 0
/dev/sdc1 /media/D: vfat rw,nosuid,nodev,noexec,fmask=0111,dmask=0000,codepage=cp850,iocharset=utf8,shortname=mixed 0 0


vfat and ext2 <=== 

bye

R.

---

### Post by falcon61102 on 2008-09-05
I wouldn't worry too much about how your drive is being classified.  Were you able get anywhere with the other stuff?

---

### Post by ELMIT on 2008-09-05
No!

I have no idea what I should do now!
I cannot access menu.lst of the SD card !!!!

bye

R.

---

### Post by falcon61102 on 2008-09-05
Let's try this.  Let's add Ubuntu to the GRUB for your internal drive, then you can get back into Ubuntu.

Add this to your menu.lst that is on your internal drive:
```
title Ubuntu 8.04.1, kernel 2.6.24-21 External SD
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-21-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-eeepc
quiet
```

And then reboot and if the GRUB menu normally doesn't display on the screen, press ESC as soon as you see GRUB Stage 1 Loading...

Make sure you pick the right one and it should boot up.

If it gives you an error, restart and when you get back to the GRUB menu, select the Ubuntu path but then press "e" to edit and change the root string from (hd2,0) to (hd1,0)

---

### Post by ELMIT on 2008-09-05
That does not work!

I added 
> title Ubuntu 8.04.1, kernel 2.6.24-21 External SD
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-21-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-eeepc
quiet

reboot, shutdown, restart, ... all the same result it boots Xandros
With ESC I get a blue selection which harddisk I want to boot
With F9 I get the Grub Menu, but there is not the lines we added. I checked, and they are in menu.lst
I also changed from hd2,0 to hd1,0 without any success.

What can we try next?

bye

Ronald

---

### Post by falcon61102 on 2008-09-05
First, could you post your menu.lst here?

Second, when you boot up, does it automatically display the GRUB menu?

---

### Post by ELMIT on 2008-09-05
cat menu.lst
#
# Configured by Xandros Configuration system.
#
hiddenmenu
# default boot entry
default=0

# Boot automatically after 1 second.
timeout=0

# Fallback to Configure.
fallback=2

title Normal Boot
        root (0x80,0)
        kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1
        initrd /boot/initramfs-eeepc.img

title Ubuntu 8.04.1, kernel 2.6.24-21 External SD
        root (hd1,0)
        kernel        /boot/vmlinuz-2.6.24-21-eeepc root=UUID=895df0d5-ad36-49c4-9f68-2fda8b590e32 ro quiet splash
        initrd        /boot/initrd.img-2.6.24-21-eeepc
        quiet

title Perform Disk Scan
        root (0x80,0)
        kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=785 irqpoll root=/dev/sda1 XANDROSSCAN=y
        initrd /boot/initramfs-eeepc.img

title Restore Factory Settings
        root (0x80,0)
        kernel /boot/vmlinuz-2.6.21.4-eeepc quiet rw vga=normal nosplash=y irqpoll root=/dev/sda1 XANDROSRESTORE=y
        initrd /boot/initramfs-eeepc.img


----

No, it does not automatically display the boot menu, with ESC I can select the disk to boot from and with F9 I get the boot menu, but WITHOUT the Ubuntu line !!!

bye

R.

---

### Post by falcon61102 on 2008-09-05
Try this.  See the line that says hiddenmenu, place a # in front of that and and change timeout=0 to timeout=10.  That should display the GRUB for 10 seconds.

---

### Post by ELMIT on 2008-09-05
Did not change anything!

BTW, if I re-mount /dev/sdc1 as -t ext2 I have all data, ... so we have not lost them so far, ...

What next?

BTW, do you have a messenger to speed up?

bye

R.

---

### Post by ELMIT on 2008-09-05
Found out why the menu does not show up!

We changed /boot/grub/menu.lst but there is also a /ro/boot/grub/menu.lst

A diff shows exactly what we changed, and this file does not allow to be altered.

bye

R.

---

### Post by ELMIT on 2008-09-05
FOUND IT!!!!

Thanks for your patient.

Our first boot device is the external 8GB SD card

I had to:
1. use automatically mounted /dev/sdc1:
sudo umount /dev/sdc1

2. remount it as ext2, so that I can get to the data:
sudo mount -t ext2 /dev/sdc1 /media/D:

3. change hd2,0 to hd0,0  (since the external SD is first drive now!
sudo vi /media/D:/boot/grub/menu.lst

4. reboot, gives me the Boot menu from the SD card and the path is correct, Ubuntu boots!


Second test:
Reboot with removed SD card - Xandros comes up

Third test:
Reboot with inserted SD card on EeePC 1000  -  Ubuntu comes up


We have done it! Thank you again!


Now one problem remains to solve:
How can I clone the SD card, so that it is bootable?


bye

Ronald

---

### Post by falcon61102 on 2008-09-05
Glad that you figured it out.  

And yeah, you should be able to clone the drive and it will boot up.

Sorry for disappearing for a while, trying to fix someone's computer and it wasn't working so well for a while.

---

### Post by ELMIT on 2008-09-05
I used to clone the SD card:

sudo dd if=/dev/sdc of=/dev/sdd

It is VERY slow. The 8 GB SD card took me 4977.67 seconds (1.6 MB/s)

Is there a faster way?
The SD card is only used with 4 GB and the rest is just a formated empty space.


The cloned card worked right away. Plug in and boot, ...


bye

R.

---

### Post by falcon61102 on 2008-09-05
There are a couple utilities out there for cloning and imaging but so speed up a dd copy, you can specify bit size by using "bs=128" at the end of the string.  That will make it copy 128 bytes at a time instead of 1.

---

### Post by ELMIT on 2008-09-05
Thanks, will use the bs=128 next time, ... 

BTW, how would I clone (not sure if you can say still clone then), if I want to move from an 8Gb SD card to a 16GB SD card? dd would not do anymore the trick, since it would stop after 8Gb.

---

### Post by falcon61102 on 2008-09-05
I've heard that clonezilla works well for doing that, but the dd command should still work.  You just need to remember to resize the partition afterwards and when you do that, the UUID for that partition will change and you need to update that the fstab and GRUB.

---

