---
title: "Dual boot upgrade 8.(04?) LTS to 10.04LTS Hangs on install restart at &quot;Starting up&quot;"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by zeelow on 2010-06-05
Hi all,

I've been using ubuntu for a couple of years rather successfully on my dual-boot Vista/Ubuntu.  It upgraded to 8.0(4?) LTS, and I kept it there until this afternoon :)  I followed the instructions on the ubuntu site to open up a terminal and update-manager --somearg to provide me with a nice little "Upgrade" button on the update manager.  I clicked said button per the instructions, let it do it's downloading and whatever else it does.  The last step of the installation is a system reboot.  I let it do that, and then my grub menu comes up as more-or-less this:


```
Ubuntu 10.04 LTS, kernel 2.6.32-32-generic
Ubuntu 10.04 LTS, kernel 2.6.32-32-generic (recovery mode)
Ubuntu 10.04 LTS, kernel 2.6.24-28-generic
Ubuntu 10.04 LTS, kernel 2.6.24-28-generic (recovery mode)
Ubuntu 10.04 LTS, kernel 2.6.22-14-generic
Ubuntu 10.04 LTS, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 10.04 LTS, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
 
```If I select the top one, I get:

```

Starting up ...
 
```

with a blinking cursor under the S for a LONG time (used the power switch after ~40 mins).  I tried the second 2.6.32-32 option for recovery mode.  It spit a bunch of gibberish to the screen for a couple seconds and then stopped, presumably doing the same thing, just with 100% more gibberish.

I tried booting into Vista, that worked fine.

Just to reiterate, I've not yet seen a 10 LTS login screen or desktop, and can't get one yet (just a "Starting up ...")

Thanks for your help


EDIT: Just to add, I did try searching, but since the only info I had to go on was 8 LTS to 10 LTS upgrade, and "Starting up ...", well those are just hard keywords to get any meaningful info.

---

### Post by zeelow on 2010-06-06
Ok, let me pose a second question then...  How do I go back to 8 LTS from the non-working 10 LTS (which never started)?

---

### Post by confused57 on 2010-06-06
You could try chrooting into your upgrade, see the instructions here by kansasnoob:
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by zeelow on 2010-06-06
Some updates (and maybe some clarification):

My 8 LTS setup was this:
Computer boots into Grub menu, then I select if I want to use ubuntu 8 LTS or vista for the session.

I'd basically like this same behavior (with legacy grub going to grub2), except with the new shiny ubuntu 10 LTS :)

I have tried some other things and have some additional information that may help.  My 10 LTS kernel is on hd0,2.  I read some information about chain loading legacy grub (which is what I believe I have because it says "Loading stage 1.5" on startup) into grub2.

I have tried the following on the grub command line (from [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)):
```
grub>  root  (hd0,2)
grub>  chainloader +1
grub>  boot
```

[FONT=Verdana]But I get the following in response to the "chainloader +1" line:

[/FONT]```
Error 13: Invalid or unsupported executable format
```

[FONT=Verdana]So I tried the next option:

[/FONT]```
grub>  configfile  (hd0,2)/boot/grub/menu.lst
```

[FONT=Verdana]And a grub menu that looks just like the first (legacy) grub menu comes up, I select my
10 LTS install and I get the same old:

[/FONT]```
Starting up ...
```[FONT=Verdana]

