---
title: "Vista missing after upgrading to ubuntu 10.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by darayzins on 2011-05-01
Hi,

I have lost the option to boot Microsoft vista after upgrading to ubuntu 10.04 and need help getting the vista boot option back so that I can use Vista once again. I'm not sure what version of ubuntu I was using previously, but I just followed a prompt in the previous version of ubuntu to update to 10.04. 

I can still access my documents in vista from ubuntu, which I assume means that I have not lost vista??

Sorry if similar things have been posted in the past but I have not been able to locate a solution. I greatly appreciate any assistance.

After reading these forums I have done the following things:

I have updated grub, but I don't think vista was detected. Results are pasted below:

[CODE]
ray@ray-laptop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-31-generic
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
[CODE]

I note that there is an error with grub and vista whereby to boot vista you must select the recovery mode. There doesn't appear to be a vista recovery mode option, but i actually tried booting the various ubuntu recovery options anyway, and did not have any luck loading vista.

Also ran a boot info script, results are pasted below:
[CODE]          
      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   496,414,157   496,412,110   7 HPFS/NTFS
/dev/sda2         496,424,565   625,137,344   128,712,780   5 Extended
/dev/sda5         496,424,628   619,787,699   123,363,072  83 Linux
/dev/sda6         619,787,763   625,137,344     5,349,582  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C8E0C0AAE0C0A054                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bb9b9206-e26d-4ace-ba9e-b4d6609841e2   ext3                                     
/dev/sda6        78cc35d1-4386-4e4b-b2cc-0c033ec39509   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-31-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro  single
initrd        /boot/initrd.img-2.6.32-31-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro  single
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.24-22-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 ro  single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 10.04.2 LTS, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=bb9b9206-e26d-4ace-ba9e-b4d6609841e2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=78cc35d1-4386-4e4b-b2cc-0c033ec39509 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 306.5GB: boot/grub/menu.lst
 306.5GB: boot/grub/stage2
 306.5GB: boot/initrd.img-2.6.24-22-generic
 306.5GB: boot/initrd.img-2.6.24-22-generic.bak
 306.6GB: boot/initrd.img-2.6.32-30-generic
 306.6GB: boot/initrd.img-2.6.32-31-generic
 306.5GB: boot/vmlinuz-2.6.24-22-generic
 306.5GB: boot/vmlinuz-2.6.32-30-generic
 306.6GB: boot/vmlinuz-2.6.32-31-generic
 306.6GB: initrd.img
 306.6GB: initrd.img.old
 306.6GB: vmlinuz
 306.5GB: vmlinuz.old

 [CODE]

---

### Post by darayzins on 2011-05-02
I'm still stuck. Please help.

---

### Post by Mark Phelps on 2011-05-03
Looks like you upgraded from an earlier version of Ubuntu that still used menu.lst -- and the file does NOT contain any entries for Vista.

Been a while since I did that, but from what I recall, every time I did an update that changed the menu.lst file, I had to manually copy back the earlier Windows stanza from a copy I had saved.

Ubuntu 10.04 doesn't require a menu.lst, and it uses a very early version of GRUB2, but I would think that it still SHOULD have generated a menu entry for Vista.

If you are in a hurry to get Vista boot back, go to the link below, download and burn the proper Vista Repair CD, boot from that CD, and run Startup Repair three times:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Quackers on 2011-05-03
Mark Phelps solution will almost certainly get Windows booting again.
That would necessitate re-installing grub afterwards to get Ubuntu booting again.
I would suggest purging and re-installing grub(2) using the CHROOT section of the guide below.
This will remove the old grub files and replace them with grub2 files.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by darayzins on 2011-05-07
Mark and Quackers thanks for your time and help. 

I completed the purge and re-install of grub(2) using the CHROOT of the recommended guide. I can now use both vista and ubuntu again. THANKS AGAIN!!! :D

---

