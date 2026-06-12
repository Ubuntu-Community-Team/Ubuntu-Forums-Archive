---
title: "Grub problem following Error 15: File not found"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by moooping on 2010-05-21
Greetings - I spent most parts of the day trying to solve a Grub problem following an upgrade to 10.04. 

My problem now is: After booting my laptop, Ubuntu doesn't load and i'm stuck in a GRUB command prompt and not sure what to do. If i type "boot" I get "error: no loaded kernel"

Here is how I got there:
1. I ran 9.1 healthily until I was prompted to do an upgrade. I ran the upgrade but some packages weren't authenticated so I ran a partial upgrade. 
2. I reboot but I'm faced with "Error 15: File not found". After some research and going through the forums, I thought I found the solution by following these instructions to copy the GRUB files from the Live CD  ([https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"))
3. Once I completed this, I'm now stuck at a grub> prompt when rebooting (the error 15 has disappeared). (the screen header informs me i'm dealing with "GNU GRUB version 1.98-1ubuntu5"

Any thoughts on what I might have done wrong? From my reading today, I might have installed GRUB2 (even though Grub legacy would have been appropriate?). What is the best way out?  I'm not sure. I'm a relative novice so not too comfortable with shell commands. So please be patient with me.

Thanks for all your help!!

---

### Post by kansasnoob on 2010-05-21
Would you please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by moooping on 2010-05-21
Many thanks - i'm on the case. Watch this space for updates.

---

### Post by moooping on 2010-05-21
This is what I get. Cheers!

```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 591572634 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2          20,973,568   118,351,863    97,378,296   7 HPFS/NTFS
/dev/sda3         329,444,955   625,137,344   295,692,390   5 Extended
/dev/sda5         329,445,018   613,056,464   283,611,447  83 Linux
/dev/sda6         613,056,528   625,137,344    12,080,817  82 Linux swap / Solaris
/dev/sda4         323,151,872   329,443,463     6,291,592   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        464A94DB4A94C957                       ntfs       RECOVERY                      
/dev/sda2        B27096C570969029                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        E4745F5D745F3212                       ntfs                                     
/dev/sda5        853de0ae-35a6-4c03-9b56-d8f03f8ae730   ext3                                     
/dev/sda6        54a872b6-b66a-4ec8-8dbf-da210b6cdfc4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=853de0ae-35a6-4c03-9b56-d8f03f8ae730

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-18-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-18-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        853de0ae-35a6-4c03-9b56-d8f03f8ae730
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=853de0ae-35a6-4c03-9b56-d8f03f8ae730 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=54a872b6-b66a-4ec8-8dbf-da210b6cdfc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

localhost:/wuala /home/matthias/wuala/direct nfs defaults,users,noauto,rsize=8192,wsize=8192,timeo=60,acregmin=10,noac,intr,nolock,soft

=================== sda5: Location of files loaded by Grub: ===================


 302.8GB: boot/grub/core.img
 302.9GB: boot/grub/menu.lst
 302.8GB: boot/grub/stage2



```

---

### Post by darkod on 2010-05-21
Uhhh... quite a mess.
OK, one thing at a time.

As you can notice in the results towards the top where the partitions are listed, you still have 9.10, I guess because the upgrade didn't go the whole way.

You are right, you should have reinstalled grub1, not grub2. Get a 9.04 cd, boot into live mode with it, and in terminal do:

sudo grub
root (hd0,4)
setup (hd0)
quit
sudo reboot

That should show you your grub1 menu at boot. Select ubuntu to boot into, and I would do two things:

1. Open Gparted and remove the boot flag (with right click, flags) from /dev/sda1 and put it on /dev/sda2. Your Vista is /dev/sda2 and it should have the boot flag.

2. Open the menu.lst with:

sudo gedit /boot/grub/menu.lst

and scroll to the bottom. The last entry, for (hd0,1) is your Vista. The previous one, for (hd0,0) is your recovery partition. Change the name of the entry in Recovery or similar, so you don't select it by mistake. At this moment both entries are identical in menu.lst.

