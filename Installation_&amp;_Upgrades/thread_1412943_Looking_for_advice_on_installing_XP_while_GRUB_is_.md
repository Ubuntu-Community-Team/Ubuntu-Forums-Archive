---
title: "Looking for advice on installing XP while GRUB is in play"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by baddoght on 2010-02-21
Hi all,
 
I am fairly new to Ubuntu, but find that I am using it more and more. Unfortunately, I still have to use Window's to work. Here is what I am facing....
 
I am looking to do a clean install of Window's 7 over my XP Pro. XP is installed on a 500 gig drive and Ubuntu is installed on a 160 gig drive (in that order). I do not want to effect Ubuntu in any way outside of to modify GRUB if it does not pick up that Window's 7 is now installed.
 
My question are:
 
1.) Should I disconnect the second drive which is Ubuntu when I install Window's 7?
2.) Will I need to modify GRUB, please explain how I would do this.
 
As I said, I am fairly new to Ubuntu but do work in a Tru64 UNIX invironment and am familuar with vi editor.
 
Thanks.
 
Bad[DOG]/HT
Ken

---

### Post by presence1960 on 2010-02-21
Not really necessary to unplug 160 Gb disk, that is just extra work for those not sure of themselves. Go into BIOS and make sure the 500 GB disk is set to boot first in the hard disk boot order. Save changes to CMOS. Now you can install Windows to the 500 GB disk with no worries about the 160 GB disk because windows writes it's bootloader to the first disk to boot in BIOS so your 160 Gb will remain untouched provided you select the 500 GB disk to install windows to from the install DVD.

If your GRUB is currently on the 500 Gb disk it will be overwritten and you will need to restore GRUB after windows is installed and you are sure windows boots fine. If you need help with reinstalling GRUB post back.

If you aren't sure where GRUB is and/or which version of GRUB you have do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by baddoght on 2010-02-22
Thanks Presence -

I hate to admit this, but I was unable to get the script to work.  I did find my grub menu in /boot/grub/.  Here is a list of assignments from menu.lst:

---
default        0
timeout        10


title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, kernel 2.6.24-22-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-22-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 9.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet


title        Other operating systems:
root


title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

----

I'm about done backing up what I wish to keep from XP.  Am I ok to proceed?

baddoght
Ken

---

### Post by presence1960 on 2010-02-22
> **baddoght said:**
> Thanks Presence -

I hate to admit this, but I was unable to get the script to work.  I did find my grub menu in /boot/grub/.  Here is a list of assignments from menu.lst:

---
default        0
timeout        10


title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, kernel 2.6.24-22-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-22-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 9.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet


title        Other operating systems:
root


title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

----

I'm about done backing up what I wish to keep from XP.  Am I ok to proceed?

baddoght
Ken

I actually wanted the other info contained in the script. I just wanted to make sure your setup is exactly as you say it is. Don't take offense but a lot of times people say their machine is set up a certain way and then we give instructions. Then after the instructions are followed there are problem(s) because the setup isn't exactly as we were told. The boot info script shows that info. I would say go ahead and install, but first  run in terminal ```
sudo fdisk -l
```That is a lowercase L in -l

Post back the output of that command so we can see your partition table.

---

### Post by baddoght on 2010-02-22
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabd449b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a63c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

---

### Post by presence1960 on 2010-02-22
Good to go. Just make sure the 500 GB disk is first to boot in BIOS in the hard disk boot order. Install windows to the 500 GB disk.

---

### Post by d3v1150m471c on 2010-02-22
I have xp on virtualbox. You might want to try it that way as it's quite stable, fast, and you don't have to worry about the hazards that can come along with dual booting and partitions. Be sure to add the guest additions after you install it on Vbox if you choose to do so.

---

### Post by baddoght on 2010-02-26
Just wanted to give an update. I've installed Win 7 successfully, but GRUB did seem to get blown away (only windows 7 boots now). I believe that I have the GRUB Legacy as I started with Ubuntu 8.04 and upgraded to 9.10. I'm doing some reading on restoring Grub, but likely won't get back to this until sometime tomorrow. If someone has a quick fix, I will check back later tonight or tomorrow morning.
 
Thanks.
 
Bad[DOG]/H.T.
Ken

---

### Post by baddoght on 2010-03-01
Hi all -
 
Still having some problems getting GRUB fixed. Again, I am a bit gunshy but what I think I need to do is somehow fix the Master Boot Record on drive /dev/sda which is my windows drive (/dev/sdb is Ubuntu).  Can someone review what I currently have (from the previous post) and advise?
 
Thanks.
 
Bad[DOG]/HT
Ken

