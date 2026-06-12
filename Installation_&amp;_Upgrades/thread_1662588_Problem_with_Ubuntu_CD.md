---
title: "Problem with Ubuntu CD"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by issacnewton on 2011-01-08
Hi

I just bought a new Toshiba Satellite C650D which has AMD processor. For some rescuing, I wanted to put ubuntu live CD. Ubuntu starts with some screen but then it converts to text mode and just sit there. I have checked md5sum of the iso file I got , before burning it on the CD. After burning the image, I also checked the directory structure on the iso file and the CD. They are fine. Currently I am writing this from XP. 
Please help, how do I use Ubuntu Live CD.

For burning, I used infrarecorder with 'Burn Image' option

I had installed debian and win xp with the same CD , so I can't see the problem with the CD.

Anyway, I tried doing this with differernt CD and the same problem appears.

 The CD's are memorex
CD-RW 700 MB 4X multi speed.

And I don't get the ubuntu boot screen at all. Some screen with ubuntu symbol appears and then text mode with some information about the hardware and it hangs there.

thanks

---

### Post by lift_test on 2011-01-08
How long do you wait?  It takes about 4-5 minutes to load the Live CD on my machine.

---

### Post by issacnewton on 2011-01-08
I waited like 10 minutes...

---

### Post by Rubi1200 on 2011-01-08
Hi and welcome to the forums :)

What graphics card do you have installed?

---

### Post by issacnewton on 2011-01-08
Hi, this is a new laptop and I have installed xp on this. Before xp I did install debian. But XP installation erased MBR and I can't access debian now . So I want to use Ubuntu Live CD to reinstall grub. Now Toshiba doesn't support XP anymore, so I was told by Toshiba Service Center , here in Mumbai. So I have some generic graphics driver. I don't have the driver required by the Toshiba. They want me to upgrade to win 7.

  So, short answer is , I don't know which graphics card.

---

### Post by Rubi1200 on 2011-01-08
A quick Google search tells me it is likely an ATI Radeon card.

You could try booting the CD using nomodeset or radeon.modeset=1

If you get this to work, post the results of the boot info script linked at the bottom of my post.

Perhaps we can find a way to see if we can rescue your Debian install.

---

### Post by issacnewton on 2011-01-08
Hi Rubi

How do I boot CD using nomodeset or radeon.modeset=1 ?

---

### Post by Rubi1200 on 2011-01-09
As the CD is booting, press F6 to see the boot options. There is one there for nomodeset. Highlight it and then Enter to continue.

---

### Post by issacnewton on 2011-01-09
> **Rubi1200 said:**
> As the CD is booting, press F6 to see the boot options. There is one there for nomodeset. Highlight it and then Enter to continue.

I could go to the screen with options varying from F1 to F10 after pressing F6 key. But there was no 'nomodest' option anywhere.
    Anyway, I came to the main screen and pressed 'Try Ubuntu'.
after that I got the same old text mode screen and it hanged there. 
I have taken pics of the hang screen with my camera.  I am attaching them here. May be you can see something.

thanks

---

### Post by Rubi1200 on 2011-01-09
Okay, let's try again.

As the CD boots do you hit Enter and see the choose language and try Ubuntu option?

If yes, hit F6 and then Esc to see the boot line. It will look something like this:
>  **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Use the arrow key to move the cursor back and remove quiet splash.

Add either nomodeset or noacpi (you can also try both at the same time, but I would try each one to see what works).

The line should then look like this:
>  **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Then hit Enter to boot.

If this gets you in, then we can take it to the next step.

Good luck!

---

### Post by issacnewton on 2011-01-09
few more pics during the same time........

the last one is after pressing F6 key again. I don't see nomodeset
option there.

---

### Post by issacnewton on 2011-01-09
> **Rubi1200 said:**
> Okay, let's try again.

As the CD boots do you hit Enter and see the choose language and try Ubuntu option?

If yes, hit F6 and then Esc to see the boot line. It will look something like this:


Use the arrow key to move the cursor back and remove quiet splash.

Add either nomodeset or noacpi (you can also try both at the same time, but I would try each one to see what works).

The line should then look like this:


Then hit Enter to boot.

If this gets you in, then we can take it to the next step.

Good luck!

I did as you said, and this time I think I got that option
'nomodeset'

:popcorn:
:popcorn:

---

### Post by Rubi1200 on 2011-01-09
So now you can choose that option with Enter and then boot. 

If it doesn't work, then try the other option I mentioned. 

Sometimes with these graphics related issues a bit of detective work is needed to figure out which options works best with your hardware.

---

### Post by issacnewton on 2011-01-09
Hi Rubi,

I did the way you said. With both 'nomodeset' and 'noacpi' , when I enter to boot , I again get the text screens which I posted earlier.

---

### Post by issacnewton on 2011-01-09
Hi, 

I rebooted the laptop and this time, I checked the options 'nomodeset' and 
'acpi=off'(check pic in # 12). The 'x' sign appeared in front of them. I then pressed 'ESc' and this particular window disappeared and I then hit enter with 'quiet splash --' there. Slowly ubuntu booted and now I am in Ubuntu (not installed). So I open the terminal and I will try to run that script you said. How do I access my USB stick where I have saved that script ?

---

### Post by issacnewton on 2011-01-09
> **issacnewton said:**
> Hi, 

I rebooted the laptop and this time, I checked the options 'nomodeset' and 
'acpi=off'(check pic in # 12). The 'x' sign appeared in front of them. I then pressed 'ESc' and this particular window disappeared and I then hit enter with 'quiet splash --' there. Slowly ubuntu booted and now I am in Ubuntu (not installed). So I open the terminal and I will try to run that script you said. How do I access my USB stick where I have saved that script ?

Hi Rubi, 

I could access the USB and ran the script you said. I am posting the RESULTS.txt here.

```
                Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000 MB, 1000341504 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,953,791     1,953,729   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,124,094    78,124,032   7 HPFS/NTFS
/dev/sdb2          78,124,095    85,931,684     7,807,590   5 Extended
/dev/sdb5          78,124,158    85,931,684     7,807,527  82 Linux swap / Solaris
/dev/sdb3          85,931,685   115,234,244    29,302,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        47D6-2A9A                              vfat
/dev/sda: PTTYPE="dos"
/dev/sdb1        3420607B20604648                       ntfs
/dev/sdb2: PTTYPE="dos"
/dev/sdb3        e5c2cdf8-d9f5-404b-9e5d-5780bd111be5   ext3       Linux
/dev/sdb5                                               swap
/dev/sdb: PTTYPE="dos"
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/47D6-2A9A         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb3/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda3 ro

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda3 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sdb3: Location of files loaded by Grub: ===================


  58.5GB: boot/grub/menu.lst
  58.6GB: boot/grub/stage2
  58.5GB: boot/initrd.img-2.6.26-2-686
  58.5GB: boot/initrd.img-2.6.26-2-686.bak
  58.6GB: boot/vmlinuz-2.6.26-2-686
  58.5GB: initrd.img
  58.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc

```

I had to convert the text files from Linux to DOS format.

---

### Post by Rubi1200 on 2011-01-09
Thanks for the results and good that you finally got in!

Well, the Debian install seems to still be there. The problem is that it uses GRUB-legacy (the older version of GRUB) and I have no experience with reinstalling GRUB in that version.

I also wonder if it is a good idea to try installing Ubuntu since you had so many difficulties just getting the CD to work.

Let me find some information for you on how to get the Debian install back up and running and I will post back as soon as I can.

---

