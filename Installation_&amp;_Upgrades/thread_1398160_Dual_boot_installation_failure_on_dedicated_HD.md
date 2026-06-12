---
title: "Dual boot installation failure on dedicated HD"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by imphil on 2010-02-04
After having tested Ubuttu 9.10 on a VM with Win XP Pro as host and running both Ubuntu 9.10 and 8.04 from a CD/CDR drive I decided to do an installation of 8.04 on a separate HD and import files.

Installation seemed to work OK, but on reboot: no menu was shown to choose OS and the machine booted directly into Windows.

Tried to boot directly from the "Ubuntu" HD in the BIOS boot menu and get the message "MBR error" full stop literally.

The Ubuntu hard drive is no longer recognised in Windows , can't be acessed from the DOS prompt and obviously cannot be reformatted from there.

Just for the record, I'm not totally excluding operator error from the cause!

Anyway, short of getting a new HD, where do I go from here??

Try a new install over the  old one?

tia 

Phil

---

### Post by Leppie on 2010-02-04
hi and welcome to the community,

booting off the livecd, you should be able to re-install grub to the mbr of your drive.
in this case, i'm presuming you installed ubuntu into partition 5 (sda5 in ubuntu). this is how most people set up dual boot the first time. if it is different for you, you will have to amend the sda5 part to whatever partition you installed ubuntu into.
the parts from ## are just comments, so do not type them in the terminal. they're just to explain what's being done.
```
sudo mount /dev/sda5 /mnt  ##mount the ubuntu partition temporarily into /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda  ##re-install grub to the mbr using your ubuntu partition as the root system
```
if you do not receive any errors, try rebooting without the cd.

---

### Post by imphil on 2010-02-04
Thanks for the welcome and your help!:D

I am not too familiar with the nomenclature (drive and partition numbering) and ignorant of the syntax but I will give it a (careful) try.

Will post again if I have difficulties finding my way.

---

### Post by darkod on 2010-02-04
When you say the hdd is no longer recognized in windows, you have to be careful with the statement.
Linux partitions will not be visible in windows My Computer, if you are expecting to see them there. That's normal.
However, the hdd should be visible as device in Disk Management, and even the partition sizes. If the hdd is not seen as present deice at all, that can be a big problem.
Easiest way to open disk management is: windows button + R, type diskmgmt.msc, hit Enter.

---

### Post by imphil on 2010-02-04
OK found the relevant HD disk with GParted, running Ubuntu from a CD. 
The extended Filesystem is called sdc1.

Typing the first line of above code into the terminal  results i an error message to the effect "mnt point does not exist"!

Question is if I can save myself a lot of messing around by formating the drive from GParted and reinstalling.

Darkod I'm not entirely surprised that the HD disc dosen't show in windows which was why I referred to win. Will check.

Was hoping the mature 8.04 release wouldn't give me any problems. LOL

---

### Post by kansasnoob on 2010-02-04
We really should see the output of the Boot Info Script so we're not flying blind (of course you'll have to run it using the Live CD):

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Leppie on 2010-02-04
yes, this would help us a lot with helping you ;)

---

### Post by imphil on 2010-02-04
Here we go. Boot Info file>

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => HP/Gateway is installed in the MBR of /dev/sdb
 => HP/Gateway is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ec44c5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa738484c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *      6,570,585   293,041,664   286,471,080   7 HPFS/NTFS