---

### Post by presence1960 on 2010-03-01
> **baddoght said:**
> Hi all -
 
Still having some problems getting GRUB fixed. Again, I am a bit gunshy but what I think I need to do is somehow fix the Master Boot Record on drive /dev/sda which is my windows drive (/dev/sdb is Ubuntu).  Can someone review what I currently have (from the previous post) and advise?
 
Thanks.
 
Bad[DOG]/HT
Ken

without the info from the boot info script we will basically be guessing about your setup & boot process. Run the script & post the results.

---

### Post by wilee-nilee on 2010-03-01
Here is a link that tells you how to identify the grub type by booting a live cd and looking at the 9.10 partition and specific files.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

There are some recovery instructions, bu I would wait until somebody responds.

---

### Post by presence1960 on 2010-03-01
> **wilee-nilee said:**
> Here is a link that tells you how to identify the grub type by booting a live cd and looking at the 9.10 partition and specific files.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

There are some recovery instructions, bu I would wait until somebody responds.

Good info indeed, I have that page bookmarked myself. but the OP is talking about repairing MBR(s) and the boot info script will tell what is on each MBR and if GRUB which partition it looks to to boot ubuntu. That is the info needed.

I would say it is best to see what is on MBR(s) prior to making any changes.

---

### Post by baddoght on 2010-03-01
Ok, got it to work this time:

Here you go and THANK-YOU for your review....

Bad[DOG]/HT
Ken

                Boot Info Script 0.55    dated February 15th, 2010              
      

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /ubninit looks at sector 700 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _________________________________________________
____

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabd449b4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _________________________________________________
____

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a63c5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   299,805,029   299,804,967  83 Linux
/dev/sdb2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sdb5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solar
is


Drive: sdg ___________________ _________________________________________________
____

Disk /dev/sdg: 8011 MB, 8011120640 bytes
16 heads, 32 sectors/track, 30560 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32    15,646,719    15,646,688   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL        
                 

/dev/loop0                                              squashfs                
                 
/dev/sda1        503065E13065CF12                       ntfs                    
                 
/dev/sdb1        994207b6-67f3-4552-ab84-9290e5b8d8a4   ext3                    
                 
/dev/sdb5        dbd464e6-093d-40dd-a79a-a06079250fb4   swap                    
                 
/dev/sdg1        F7EC-64F6                              vfat       KINGSTON     
                 

============================ "mount | grep ^/dev  output: ======================
=====

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=ha
l,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, kernel 2.6.24-22-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-22-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=994207b6-67f3-4552-ab8
4-9290e5b8d8a4 ro  single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 9.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=994207b6-67f3-4552-ab84-9290e5b8d8a4 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sdb5
UUID=dbd464e6-093d-40dd-a79a-a06079250fb4 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.7GB: boot/grub/menu.lst
  30.7GB: boot/grub/stage2
  30.8GB: boot/initrd.img-2.6.24-22-generic
  30.8GB: boot/initrd.img-2.6.24-22-generic.bak
  30.8GB: boot/initrd.img-2.6.27-11-generic
  30.7GB: boot/initrd.img-2.6.28-17-generic
  30.8GB: boot/initrd.img-2.6.31-17-generic
  30.8GB: boot/initrd.img-2.6.31-19-generic
  30.7GB: boot/vmlinuz-2.6.24-22-generic
  30.8GB: boot/vmlinuz-2.6.27-11-generic
  30.8GB: boot/vmlinuz-2.6.28-17-generic
  30.7GB: boot/vmlinuz-2.6.31-17-generic
  30.7GB: boot/vmlinuz-2.6.31-19-generic
  30.8GB: initrd.img
  30.8GB: initrd.img.old
  30.7GB: vmlinuz
  30.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by presence1960 on 2010-03-01
Your GRUB is indeed intact. it is on MBR of sdb. Go into BIOS and set sdb (160 GB) as first to boot in the hard disk boot order. Save changes to CMOS and continue booting into ubuntu. When the desktop loads open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```that is a lowercase L in .lst

Scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title               Microsoft Windows 7
rootnoverify        (hd1,0)
chainloader         +1

```

Click Save on top toolbar & close file. reboot & try booting windows from the GRUB menu.

---

### Post by baddoght on 2010-03-01
Thanks!  That did fix it.  I really appreciate the help.

Thanks again.

Bad[DOG]/HT
Ken

---

### Post by presence1960 on 2010-03-02
> **baddoght said:**
> Thanks!  That did fix it.  I really appreciate the help.

Thanks again.

Bad[DOG]/HT
Ken

Glad you got it working, enjoy ubuntu & windows.

---