PS. Also as you can see, inside your Vista you have wubi install, or traces from it. If you are using a full install of ubuntu, why is wubi still in vista? Why don't you remove it to free the space taken by it? As I said, unless there are only traces from not fully removed wubi.

---

### Post by moooping on 2010-05-21
Champ!

I will have to download and burn a new live CD so might be a while, but your instructions seem clear. Many thanks.

Not sure what  "Gparted" is and how to "remove the boot flag"  - but I will try to figure this one out when I get to it.

As for Vista - I got my laptop with Vista preinstalled but never used it - the first thing I did was to install Ubuntu so I'm happy to lose Vista completely - just never figured out how to. Maybe that's my next project once I have gotten myself out of this mess.

Many thanks again! I will post progress here.

Cheers!

---

### Post by darkod on 2010-05-21
Gparted is Gnome Partition Editor, a very good tools for editing partitions, creating, deleting, etc. In live mode, it's in System-Administration.

But once you install, it's not in the default programs, you need to install it with:

sudo apt-get install gparted

When you open it, you'll figure it out. :) One thing about Gparted: any change you make is not executed until you hit the big green button in the toolbar. That gives you option to cancel something if you made a mistake. You simply don't hit the green button and nothing is executed. :)
But when you want it executed, you need to hit the button. If you just close the program, nothing is done.

---

### Post by moooping on 2010-05-21
Thanks - looking forward to hitting that green button!:)

But first, I need to download the new image - currently at 25% and internet is slow!

---

### Post by moooping on 2010-05-21
OK - so I've run the sudo grub procedure which went well. I then rebooted but when I choose to boot into Ubuntu 9.10 I'm back at my old "Error 15: File not found" error. Any thoughts on how to progress? Do you need any additional info?

---

### Post by kansasnoob on 2010-05-21
> **darkod said:**
> Uhhh... quite a mess.
OK, one thing at a time.

As you can notice in the results towards the top where the partitions are listed, you still have 9.10, I guess because the upgrade didn't go the whole way.

You are right, you should have reinstalled grub1, not grub2. Get a 9.04 cd, boot into live mode with it, and in terminal do:

sudo grub
root (hd0,4)
setup (hd0)
quit
sudo reboot

That should show you your grub1 menu at boot. Select ubuntu to boot into, and I would do two things:

1. Open Gparted and remove the boot flag (with right click, flags) from /dev/sda1 and put it on /dev/sda2. Your Vista is /dev/sda2 and it should have the boot flag.

2. Open the menu.lst with:

sudo gedit /boot/grub/menu.lst

and scroll to the bottom. The last entry, for (hd0,1) is your Vista. The previous one, for (hd0,0) is your recovery partition. Change the name of the entry in Recovery or similar, so you don't select it by mistake. At this moment both entries are identical in menu.lst.

PS. Also as you can see, inside your Vista you have wubi install, or traces from it. If you are using a full install of ubuntu, why is wubi still in vista? Why don't you remove it to free the space taken by it? As I said, unless there are only traces from not fully removed wubi.

@ Darkod & other grub aficionados only! While my DSL was down I typed up some stuff to address the issue of needing a specific *buntu CD for legacy grub and/or Grub 2:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

I'd appreciate your feedback. If it sucks I want to know :)

---

### Post by darkod on 2010-05-21
> **moooping said:**
> OK - so I've run the sudo grub procedure which went well. I then rebooted but when I choose to boot into Ubuntu 9.10 I'm back at my old "Error 15: File not found" error. Any thoughts on how to progress? Do you need any additional info?

Hmmm, the files are there. But not sure where grub1 expects them. Maybe because of the broken upgrade, it's messed up too.

With that command root (hd0,4) it should have located the files correctly, that was the point of the command.

---