[/FONT][FONT=Verdana]So I tried something else posted at [/FONT][http://ubuntuforums.org/showthread.php?t=1307385](http://ubuntuforums.org/showthread.php?t=1307385)[FONT=Verdana] 

[/FONT]```
grub> root (hd0,2)
grub> kernel /boot/grub/core.img

```			
		
[FONT=Verdana]And the results were [/FONT]

```
Error 15: File not found
```

[FONT=Verdana]So now I'm a bit out of ideas.  All I want to do is use grub to chainload/smoke/whatever into
grub2 so that it has a shot at starting 10 LTS.

Thanks in advance for any advice.
[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by confused57 on 2010-06-06
It would probably be a good idea to post the output of the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by zeelow on 2010-06-06
Thanks for checking back in confused :)

Here is my results.txt from the boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/BCD

hda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

hda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdb: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9aeed03f

Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63    19,438,649    19,438,587   7 HPFS/NTFS
/dev/hda2    *     19,439,616   117,293,131    97,853,516   7 HPFS/NTFS
/dev/hda3         117,306,630   154,577,429    37,270,800  83 Linux
/dev/hda4         154,577,430   156,296,384     1,718,955   5 Extended
/dev/hda5         154,577,493   156,296,384     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        6EEC74BFEC7482DF                       ntfs       RECOVERY                      
/dev/hda2        343C03803C033C7C                       ntfs                                     
/dev/hda3        9cd2e410-0597-4d18-84cf-9911903e7d55   ext3                                     
/dev/hda5        8e137cc2-52ad-4842-9899-7110f8f5c2a4   swap                                     
/dev/hdb                                                iso9660    Ubuntu 8.04.1 i386            
/dev/loop0                                              squashfs                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



=========================== hda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.24-28-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro  single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 10.04 LTS, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro  single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 ro  single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== hda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=9cd2e410-0597-4d18-84cf-9911903e7d55 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8e137cc2-52ad-4842-9899-7110f8f5c2a4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== hda3: Location of files loaded by Grub: ===================


  75.1GB: boot/grub/menu.lst
  75.1GB: boot/grub/stage2
  75.1GB: boot/initrd.img-2.6.20-16-generic
  75.1GB: boot/initrd.img-2.6.20-16-generic.bak
  75.1GB: boot/initrd.img-2.6.22-14-generic
  75.1GB: boot/initrd.img-2.6.22-14-generic.bak
  76.5GB: boot/initrd.img-2.6.24-28-generic
  75.4GB: boot/initrd.img-2.6.24-28-generic.bak
  75.1GB: boot/initrd.img-2.6.32-22-generic
  75.1GB: boot/vmlinuz-2.6.20-16-generic
  75.2GB: boot/vmlinuz-2.6.22-14-generic
  75.3GB: boot/vmlinuz-2.6.24-28-generic
  75.3GB: boot/vmlinuz-2.6.32-22-generic
  75.1GB: initrd.img
  76.5GB: initrd.img.old
  75.3GB: vmlinuz
  75.3GB: vmlinuz.old
```

---

### Post by oldfred on 2010-06-06
I do not see anything obvious in the boot script and I think you are past that anyway. the main issue with Lucid is changes to video and many of us have had issues. My Karmic loaded without any problems at all but Lucid I had to add nomodeset to both install and first boot.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line


if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by zeelow on 2010-06-08
Grub isn't saving my change to remove quiet splash and replace it with nomodeset.  I've hit "e" to edit the kernel line, and removed the "quiet" line entirely, but when I go back to reboot (because it totally reboots the computer on grub's 'b' command, bios and all), the orig line is there, my edits have not stuck.  How do I get grub to save my config?

I used the nomodeset and acpi=off options on the 10 LTS live cd and I got a desktop (woot), now I'd just like to get grub to save my changes!

---

### Post by oldfred on 2010-06-09
If you do not have a driver to install and want to keep the settings, you have to edit grub. Then run sudo update-grub to make it permanent.

/etc/default/grub

# GRUB_CMDLINE_LINUX
If it exists, this line imports any entries to the end of the 'linux' command line (Grub Legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

More details:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by zeelow on 2010-06-09
Almost there!

I looked for an /etc/default/grub, and there isn't one (I suspect that I'm just using grublegacy all the way instead of going grublegacy -> grub2 -> 10LTS)

However, I did go in and edit the "don't edit this" automagic section of grub legacy's /boot/grub/menu.lst and added the
```
radeon.modeset=1 acpi=off
```
options after the kernel line (and replaced "splash quiet").  At first I tried nomodeset in place of the radeon one (I have a supported radeon integrated graphics chip in that computer), and it eventually started, but it was a flash with the radeon.modeset=1 argument!

But, since it doesn't look like I have grub2 going (which is fine, I've read a lot of horror stories about dual boot machines like mine that upgrade to grub2), I did commit a major sin by editing the automagic "don't touch this" part of menu.lst.  What's the safe way to proceed here?  I'm fine with keeping grublegacy.

Note that I'm not 100% opposed to grub2, I just don't want it to wipe out my ability to get to the windows side.

---

