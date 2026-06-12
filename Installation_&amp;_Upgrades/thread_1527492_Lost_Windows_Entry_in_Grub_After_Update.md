---
title: "Lost Windows Entry in Grub After Update"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by Experiment on 2010-07-09
Ubuntu's update manager recently updated the Grub menu.lst file.  It let me decide if I wanted to keep my old menu.lst or the new one.  After deciding that I was fine with the new one, I found out that I can no longer boot into Windows 7.  I had previously edited menu.lst so that Windows would be at the top of the list, however, I didn't notice that this had put it into the automagic update area, and I realize now that I should have just edited what the default number was instead of moving around the entries.

Anyways, I can no longer access my Windows 7 OS via Grub, and I was wondering what sort of fix I can have for this.  I've tried running update-grub, but it hasn't fixed the problem.  The Windows bootloader is on the first partition of the only hard drive, as far as I can remember.

---

### Post by tommcd on 2010-07-09
> **Experiment said:**
> Ubuntu's update manager recently updated the Grub menu.lst file.
What version of Ubuntu are you using??? Ubuntu 9.10 and 10.04 use grub2. Ubuntu 9.04 and downward use grub-legacy. The menu.lst file is from grub-legacy. Grub2 uses grub.cfg.
> **Experiment said:**
> 
I've tried running update-grub, but it hasn't fixed the problem.  
The *sudo update-grub* command is for grub2, not grub-legacy.
So ... which version of Ubuntu are you on?? And was this a clean install or a dist-upgrade???

---

### Post by Experiment on 2010-07-09
I'm running 10.4, and yes, it was a dist upgrade, but I'm not sure what the original distribution I had installed was.  Before I had edited menu.lst, and it had changed the grub boot menu, so I assume I'm still using grub-legacy.  grub and grub-common are the only packages that show up as installed when I look up "grub" in the package manager.

---

### Post by oldfred on 2010-07-09
Did the upgrade save an old menu.lst like menu.lst.backup? If so you can copy your windows entry from that. Everyone says old grub was better but many users have had your issue and grub legacy does not always find windows. The new osprober finds windows and even finds non working windows. 

So we can give you an entry:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by mcduck on 2010-07-09
Let me guess, you had at some point edited the menu.lst file by hand, perhaps moving the windows entry to the top of the menu or something like that?

If you edit the menu.lst file you *must* keep any additional menu entries (like the Windows entry) outside of the region marked as "Debian Automagick kernels list". It actually says that in the menu.lst file itself, and if I remember right the section start & end are even marked with plenty of uppercase text and some exclamation marks to make the point as clear as possible :D.

That section gets automatically rewritten using the rules in the default options -section right above it, so you must keep all additional menu entries either above that section, or under it, or you'll loose them when the next kernel update recreates the menu.lst file.

Also if you make any modifications to Ubuntu boot options in the menu.lst file you must make the same changes in the default options-section as well.

I'd actually recommend reading through all the comments in the menu.lst file, they give pretty good explanation about how the file works and what you need to do when you edit it.

---

### Post by Shompol on 2010-07-09
was editing menu.lst by hand to move windows entry up, and accidentally deleted it. Can I regenerate that without reinstalling now? Will Gparted help?

---

### Post by oldfred on 2010-07-09
Shompol - You really should start your own thread. It is best to back up any important system file before editing so you have something to go back to. 
Gparted will not help. Grub will create a new menu.lst, I do not remember if a sudo update-grub will do it or if you have to reinstall grub.

---

### Post by mcduck on 2010-07-09
> **Shompol said:**
> was editing menu.lst by hand to move windows entry up, and accidentally deleted it. Can I regenerate that without reinstalling now? Will Gparted help?

You definitely don't have to reinstall for that, as long as you tell what version of Windows you are running and provide detailed information about your hard drive/partition layout (like the output of "sudo fdisk -l") it's quite simple to recreate the windows entry by hand.

Of course same applies to thread starter as well. :)

(and I agree with oldfred about making backups of files you edit. Great habit that saves you from lots of troubles if something goes wrong)

---

### Post by Shompol on 2010-07-09
Thanx. Was Windows XP on first partition. Won't have access to that computer until weekend (this is an experiment to transition my grandpa from his malware-infested XP)

---

### Post by Experiment on 2010-07-10
> **mcduck said:**
> Let me guess, you had at some point edited the menu.lst file by hand, perhaps moving the windows entry to the top of the menu or something like that?

Yeah, I mentioned that I had done exactly that in my first post.  You are spot on sir. ;)  Tragically, there's not as many warnings as you remembered, especially near the end of the code where the Windows entry that I was looking at were. :(  I'll make sure to read through the whole file next time I'm editing system files.

Here's the results of the bootscript.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    83,888,127    83,681,280   7 HPFS/NTFS
/dev/sda3          83,891,430   153,356,489    69,465,060   5 Extended
/dev/sda5         147,348,243   153,356,489     6,008,247  82 Linux swap / Solaris
/dev/sda6          83,891,556   144,649,259    60,757,704  83 Linux
/dev/sda7         144,649,323   147,348,179     2,698,857  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        085AA6845AA66DDE                       ntfs       System Reserved               
/dev/sda2        ECE8B8B4E8B87F00                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9b87da4f-5a72-4560-97a4-c1d5146bb515   swap                                     
/dev/sda6        ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8   ext3                                     
/dev/sda7        f33e1fc4-5144-4e0b-91de-571160cbf8f3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.






=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=ae10d0fe-d07e-401e-aac8-f3d8d25e1ec8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f33e1fc4-5144-4e0b-91de-571160cbf8f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  49.8GB: boot/grub/menu.lst
  49.8GB: boot/grub/stage2
  49.8GB: boot/initrd.img-2.6.28-11-generic
  49.9GB: boot/initrd.img-2.6.31-21-generic
  49.8GB: boot/initrd.img-2.6.32-22-generic
  49.9GB: boot/initrd.img-2.6.32-23-generic
  49.8GB: boot/vmlinuz-2.6.28-11-generic
  49.9GB: boot/vmlinuz-2.6.31-21-generic
  49.8GB: boot/vmlinuz-2.6.32-22-generic
  49.8GB: boot/vmlinuz-2.6.32-23-generic
  49.9GB: initrd.img
  49.8GB: initrd.img.old
  49.8GB: vmlinuz
  49.8GB: vmlinuz.old
```

---

### Post by oldfred on 2010-07-10
An entry like this will work.

title        Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify    (hd0,0)
savedefault
chainloader +1


If you want it first:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]Paste here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by Experiment on 2010-07-20
That entry worked great, thanks!

SOLVED!

---