### Post by moooping on 2010-05-21
This thread ([http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)) describes a similar procedure as darkod described in #5 above (i.e.```
sudo grub
root (hd0,4)
setup (hd0)
quit
sudo reboot
```

It is also recommended to proceed like this:
```


1. Boot with any live CD (I've done it with Knoppix 3.x and Ubuntu)
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hdb ubuntu if  you have two disks)
4. chroot the mounted partition (chroot ubuntu)
5. grub-install /dev/hda [1]
5. Exit the shell
6. Reboot

[1] Important: If you are multi-booting with Windows, make sure you do  NOT install the MBR on the active partition (say /dev/hda1) but on the  drive (/dev/hda). At least with Windows XP, you will have to re-install  it (FIXMBR/FIXBOOT won't work).

```Is this a potential way out of my troubles?

---

### Post by kansasnoob on 2010-05-21
@ moooping,

I want you to try something please :)

Post the output from terminal of all this (please copy-n-paste):

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
lsb_release -a
```

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Let's see if my new experiment works :)

BTW, that's not intended to fix anything! We're simply gathering info!

---

### Post by darkod on 2010-05-21
Listen to kansas, I was waiting for the cavalry. :)

---

### Post by kansasnoob on 2010-05-21
> **darkod said:**
> Listen to kansas, I was waiting for the cavalry. :)

Well, I've seen some odd things recently where it appears that we have legacy grub and/or grub2 but we end up with what we didn't expect. So I'm looking for a solution.

Hopefully we'll come up with something that causes us to spend less time chasing our own tails :)

Oh, and you're my cavalry. You and several others. It's always good to have several pairs of eyes looking.

---

### Post by moooping on 2010-05-21
Ok - lets go. This is where I got to
```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

root@ubuntu:/# lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

root@ubuntu:/# grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: apt-get install <selected package>
grub-install: command not found
root@ubuntu:/# ^C
root@ubuntu:/# 



```Looks like there is a poroblem with grub-install? Should I just continue?

---

### Post by moooping on 2010-05-21
For completeness this is how the experiment ends:
```

root@ubuntu:/# exit
exit

ubuntu@ubuntu:~$ sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt

ubuntu@ubuntu:~$ 


```

---

### Post by kansasnoob on 2010-05-21
I've never seen this:

> root@ubuntu:/# lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

Here's my Karmic:

> root@lance-desktop:/# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic


So I'm totally puzzled :confused:

What's this arch stuff?