/dev/sdb2                  63     6,570,584     6,570,522  12 Compaq diagnostics


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ac6adf8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   468,616,049   468,615,987  83 Linux
/dev/sdc2         468,616,050   488,392,064    19,776,015   5 Extended
/dev/sdc5         468,616,113   488,392,064    19,775,952  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        88A8731EA87309C8                       ntfs       Working_Files                 
/dev/sdb1        70C4056BC405353E                       ntfs       VelociRaptor                  
/dev/sdb2        423B-2BDF                              vfat                                     
/dev/sdc1        f1b1db67-0ecb-4108-bcae-d4d3cb80c978   ext3                                     
/dev/sdc5        213b7620-7f2b-4ebd-8b03-73c72987defc   swap                                     
/dev/sdd1        D23C96763C965577                       ntfs       Backups                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /media/Backups           fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f1b1db67-0ecb-4108-bcae-d4d3cb80c978 ro

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=f1b1db67-0ecb-4108-bcae-d4d3cb80c978 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=f1b1db67-0ecb-4108-bcae-d4d3cb80c978 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd2,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows NT/2000/XP
root        (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=f1b1db67-0ecb-4108-bcae-d4d3cb80c978 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=213b7620-7f2b-4ebd-8b03-73c72987defc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


 125.9GB: boot/grub/menu.lst
 125.9GB: boot/grub/stage2
 125.9GB: boot/initrd.img-2.6.24-26-generic
 125.9GB: boot/vmlinuz-2.6.24-26-generic
 125.9GB: initrd.img
 125.9GB: vmlinuz


Hope this looks right.

Thanks!

---

### Post by kansasnoob on 2010-02-04
**Please read this all before beginning and if you have questions ask away!**

OK that tells us a lot. You have four drives total:

> => Grub 0.97 is installed in the MBR of **/dev/sda** and looks on boot drive #3
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> HP/Gateway is installed in the MBR of **/dev/sdb**
=> HP/Gateway is installed in the MBR of **/dev/sdc**
=> Windows is installed in the MBR of **/dev/sdd**

And we can see that Ubuntu installed it's grub to the mbr of sda, but Ubuntu is installed on sdc1.

Windows is installed on sdb1. Drives sda and sdd must be just storage. I see you have an HP Recovery on sdb2.

So challenge #1 is getting Ubuntu to boot. If you can in fact get drive sdc (the 250 GB drive) to boot first in BIOS it should be as easy as setting the BIOS properly and then booting the Ubuntu Live CD and going to the Terminal and opening a grub shell:

```
sudo grub
```

You'll see the prompt change as you go to the grub shell, and if you run:

```
find /boot/grub/stage1
```

You should see "(hd2,0)". That is two,zero! So then:

```
root (hd2,0)
```

```
setup (hd2)
```

You should see:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

So then:

```
quit
```

If you have the BIOS settings correct and I'm right you should be able to boot Ubuntu, but I'm a bit worried about being able to boot Windows.

The current entries are:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Windows NT/2000/XP
root (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

That's mostly right. XP is on sdb1 so (hd1,0) is correct but I think the drive mapping may be a problem. The same is true of the HP Recovery.

I think the mapping in both cases should be changed from:

```
map (hd0) (hd1)
map (hd1) (hd0)
```

To:

```
map (hd1) (hd2)
map (hd2) (hd1)
```

To do that you first want to backup the menu.lst, so after booting into your new Ubuntu:

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_BU
```

Then we'll edit:

```
gksudo gedit /boot/grub/menu.lst
```

And change the above to this (changes in red):

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
[B][COLOR="Red"]map (hd1) (hd2)
map (hd2) (hd1)[/COLOR][/B]
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Windows NT/2000/XP
root (hd1,1)
savedefault
makeactive
[B][COLOR="Red"]map (hd1) (hd2)
map (hd2) (hd1)[/COLOR][/B]
chainloader +1
```

You also may want to "hide" the HP Recovery by adding comments (ie: #) to those lines like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd1) (hd2)
map (hd2) (hd1)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
**[COLOR="Red"]#[/COLOR]**title Windows NT/2000/XP
**[COLOR="Red"]#[/COLOR]**root (hd1,1)
**[COLOR="Red"]#[/COLOR]**savedefault
**[COLOR="Red"]#[/COLOR]**makeactive
**[COLOR="Red"]#[/COLOR]**map (hd1) (hd2)
**[COLOR="Red"]#[/COLOR]**map (hd2) (hd1)
**[COLOR="Red"]#[/COLOR]**chainloader +1
```

Clear as mud????????????

---

### Post by imphil on 2010-02-04
Kansasnoob many thanks for your effort!

I understand the *gist* of the problem. The devil lives in the details.

I will study this carefully tomorrow, its getting close to bed time CET and my head is already spinning. ;)
If I do anything now Ill probably screw up.

Oh!
Windows and apps on one hard drive, files on a second, third given over to Ubuntu, fourth external drive for back ups.

best 

Phil

---

### Post by imphil on 2010-02-05
OK!

Have read the instruction several times.

No problem getting the system to try and boot from the 250GB file fdc.

Booting from a CD and entereing script should be OK with a slight reservation that the non US keyboard mappings availible on the CD seem a bit off for some keys.

Getting Widows to boot is what gives me a some apprehension.
This is also the reason I gave Ubuntu a dedicated disk in the hope that less problems would ensue. 

The PC is mainly a photography workstation.
I run several memory and power hungry photo processing and sorting apps in Windows.
They won't run under a Linux system, short of running them on a VM and my system dosen't have enough clout for that. 
Without the photo apps, Windows would have probably have been out the door long ago!

Bottom line is I would like to get a gut feel for how risky the drive remapping, which I don't understad all that well, would be?

Alternative, less fraught with angst for me ;):

What is to stop me swapping the SATA cables between sda and sdb to get the Windows boot disc adress where Ubuntu wants it, then install Grub in sda via terminal, finished??
Would in that case need help with the script.
Could also format sdc from a CD then let a clea install get the system up? 
Too easy to work?? 

Would appreciate points of view and/or help and please dont hesitate to tell me if I misunderstood something entirely.

---

### Post by imphil on 2010-02-11
I shifted the SATA HD cables just to see what would happen and the dual boot menu worked directly.

Formatted and reinstalled just to be on the safe side and everything seems to be OK, I'm posting from Ubuntu.

So anybody installing a dual boot with Ubuntu on a separate HD, make sure that Windows is booting from the first HD on your system.

Thanks for all your help, without the boot info script and analysis I would never have found out why it didn't work. I am also convinced the scripting would have done the trick as well.

---

