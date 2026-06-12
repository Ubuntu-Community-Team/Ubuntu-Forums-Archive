---
title: "Computer says &quot;Grub loading&quot; then restarts"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by arcmandak on 2010-04-07
I know this is an issue that has been brought up before and the solution I found is to recover Grub through the live CD 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) 

However, this problem has occurred multiple times for me now. First time I thought it was just a freak error but it's happened multiple times within a short period of time (couple times this week) so I just wanted to get input on what's causing this and how I can fix it permanently. I've recently installed Ubuntu and I'm dual booting Ubuntu 9.10/Windows 7 Ultimate 64bit. If there's any other info you guys need, I can try to provide it (I'm still relatively new to linux in general).

Any input would be appreciated!

---

### Post by oldfred on 2010-04-07
Is this a problem just after being in windows? There are some windows software that writes hidden info into the boot sector and messes up grub.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

---

### Post by arcmandak on 2010-04-07
Yes, it's a problem after being in windows. I'll be in Windows playing a game or something and then shutdown for the night. Next morning Grub won't load. 

I'll try some of the solutions that you posted and we'll see if I have to come back in 2 days to recover Grub again =).

---

### Post by arcmandak on 2010-04-07
> **oldfred said:**
> Is this a problem just after being in windows? There are some windows software that writes hidden info into the boot sector and messes up grub.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
So I tried to use solution 2 from your first link (revert to legacy grub) and now nothing works =(. I followed all the instructions and did every step other than the last "if Windows is  not on the boot drive, that is if Y is not zero,you also need the map line:" step.

Now after the initial screen there isn't even a "Grub loading", it just becomes a blank screen that doesn't do anything. I went into the bios and I changed to boot off of CD to try the Ubuntu CD but even that doesn't boot. What can I do?

---

### Post by oldfred on 2010-04-07
Reinstalling grub would have nothing to do with BIOS and being able to boot from CD.

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by arcmandak on 2010-04-07
Hi oldfred,

Currently my computer won't even boot past the BIOS screen (as in after the BIOS screen it just goes to a blank screen). This occurred right after I tried to install grub =/.

---

### Post by oldfred on 2010-04-07
If it is past BIOS it could be the grub in the MBR problem, but you still should be able to boot the CD either with f12 or whatever key your BIOS says or in BIOS set CD/DVD as first boot device.

---

### Post by arcmandak on 2010-04-07
I can't boot from the CD. I went into the BIOS to set CD/DVD as the first option and I still get the blank screen after the initial BIOS screen.

---

### Post by oldfred on 2010-04-07
It has to still be booting from the hard drive. Did a connection come loose or is the CD now defective. It has to be a bootable CD, or it will just go to the hard drive and give you the error.

---

### Post by arcmandak on 2010-04-07
Ah, eventually I got it to boot off of the CD eventually (I went to the BIOS and I went to something like "Revert to Default Settings" and then things started to work again)

Now everything works except I can't get into Windows 7. I just need to edit the menu.lst correctly.

Edit: I ran the script you gave me and here are the results

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 499784162 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99aa1f29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   499,213,171   468,411,252   7 HPFS/NTFS
/dev/sda4         499,219,875   625,137,344   125,917,470   5 Extended
/dev/sda5         499,219,938   619,916,219   120,696,282  83 Linux
/dev/sda6         619,916,283   625,137,344     5,221,062  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda3        9670C1E370C1C9E7                       ntfs       OS                            
/dev/sda5        15b1ab4f-6738-4355-9124-9a6f4c3b8819   ext4                                     
/dev/sda6        0d509719-4f7e-409d-bb29-ef486b0116bd   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
# kopt=root=UUID=15b1ab4f-6738-4355-9124-9a6f4c3b8819 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=15b1ab4f-6738-4355-9124-9a6f4c3b8819

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
uuid        15b1ab4f-6738-4355-9124-9a6f4c3b8819
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=15b1ab4f-6738-4355-9124-9a6f4c3b8819 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        15b1ab4f-6738-4355-9124-9a6f4c3b8819
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=15b1ab4f-6738-4355-9124-9a6f4c3b8819 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        15b1ab4f-6738-4355-9124-9a6f4c3b8819
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=15b1ab4f-6738-4355-9124-9a6f4c3b8819 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        15b1ab4f-6738-4355-9124-9a6f4c3b8819
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=15b1ab4f-6738-4355-9124-9a6f4c3b8819 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        15b1ab4f-6738-4355-9124-9a6f4c3b8819
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
title        Windows 7 Ultimate
rootnoverify (hdY,Z)
chainloader +1

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
UUID=15b1ab4f-6738-4355-9124-9a6f4c3b8819 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0d509719-4f7e-409d-bb29-ef486b0116bd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 259.1GB: boot/grub/menu.lst
 255.8GB: boot/grub/stage2
 256.1GB: boot/initrd.img-2.6.31-14-generic
 256.4GB: boot/initrd.img-2.6.31-20-generic
 256.1GB: boot/vmlinuz-2.6.31-14-generic
 256.2GB: boot/vmlinuz-2.6.31-20-generic
 256.4GB: initrd.img
 256.1GB: initrd.img.old
 256.2GB: vmlinuz
 256.1GB: vmlinuz.old


---

### Post by oldfred on 2010-04-08
You installed grub to the windows boot partition sda2. That wipes windows and even the script cannot read it. You only have part of the windows boot still in the main windows partition sda3.

You need to run the windows recovery disk repairs. I do not know if it will see the sda2 partition but it does have to boot flag, so it may work.

If you run the fixmbr command you will have to reinstall grub. 

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

In case you have to reinstall grub, you still have grub legacy 0.97:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by arcmandak on 2010-04-10
Hey oldfred,

I followed your directions and they worked! Luckily I was able to recover the MBR, everything works fine now. Thanks!

---

### Post by oldfred on 2010-04-10
Glad you got it working. 

Post it as solved so others searching similar issues will see one way to solve their issues.

---