Give me a few minutes to try and research :(

---

### Post by kansasnoob on 2010-05-21
On account of that "arch-kernel" or whatever I need you try this again. First of all, why? Well that old command: : "grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4" is not a true script. It's just commands tied together with "space&&space" so if one part fails, the rest fails, and whatever freakin' kernel you have doesn't support the command "grub-install -v" so now post the output of this:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

---

### Post by moooping on 2010-05-21
Cool - this is my output

> 
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
> 
root@ubuntu:/# aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
Package: grub
State: not installed
Version: 0.97-29ubuntu59
Priority: optional
Package: grub-pc
State: not installed
Version: 1.97~beta4-1ubuntu5
Priority: optional
Package: grub-common
State: installed; will be removed because nothing depends on it
Automatically installed: yes
Version: 1.97~beta4-1ubuntu5
Package: os-prober
State: installed; will be removed because nothing depends on it
Automatically installed: yes
Version: 1.35
root@ubuntu:/# exit^C
> 
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 
> 
ubuntu@ubuntu:~$ sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
ubuntu@ubuntu:~$ 

It seems to have worked fine?

---

### Post by kansasnoob on 2010-05-21
> **moooping said:**
> Cool - this is my output

It seems to have worked fine?

Well, it shows that neither "grub" nor "grub-pc" is installed.

> Package: grub
State: **[COLOR="Red"]not installed[/COLOR]**
Version: 0.97-29ubuntu59
Priority: optional
Package: grub-pc
State: **[COLOR="Red"]not installed[/COLOR]**
Version: 1.97~beta4-1ubuntu5
Priority: optional

So give me a few more minutes to parse this.

In the meanwhile look at this just to get an idea what we're going to do next:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Something I wished I'd asked for and didn't was the output of:

```
uname -a

```

while in the chroot.

---

### Post by moooping on 2010-05-21
Thanks for your help, kansas!  I will look at the other discussion. How do I return the output of "uname -a"? Happy to provide this.

---

### Post by kansasnoob on 2010-05-21
Going back to the beginning you said:

> Greetings - I spent most parts of the day trying to solve a Grub problem following an upgrade to 10.04.


But the Boot Info Script shows this:

> =================== sda5: Location of files loaded by Grub: ===================


 302.8GB: boot/grub/core.img
 302.9GB: boot/grub/menu.lst
 302.8GB: boot/grub/stage2

Compare that to mine:

> =================== sda2: Location of files loaded by Grub: ===================


  22.1GB: boot/grub/core.img
  22.1GB: boot/grub/grub.cfg
  22.2GB: boot/initrd.img-2.6.32-22-generic
  22.2GB: boot/vmlinuz-2.6.32-22-generic
  22.2GB: initrd.img
  22.2GB: vmlinuz


No kernel image at all! In other words a totally failed upgrade but we'll try something, just give me several minutes.

---

### Post by moooping on 2010-05-21
OK - this sounds like something went very wrong. Maybe related to the fact that I had to run the partial upgrade?  Do you think I have a very big problem and I should just say goodbye to my fails and reinstall?

---

### Post by kansasnoob on 2010-05-21
First of all browse this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Especially the part about:

**Note: the commands below are just a string of commands connected by "space&&space" but if one part of the string fails it stops the whole process so if you encounter any failure message look at the list of individual commands below!**

Note: you're my eyes here, I can only know what's up on your end by seeing the FULL terminal output!

If you didn't properly "unmount" from the previous operations the whole darn thing could fail right out of the gate! It might be best to reboot! then from the Live CD:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Note: feel free to repeat any of the following commands in no specific order!

```
apt-get clean
```

```
apt-get update
```

```
dpkg --configure -a
```

```
apt-get -f install
```

```
apt-get dist-upgrade
```

Note: Any errors shown might give us some direction where to go next!

Commands helpful regarding disc usage/free space:

```
df -H
```

```
du -sh /*
```

Only if package management seems OK (takes an hour or more to run):

```
sudo dpkg-reconfigure -phigh -a
```

And if all seems well remember to exit and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

---

### Post by kansasnoob on 2010-05-21
> **moooping said:**
> OK - this sounds like something went very wrong. Maybe related to the fact that I had to run the partial upgrade?  Do you think I have a very big problem and I should just say goodbye to my fails and reinstall?

Partial upgrade!!!!!!!!!!!!!!!! During a distribution upgrade?

IMHO it's always worth a try to rescue. It's probably faster to reinstall.

---

### Post by moooping on 2010-05-21
Many thanks for your continued help! 

This is the full terminal output up until du -sh /*

> 
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
root@ubuntu:/# apt-get clean
root@ubuntu:/# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_US                 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Get:4 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [1,032B]                          
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_US                          
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports Release.gpg                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/restricted Translation-en_US 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/main Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/universe Translation-en_US   
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release.gpg [189B]          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Translation-en_US        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Translation-en_US    
Get:7 [http://ftp.debian.org](http://ftp.debian.org) etch Release [67.8kB]                              
Get:8 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports Release                      
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release [44.1kB]            
Get:10 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                            
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Hit [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [99.8kB]       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources             
Get:12 [http://dl.google.com](http://dl.google.com) stable/main Packages [920B]                        
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [11.0kB]                  
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/restricted Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/main Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/multiverse Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/universe Packages           
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Packages [14B] 
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Packages [103kB]     
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [29.5kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [54.5kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [9,458B]    
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]    
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Packages [14B]  
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Packages [19.0kB]
Fetched 488kB in 3s (130kB/s)                           
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
root@ubuntu:/# dpkg --configure -a
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xorg-docs-core linux-headers-2.6.31-14 libnfsidmap2 ttf-wqy-zenhei
  libcupscgi1 libuser-perl apport-symptoms wine-gecko libwvstreams4.6-base
  nvidia-settings libsctp1 libcupsmime1 libcouchdb-glib-1.0-1
  libcompress-bzip2-perl libcarp-clan-perl pavucontrol libgnome-bluetooth7
  dnsmasq-base libpolkit-gtk-1-0 python-couchdb librpcsecgss3 python-avahi
  obexd-client libcupsdriver1 libjson-glib-1.0-0 libdate-manip-perl
  lksctp-tools os-prober libzip1 libfile-slurp-perl tcl8.4 paman tk8.4
  libgconfmm-2.6-1c2 libuniconf4.6 libwvstreams4.6-extras odt2txt winbind
  grub-common libgssglue1 linux-headers-2.6.31-14-generic pavumeter
  libavahi-core6 libglademm-2.4-1c2a modemmanager libbit-vector-perl
  libntfs-3g54
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  anacron aptdaemon apturl contact-lookup-applet deskbar-applet empathy
  evolution evolution-dev evolution-exchange evolution-indicator
  evolution-plugins evolution-rss f-spot gdebi gdesklets gksu gnome-about
  gnome-applets gnome-codec-install gnome-control-center gnome-keyring
  gnome-netstatus-applet gnome-orca gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-session-bin gnome-spell gnomebaker gstreamer0.10-gnomevfs
  indicator-applet indicator-messages jockey-common jockey-gtk kde-l10n-de
  kde-l10n-engb kde-l10n-es kde-l10n-fr kdebase-runtime
  kdebase-runtime-bin-kde4 kdelibs-bin kdelibs5 khelpcenter4 kmix
  libbonoboui2-dev libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-dev
  libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomepanel2.24-cil
  libgnomeui-0 libgnomeui-dev libgnomevfs2-bin libgnomevfs2-dev
  libgnomevfs2-extra libgtkhtml3.14-dev libknotificationitem1 libplasma3
  libpolkit-gtk-1-0 logrotate nautilus-share policykit python-aptdaemon
  python-aptdaemon-gtk python-gnome2 python-gnome2-desktop python-gnomeapplet
  python-pyatspi screen-resolution-extra software-center
  software-properties-gtk system-config-printer-gnome tomboy totem-mozilla
  ubufox ubuntu-system-service ubuntuzilla update-manager update-notifier
  usb-creator usb-creator-gtk xulrunner-1.9.1-gnome-support
The following packages have been kept back:
  devede
The following packages will be upgraded:
  libpq5
1 upgraded, 0 newly installed, 87 to remove and 1 not upgraded.
Need to get 80.5kB of archives.
After this operation, 308MB disk space will be freed.
Do you want to continue [Y/n]? z
Abort.
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  anacron aptdaemon apturl contact-lookup-applet deskbar-applet empathy
  evolution evolution-dev evolution-exchange evolution-indicator
  evolution-plugins evolution-rss f-spot gdebi gdesklets gksu gnome-about
  gnome-applets gnome-codec-install gnome-control-center gnome-keyring
  gnome-netstatus-applet gnome-orca gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-session-bin gnome-spell gnomebaker gstreamer0.10-gnomevfs
  indicator-applet indicator-messages jockey-common jockey-gtk kde-l10n-de
  kde-l10n-engb kde-l10n-es kde-l10n-fr kdebase-runtime
  kdebase-runtime-bin-kde4 kdelibs-bin kdelibs5 khelpcenter4 kmix
  libbonoboui2-dev libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-dev
  libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomepanel2.24-cil
  libgnomeui-0 libgnomeui-dev libgnomevfs2-bin libgnomevfs2-dev
  libgnomevfs2-extra libgtkhtml3.14-dev libknotificationitem1 libplasma3
  libpolkit-gtk-1-0 logrotate nautilus-share policykit python-aptdaemon
  python-aptdaemon-gtk python-gnome2 python-gnome2-desktop python-gnomeapplet
  python-pyatspi screen-resolution-extra software-center
  software-properties-gtk system-config-printer-gnome tomboy totem-mozilla
  ubufox ubuntu-system-service ubuntuzilla update-manager update-notifier
  usb-creator usb-creator-gtk xulrunner-1.9.1-gnome-support
The following packages have been kept back:
  devede
The following packages will be upgraded:
  libpq5
1 upgraded, 0 newly installed, 87 to remove and 1 not upgraded.
Need to get 80.5kB of archives.
After this operation, 308MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main libpq5 8.4.4-0ubuntu9.10 [80.5kB]
Fetched 80.5kB in 5s (14.1kB/s)       
(Reading database ... 286933 files and directories currently installed.)
Removing logrotate ...
Removing anacron ...
Removing software-center ...
Removing aptdaemon ...
Removing ubufox ...
Removing apturl ...
Removing contact-lookup-applet ...
Removing deskbar-applet ...
Removing empathy ...
Removing evolution-plugins ...
Removing evolution-indicator ...
Removing evolution-dev ...
Removing evolution-rss ...
Removing evolution-exchange ...
Removing evolution ...
Removing f-spot ...
Removing ubuntuzilla ...
Removing gdebi ...
Removing gdesklets ...
Removing update-notifier ...
Removing update-manager ...
Removing gnome-netstatus-applet ...
Removing software-properties-gtk ...
Removing gnome-codec-install ...
Removing gksu ...
Removing gnome-session ...
Removing gnome-applets ...
Removing gnome-keyring ...
Removing gnome-orca ...
Removing gnome-pilot-conduits ...
Removing gnome-pilot ...
Removing gnome-power-manager ...
Removing gnome-screensaver ...
Removing gnome-session-bin ...
Removing gnome-spell ...
Removing gnomebaker ...
Removing gstreamer0.10-gnomevfs ...
Removing jockey-gtk ...
Removing jockey-common ...
Removing kde-l10n-de ...
Removing kde-l10n-engb ...
Removing kde-l10n-es ...
Removing kde-l10n-fr ...
Removing kmix ...
Removing khelpcenter4 ...
Removing libgtkhtml3.14-dev ...
Removing libgnomeui-dev ...
Removing libbonoboui2-dev ...
Removing libgnome-pilot2 ...
Removing tomboy ...
Removing libgnomepanel2.24-cil ...
Removing libgnomepanel2.24-cil from Mono
Removing libgnome2.24-cil ...
Removing libgnome2.24-cil from Mono
Removing libgnome-vfs2.0-cil ...
Removing libgnome-vfs2.0-cil from Mono
Removing libgnome2-dev ...
Removing libgnome2-perl ...
Removing libgnome2-vfs-perl ...
Removing python-gnome2-desktop ...
Removing python-gnomeapplet ...
Removing usb-creator ...
Removing usb-creator-gtk ...
Removing system-config-printer-gnome ...
Removing python-pyatspi ...
Removing nautilus-share ...
Removing libgnomevfs2-bin ...
Removing libgnomevfs2-dev ...
Removing libgnomevfs2-extra ...
Removing libpolkit-gtk-1-0 ...
Removing policykit ...
Removing python-aptdaemon-gtk ...
Removing python-aptdaemon ...
Removing screen-resolution-extra ...
Removing totem-mozilla ...
Removing xulrunner-1.9.1-gnome-support ...
Removing indicator-applet ...
Removing indicator-messages ...
Removing gnome-panel ...
Removing gnome-about ...
Removing gnome-control-center ...
Removing python-gnome2 ...
Removing libgnomeui-0 ...
Removing ubuntu-system-service ...
Removing kdebase-runtime ...
Removing kdebase-runtime-bin-kde4 ...
Removing libplasma3 ...
Removing libknotificationitem1 ...
Removing kdelibs5 ...
Removing kdelibs-bin ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for gnome-icon-theme ...
(Reading database ... 271966 files and directories currently installed.)
Preparing to replace libpq5 8.4.3-0ubuntu9.10.1 (using .../libpq5_8.4.4-0ubuntu9.10_i386.deb) ...
Unpacking replacement libpq5 ...
Setting up libpq5 (8.4.4-0ubuntu9.10) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place





---

### Post by moooping on 2010-05-21
And here is the rest, I will continue through your instructions as I dont think we had an error? How do I check your package management point explicitly?

```

**root@ubuntu:/# du -sh /***
5.0M    /bin
2.0M    /boot
0    /cdrom
168K    /dev
17M    /etc
32G    /home
43M    /lib
16K    /lost+found
8.0K    /media
4.0K    /mnt
11M    /op
181M    /opt
du: cannot access `/proc/6452/task/6452/fd/4': No such file or directory
du: cannot access `/proc/6452/task/6452/fdinfo/4': No such file or directory
du: cannot access `/proc/6452/fd/4': No such file or directory
du: cannot access `/proc/6452/fdinfo/4': No such file or directory
0    /proc
199M    /root
6.2M    /sbin
4.0K    /selinux
200K    /srv
0    /sys
96K    /tmp
3.5G    /usr
326M    /var

```

Muchly appreciated!

---

### Post by kansasnoob on 2010-05-21
You had a huge mess to begin with:

> Get:4 [http://ftp.debian.org](http://ftp.debian.org)  etch Release.gpg [1,032B]
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_US 

If you're going to perform a distribution upgrade you should make sure that your package management is in order!

Why did you have a Debian Etch repo?

I'd probably try to save it if it were in front of me, but it's not. The thing is you still have a Karmic sources.list with some other crap and no Lucid at all.

This was somewhat broken before you ever tried to upgrade.

---

### Post by moooping on 2010-05-21
> 
Why did you have a Debian Etch repo?
  

Not sure what this is - I really just thought I should go for the upgrade.
 
> 
 I'd probably try to save it if it were in front of me, but it's not. The thing is you still have a Karmic sources.list with some other crap and no Lucid at all.


Many thanks for trying and staying with me for so long.

Looks like I'm going to have to go for the painful reinstall option. Do you know what the best way to proceed is? Do I have to remove the existing installation or will this automatically be done if I run an install from the live CD?

---

### Post by moooping on 2010-05-21
I should probably wait with the reinstall for a day or so, just in case someone stumbles across this discussion and has  any additional ideas.

Thanks darko and kansas for all the help!

---

### Post by darkod on 2010-05-21
> **moooping said:**
> Not sure what this is - I really just thought I should go for the upgrade.
 


Many thanks for trying and staying with me for so long.

Looks like I'm going to have to go for the painful reinstall option. Do you know what the best way to proceed is? Do I have to remove the existing installation or will this automatically be done if I run an install from the live CD?

I can help with this, lets give kansas a break. :)

I would recommend: boot the live mode again and in Places find your root partition, /dev/sda5, which will probably be called something like 140GB filesystem. Once you open the partition, copy any data you need to external hdd or similar.

Then start the installer, and in step 4 select Manual Partitioning. It will show you a list of your partitions. Select /dev/sda5 and click the Change button at bottom.

Set the filesystem as ext4, tick the format box to get rid of the failed system on it, and select mount point /.
It should automatically pick up the swap partition.

That's it. Continue with the installer steps and you're done. That's how you can use the same partition without too much fuss.

Don't forget to copy all the data you need from it first because it will be gone!!!

---

### Post by moooping on 2010-05-21
Awesome - many thanks Darko. I will give it a break for the moment and tackle the problem again tomorrow morning! Thanks so much!

---

