---
title: "messed up partition table/boot record?"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by Banjo_Ben on 2010-03-14
Hello, folks,

I am still very much a beginner.  Running ubuntu 8.10 and windows XP MCE in separate partitions; grub 1.5 lets me choose which to boot.

Updated the kernel to 2.6.27-17-generic (at the urging of the update manager), and on reboot, ubuntu has only a command-line interface; seems it is looking for a device by UUID and is unable to find it.  Choosing older versions of the kernel from the grub menu bring the same result.  I poked around on the forums, and based on a thread I found, I typed this into the command-line prompt where I found myself after logging into ubuntu:

```
sudo fdisk /dev/sda

x
f
w
```After that, ubuntu behaves the same (boots to command-line interface only), but now Windows will not boot; it says I must reinstall a file called hal.dll.  I think hal.dll is probably fine, and that I have just messed up the partition table or boot record (not sure exactly what those mean) by executing the commands quoted above.  I have what I thought was a recovery DVD for windows, but it won't boot from that, either.

Ran GParted from the live CD of 8.10 and checked these partitions:
/dev/sda1  FAT32  this is the recovery partition for windows
/dev/sda2  ntfs  this is the main windows partition
/dev/sda3  ext3  this is the linux partition
the rest of the disk is for the linux swap file, which I did not check with GParted.  In sda1, GParted noted that "there are differences between boot sector and its backup[,]" but it did not automatically fix that.  I saved the results from GParted, but it's a .htm file, which cannot be attached to a forum post.

How can I:

(1) fix the partition table so that windows will boot again?

(2) get ubuntu to boot into a desktop environment, instead of the command-line interface?

Thank you very much in advance,
--Banjo_Ben

---

### Post by oldfred on 2010-03-14
I saved this thread on hal.dll error:

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)

---

### Post by srs5694 on 2010-03-14
> **Banjo_Ben said:**
> Updated the kernel to 2.6.27-17-generic (at the urging of the update manager), and on reboot, ubuntu has only a command-line interface; seems it is looking for a device by UUID and is unable to find it.

It might be helpful for you to post a screen shot (use a digital camera) of the error message, along with the contents of /boot/grub/menu.lst and the output of "fdisk -l".

> I typed this into the command-line prompt where I found myself after logging into ubuntu:

Those fdisk commands sort the partition table entries. Doing this might fix the problem you report, but only with certain specific causes and then only by chance.

> After that, ubuntu behaves the same (boots to command-line interface only), but now Windows will not boot; it says I must reinstall a file called hal.dll.

Windows is very fussy about its boot partition. If you knew the original order of the boot partitions, you could undo your sort, but I suspect you don't remember that detail. Failing that, you'll need to use the Windows recovery DVD (see below)....

> I think hal.dll is probably fine, and that I have just messed up the partition table or boot record (not sure exactly what those mean) by executing the commands quoted above.

The partition table is a list on the disk of all the partitions on the disk, including their start points, end points, type codes, and a few other details. Your partition table is almost certainly fine, in the sense that it's valid; it's just that by changing the order of the partitions in the table with the fdisk experts' menu 'f' command, you upset Windows; it's now sulking like a recalcitrant two-year-old.

"Boot record" is not entirely precise. It could refer to the Master Boot Record (MBR), which is the first sector of the hard disk. The MBR contains both the first-stage boot loader (code that the BIOS loads and runs before it runs anything else) and the partition table. "Boot record" could also mean the boot code in the first sector or two of a partition or to boot loader code stored elsewhere. (The boot process on most computers is rather convoluted, especially on multi-boot systems.) It's likely that all of these types of boot code are just fine; the problems are most likely in the GRUB configuration for your new kernel and in the fact that your sorted partitions are out of the order of what Windows' late-stage boot loader expects.

> I have what I thought was a recovery DVD for windows, but it won't boot from that, either.

Post details. It should boot to a Windows recovery menu. If there's no sign of activity when you insert the disc and reboot the computer, it could be that your system is configured to not boot from CD/DVD. That's easily fixed. Most modern systems let you adjust the boot order on a boot-by-boot basis by pressing F10 or some other key during the boot process. Watch your boot messages for a prompt about this. (It only stays on-screen for a couple of seconds, so it's easy to miss.) Failing that, you can enter your BIOS setup utility to adjust the order in which the BIOS checks boot devices. Again, check the prompts when you boot to see what key to press.

Other problems might not be so easy to solve. For instance, your disc might not actually be a Windows installation or recovery disc.

---

### Post by Banjo_Ben on 2010-03-14
Thank you to all those who viewed, and especially to those who replied.

oldfred, I glanced at that thread, and will look at it more closely tomorrow, thank you.  I think I'm going to have to make a windows xp recovery disk, and I have a couple of leads on that, I just need to look into it a bit more.

srs5694, I've attached the contents of /boot/grub/menu.lst and a photo of the error message on the screen (thanks, too, for that idea--not sure if I would've thought of just taking a picture of it).  Here is the output of sudo fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16521652

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         691     5550426    b  W95 FAT32
/dev/sda2             692       20766   161252437+   7  HPFS/NTFS
/dev/sda3           20767       24168    27326565   83  Linux
/dev/sda4           24169       24321     1228972+   5  Extended
/dev/sda5           24169       24321     1228941   82  Linux swap / Solaris
```

I've already got the boot order set up with the DVD-ROM/CD-RW and DVD-RW drives in line before the hard disk, but when the so-called recovery disk is in either tray, it pauses just a bit, then goes to the grub list.  That's how I concluded it's not actually a bootable disk.  This is an emachines model with mfr-installed windows, so I don't have an actual windows installation disk, and I've never had occasion to check the "recovery disk" since I made it shortly after getting the computer about 3 years ago.

Any confusion about partition table vs. boot record is purely the result of my fractured understanding of the terms, and attempt to synthesize some of what I've read.  I appreciate the explanation, of those terms as well as throughout the rest of your post.

Thank you,
--Banjo_Ben

---

### Post by oldfred on 2010-03-14
It looks like you have booted to the normal command line. Have your tried this to see whether it will continue to load the graphical gnome window system or error out?

```
startx
```

---

### Post by Banjo_Ben on 2010-03-15
> **oldfred said:**
> It looks like you have booted to the normal command line. Have your tried this to see whether it will continue to load the graphical gnome window system or error out?

```
startx
```

oldfred,

I had not tried that, because I didn't know that command.  I just tried it, and got a screen with about the top third garbage, the bottom two-thirds the light-brown login screen color.  I get about that same look with the live cd, but it corrects itself after a moment and continues.  Booting from the hard disk, I left it for several seconds, but it did not change or continue to a recognizable desktop (with top and bottom panels, etc.).  Please see the attached picture, and thank you again.

--Benjo_Ben

---

### Post by srs5694 on 2010-03-15
The message you see ("...trying to resume from..." and so on) is telling you that the kernel is looking for data from a suspend-to-disk operation. When it doesn't find such data, the kernel does a normal boot ("no resume image, doing normal boot..."). This is all perfectly normal, unless of course you did perform a suspend-to-disk, and is not cause for concern.

Overall, it appears to me that your Linux installation is booting normally. What's *not* normal is your X setup. The answers to two additional sets of questions will help you fix the Linux side of the problem:


[list=1]
[*]Did you upgrade anything other than the kernel? In particular, did you upgrade any X packages ("xorg-{whatever}.deb")? If so, it's conceivable that you've encountered a new bug, or perhaps the package reconfigured your X server.
[*]What type of video hardware are you using? If you've got an ATI or nVidia card, are you using the proprietary ATI or nVidia drivers or the open source drivers? The proprietary drivers include a kernel component, and if that component is missing, they won't work.
[/list]


Overall, I think the problem is most likely to be with proprietary ATI or nVidia drivers. You should be able to get the drivers working again by re-installing those drivers. On my Ubuntu 9.10 system, the ATI drivers seem to be called xorg-driver-fglrx, and there are an awful lot of packages that match the "nvidia" string. Unfortunately for my ability to help you on this, my Ubuntu system has Intel video, so I don't use these packages myself. You may need to just try a few. Alternatively, go to the ATI or nVidia Web sites and download their distribution-agnostic packages. In the case of nVidia cards, if you don't need the 3D features, you can switch to the open source drivers by editing /etc/X11/xorg.conf and changing "nvidia" to "nv" in the "Driver" line in the "Device" section. The open source ATI drivers work well for older chipsets, but poorly for new ones.

As to Windows, my best suggestion is to track down a friend with an install CD/DVD for whatever version of Windows you're running and use it to repair your installation. Another possibility is to go into fdisk and use its 'a' option to set the Windows NTFS partition bootable and remove the bootable flag from the FAT partition.

---

### Post by Banjo_Ben on 2010-03-15
> **srs5694 said:**
> Overall, it appears to me that your Linux installation is booting normally.
 
I don't know enough about the different components of the software, and what's actually happening during boot, to have recognized that. I suppose what I captured in the screenshot is something that has always displayed, but I've not noticed it because it is erased so quickly.  The first time it stayed up long enough for me to read it, I thought it indicated a problem.
 
> What's *not* normal is your X setup. The answers to two additional sets of questions will help you fix the Linux side of the problem:
 

[LIST=1]
[*]Did you upgrade anything other than the kernel? In particular, did you upgrade any X packages ("xorg-{whatever}.deb")? If so, it's conceivable that you've encountered a new bug, or perhaps the package reconfigured your X server.
[/LIST]I'm sure I updated whatever was on the update manager's list; I don't remember if any X packages were included, but from now on, I'll have to pay attention to that.

> [LIST=1]
[*]What type of video hardware are you using? If you've got an ATI or nVidia card, are you using the proprietary ATI or nVidia drivers or the open source drivers? The proprietary drivers include a kernel component, and if that component is missing, they won't work.
[/LIST]Overall, I think the problem is most likely to be with proprietary ATI or nVidia drivers.
 
What you're saying makes sense, and it's also helping me understand things in general. My video hardware is ATI Radeon Express, not a card, but one of those that's on the motherboard. When I first started playing with ubuntu, I wanted to try compiz fusion, so I went through a lot of stuff to get that to work. I remember pursuing the proprietary driver from the ATI website, and that's probably what I've been running.
 
> As to Windows, my best suggestion is to track down a friend with an install CD/DVD for whatever version of Windows you're running and use it to repair your installation. Another possibility is to go into fdisk and use its 'a' option to set the Windows NTFS partition bootable and remove the bootable flag from the FAT partition.
 
I'm working on getting a CD for Windows XP. Will putting the boot flag on the NTFS partition likely reorder the partitions to Windows' satisfaction? Getting back to something you said earlier--that I probably didn't know what order they were in before I used the fdisk experts' "f" command (and I don't)--is it simply a matter of ordering them in the same sequence as the drive letters in Windows? For instance, the NTFS partition is "C:" in Windows, so should that be /dev/sda1? The FAT32 recovery partition is some subsequent letter, "H:," I believe, so should that be /dev/sda2? The linux partitions don't appear in Windows, so I can leave them where they are in the order, I guess. Is correctly reordering the partition table (correctly for Windows, that is) as simple as that?
 
Again, thank you very much,
--Banjo_Ben

---

### Post by oldfred on 2010-03-15
If you do not have problems with a partition table you do not want to mess with it. Changing the boot flag is just that, a setting in the table on which partition the windows system will look to continue booting.

If you still can get to a command line, you probably can uninstall and reinstall whatever you need, I just do not know about ATI drivers and my Nvidia has worked without issue for the last two years (do not ask about the first year).

---

### Post by presence1960 on 2010-03-15
Let's see what you have on that machine before you go fiddling around. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by srs5694 on 2010-03-15
> **Banjo_Ben said:**
> What you're saying makes sense, and it's also helping me understand things in general. My video hardware is ATI Radeon Express, not a card, but one of those that's on the motherboard. When I first started playing with ubuntu, I wanted to try compiz fusion, so I went through a lot of stuff to get that to work. I remember pursuing the proprietary driver from the ATI website, and that's probably what I've been running.

Then that's almost certainly your problem. You should track down and re-install the software you originally installed from copies still on your hard disk; go back to the ATI Web site, download the latest driver, and install it; or install the appropriate Ubuntu packages. It's very unlikely that there's anything else wrong with your boot process. (I speak from experience; I've dealt with these issues before, and it's why I hate the proprietary ATI and nVidia drivers.)

> Will putting the boot flag on the NTFS partition likely reorder the partitions to Windows' satisfaction?

Setting or removing the boot flag won't re-order the partitions. My suggestion to do this is based on the idea that the boot flag may have been reset in your earlier changes. This doesn't actually seem very likely to me, based on my knowledge of what fdisk does; but it's conceivable and it's easy to test, so I suggested it as something to try.

> Getting back to something you said earlier--that I probably didn't know what order they were in before I used the fdisk experts' "f" command (and I don't)--is it simply a matter of ordering them in the same sequence as the drive letters in Windows? For instance, the NTFS partition is "C:" in Windows, so should that be /dev/sda1?
 
No, I'm afraid not. Windows (even XP) keeps a record of what partitions get what drive letters, based on filesystem ID codes, and these can have nothing to do with the partitions' order in the partition table. I'm working off of the assumption (which may be incorrect) that Windows is objecting to the fact that the placement of its partitions in the partition table isn't what it's expecting. Since there are four possible primary partition locations and two Windows partitions, there are 4x3 = 12 possible combinations, assuming that Windows doesn't care about the Linux, extended, or logical partitions' locations. That's a total of two assumptions and 12 possible combinations to test. (Well, 11 combinations; you already know that one doesn't work!) Testing each combination would require deleting and (correctly!) re-creating two or more partitions, so this is a lot of work and the potential to create even more of a mess of things is pretty high. That's why I think you should try using a Windows install CD/DVD first. Personally, I'd re-install Windows rather than risk trashing my Linux installation with such partition manipulations. At most, I'd try swapping the two Windows partitions and leave the Linux partitions alone.

---

### Post by Banjo_Ben on 2010-03-15
presence1960,

Thank you for your help, and the easy-to-follow directions.  I ran the script as you instructed, and here is the RESULTS.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16521652

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    11,100,914    11,100,852   b W95 FAT32
/dev/sda2          11,100,915   333,605,789   322,504,875   7 HPFS/NTFS
/dev/sda3         333,605,790   388,258,919    54,653,130  83 Linux
/dev/sda4         388,258,920   390,716,864     2,457,945   5 Extended
/dev/sda5         388,258,983   390,716,864     2,457,882  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        423B-2BDF                              vfat       RECOVERY                      
/dev/sda2        36DCF432DCF3E9CF                       ntfs                                     
/dev/sda3        358de88d-921e-4ae1-b176-9ea1695dd72e   ext3                                     
/dev/sda5        8c5f2633-add2-490b-b146-2b84f9294af1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd1        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda3/boot/grub/menu.lst: ===========================

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
default        8

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

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
# kopt=root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro

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

title        Ubuntu 8.10, kernel 2.6.27-17-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 8.10, kernel 2.6.27-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
initrd        /boot/initrd.img-2.6.27-16-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
initrd        /boot/initrd.img-2.6.27-16-generic

title        Ubuntu 8.10, kernel 2.6.27-15-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
initrd        /boot/initrd.img-2.6.27-15-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-15-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
initrd        /boot/initrd.img-2.6.27-15-generic

## title        Ubuntu 8.10, kernel 2.6.27-14-generic
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
## initrd        /boot/initrd.img-2.6.27-14-generic
## quiet

## title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
## initrd        /boot/initrd.img-2.6.27-14-generic

## title        Ubuntu 8.10, kernel 2.6.27-11-generic
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
## initrd        /boot/initrd.img-2.6.27-11-generic
## quiet

## title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
## initrd        /boot/initrd.img-2.6.27-11-generic

## title        Ubuntu 8.10, kernel 2.6.27-9-generic
## root        (hd0,2)
## kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
## initrd        /boot/initrd.img-2.6.27-9-generic
## quiet

## title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
## initrd        /boot/initrd.img-2.6.27-9-generic

## title        Ubuntu 8.10, kernel 2.6.24-19-generic
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
## initrd        /boot/initrd.img-2.6.24-19-generic
## quiet

## title        Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
## initrd        /boot/initrd.img-2.6.24-19-generic

## title        Ubuntu 8.10, kernel 2.6.22-14-generic
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro quiet splash 
## initrd        /boot/initrd.img-2.6.22-14-generic
## quiet

## title        Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
## root         (hd0,2)
## kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=358de88d-921e-4ae1-b176-9ea1695dd72e ro  single
## initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 8.10, memtest86+
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
title        Windows XP Media Center Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title        Windows XP (recovery mode)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=358de88d-921e-4ae1-b176-9ea1695dd72e /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=8c5f2633-add2-490b-b146-2b84f9294af1 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/hda1    /media/windows_ntfs  ntfs  nls=utf8,umask=0222  0  0

=================== sda3: Location of files loaded by Grub: ===================


 183.0GB: boot/grub/menu.lst
 183.0GB: boot/grub/stage2
 183.0GB: boot/initrd.img-2.6.22-14-generic
 183.0GB: boot/initrd.img-2.6.22-14-generic.bak
 183.1GB: boot/initrd.img-2.6.24-19-generic
 183.0GB: boot/initrd.img-2.6.24-19-generic.bak
 183.1GB: boot/initrd.img-2.6.27-11-generic
 183.0GB: boot/initrd.img-2.6.27-14-generic
 183.1GB: boot/initrd.img-2.6.27-15-generic
 183.1GB: boot/initrd.img-2.6.27-16-generic
 183.0GB: boot/initrd.img-2.6.27-17-generic
 183.0GB: boot/initrd.img-2.6.27-9-generic
 183.1GB: boot/vmlinuz-2.6.22-14-generic
 183.0GB: boot/vmlinuz-2.6.24-19-generic
 183.1GB: boot/vmlinuz-2.6.27-11-generic
 183.1GB: boot/vmlinuz-2.6.27-14-generic
 183.0GB: boot/vmlinuz-2.6.27-15-generic
 183.0GB: boot/vmlinuz-2.6.27-16-generic
 183.1GB: boot/vmlinuz-2.6.27-17-generic
 183.1GB: boot/vmlinuz-2.6.27-9-generic
 183.0GB: initrd.img
 183.1GB: initrd.img.old
 183.1GB: vmlinuz
 183.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Meanwhile, I am going to work on the graphics driver issue to get the X system working again..

Thank you,
--Banjo_Ben

---

### Post by presence1960 on 2010-03-15
I can see that sda1 has the boot flag and sda2 should have the boot flag. sda1 is your recovery partition and sda2 is your windows OS partition.

As far as Ubuntu I can't see anything out of the ordinary. Booting to a command line is not necessarily a GRUB issue. Maybe you can post any messages you get when that happens.

To at least try to fix windows boot the Ubuntu Live CD & choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
gksu gparted
``` When gparted loads right click on sda2 and choose Manage Flags. Tick the boot flag at top of list. Click close. Click the green check mark at top toolbar to apply. Reboot without the Live CD.

At the GRUB menu please be aware that your descriptions are reversed for your windows partition. Choose Recovery to boot windows. See why here:
```

# This entry automatically added by the Debian installer for a non-linux OS
[COLOR="Red"]# on /dev/hda1
title        Windows XP Media Center Edition
root        (hd0,0)[/COLOR]
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
[COLOR="Red"]# on /dev/hda2
title        Windows XP (recovery mode)
root        (hd0,1)[/COLOR]
savedefault
makeactive
chainloader    +1
```

Remember sda1 (hd0,0) is your Recovery partition, sda2 (hd0,1) is your Windows OS. So select Windows XP Recovery mode for now because that is your Windows OS (hd0,1). You can fix the title when you get ubuntu up & running. If you still get the hal.dll is missing you are going to have to fix that.

If your Ubuntu boots to a command line you may need to install ubuntu-desktop. Try running that from the command line ```
sudo apt-get install ubuntu-desktop
``` If the ubuntu-desktop is already installed it will let you know.

---

### Post by Banjo_Ben on 2010-03-16
Windows is back!

After using gparted to change the boot flag from partition 1 to partition 2, I still had the "missing or corrupt hal.dll file" error when attempting to reboot, so here is what I did:

Used the script found here:

[HTML]http://vlaurie.com/computers2/downloads/recovery_console_cd.zip[/HTML]together with this file from microsoft:

[HTML]http://www.microsoft.com/downloads/details.aspx?FamilyId=535D248D-5E10-49B5-B80C-0A0205368124&displaylang=en[/HTML]to create a recovery disk for Windows XP Professional SP2 on CD-ROM.  (Microsoft intends the file to be put on six floppies; the script burns the file onto a CD, instead.)  I did this at work today (why risk making my situation worse, when I could put the risk on their  computer, instead?) and it worked flawlessly.

I booted from the recovery disk and ran the recovery console.  In recovery console, I ran the following commands:

```
fixboot
fixmbr
exit
```On reboot, still had the hal.dll error, so back into the recovery console I went.  The "MAP" command showed that, just like when viewed from ubuntu, the FAT32 "recovery" partition was identified as the first partition, the second was the NTFS partition where windows was installed, etc.  Putting that information together with what presence1960 pointed out from my grub menu.lst (that the menu choices for windows and windows recovery mode had been switched), I figured that, when I ran the fdisk experts' "f" command in the ubuntu terminal, it just made partitions 1 and 2 switch places in the table.

The C:\boot.ini file identified windows as having been installed on partition 1, so I just rebooted from the ubuntu live CD, saved a copy of boot.ini, and edited it to change partition 1 to partition 2.  If I were better at using a command line, I could have done that from the windows recovery console.  No matter.  I suppose I also could have gone back into ubuntu and made partitions 1 and 2 switch places in the table, again, as another way to fix it.

On reboot with the CD trays empty, windows booted without a problem.  Of course, now I have no grub menu.  There is a thread on restoring grub here:

[HTML]http://ubuntuforums.org/showthread.php?t=1014708[/HTML]I will pursue that.

When I get grub back and am able to boot into ubuntu, I'm sure I will have questions about how to edit xorg.conf so that X will use some open-source driver for my ATI chipset.

Thank you all very much,
--Banjo_Ben

---

### Post by srs5694 on 2010-03-16
> **Banjo_Ben said:**
> When I get grub back and am able to boot into ubuntu, I'm sure I will have questions about how to edit xorg.conf so that X will use some open-source driver for my ATI chipset.

How recent is your computer? If it's even remotely recent, you may be disappointed in the open source ATI drivers. I've got one system with an on-motherboard ATI Radeon HD 3200 (bought a bit over a year ago, IIRC). I recently tried the open source drivers and they were abysmal. When dragging a window around the screen (even an xterm or something else with static content), the window jumped and jerked around. It felt like I was using something from the early 1990s. Some Googling revealed why: The open source ATI drivers don't support any 2D acceleration features. This is disappointing, since I personally detest all the extra hoops you've got to go through to get the proprietary drivers working -- and continuing to work through X or kernel upgrades! I'm sure the open source drivers will be improved in time. I just hope it's before I retire that computer!

---

### Post by Banjo_Ben on 2010-03-16
grub is back, with the two Windows menu choices working correctly!

I followed the directions for "how to restore the ubuntu grub bootloader (9.04 and older)" from this thread:

[HTML]http://ubuntuforums.org/showthread.php?t=1014708[/HTML]Then, I booted ubuntu from the hard disk (still no X system operating) and, from the command line, I typed:

```
sudo nano /boot/grub/menu.lst
```and managed to fix the identifiers for Windows and Windows (recovery mode) in the menu.

Folks, I correctly identified a file's location, opened a text editor, edited the file (making the correct changes), and saved the file, ALL FROM THE COMMAND LINE.  I hope you'll forgive my excitement at this series of achievements.  Thank you.

Now, as to getting X to work,  I believe that srs5694 is correct:  when I updated the kernel, the proprietary ATI driver I was using quit working.  (presence1960, I did try installing ubuntu-desktop, but it was already installed.)

srs5694, on the subject of open-source ATI drivers, I found this thread:

[HTML]http://ubuntuforums.org/showthread.php?t=1238129&highlight=device+information[/HTML]But, I am still such a command-line neophyte that I don't know exactly what to do next.  My computer is about 3 years old and has an ATI Radeon Express 200 or 300 (I don't recall the command in terminal to identify hardware and devices).  Here are the contents of the /etc/X11/xorg.conf file:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Now, I'm no expert, but that looks practically empty of information, to me.  I believe the proprietary ATI driver, "Catalyst," hasn't been updated for nearly a year, so I'm treating that as a dead end. How, then, to get X working again with an open-source driver?  I'm willing to give up 3D for decent 2D.

Many thanks, again,
--Banjo_Ben

---

### Post by presence1960 on 2010-03-16
For the ati driver you can try this since you are having good success at the command line. Boot into recovery mode. I forget if the following commands need sudo or not. First try them one at a time without sudo:

```
apt-get install envyng-core
apt-get install envyng-qt
apt-get install envyng-gtk
```

Now envyng is installed. Run ```
envyng -t
```Follow the prompts to first uninstall the ATI driver. Once uninstalled follow prompts to install the ATI driver.When completed close envyng & reboot.

---

### Post by Banjo_Ben on 2010-03-16
> **presence1960 said:**
> For the ati driver you can try this since you are having good success at the command line. Boot into recovery mode. I forget if the following commands need sudo or not. First try them one at a time without sudo:
 
```
apt-get install envyng-core
apt-get install envyng-qt
apt-get install envyng-gtk
```
 
Now envyng is installed. Run ```
envyng -t
```Follow the prompts to first uninstall the ATI driver. Once uninstalled follow prompts to install the ATI driver.When completed close envyng & reboot.
 
I want to make sure I understand the effect of executing the code you suggest. Will envyng install the latest version of the ATI proprietary driver? If so, I don't think that will do the trick. According to the AMD/ATI web site, my graphics hardware (ATI Radeon Xpress 200 or 300) is considered "legacy," and the driver hasn't been updated in about a year. That's the driver I was already running when I updated the kernel and/or the X system--the same driver that currently doesn't allow X to draw a working desktop. If envyng installs the latest version of ATI's proprietary driver without regard to the hardware, i.e., the very latest version for the newest card(s), I wouldn't expect that to work, either. I suspect what I might need to do is uninstall the ATI proprietary driver, and replace it with an open-source driver, but I don't know what that entails. I'm guessing some command-line work to uninstall/install, and maybe some editing of the /etc/X11/xorg.conf file, too.
 
Thank you,
--Banjo_Ben

---

### Post by Banjo_Ben on 2010-03-16
I have found documentation about proprietary drivers here:
 
[URL="https://help.ubuntu.com/community/BinaryDriverHowto#ATI%20(fglrx"][HTML] 
https://help.ubuntu.com/community/BinaryDriverHowto#ATI%20(fglrx)
[/HTML][/URL]
and open-source drivers here:
 
[URL="https://help.ubuntu.com/community/RadeonDriver"][HTML] 
https://help.ubuntu.com/community/RadeonDriver
[/HTML][/URL]
 
When I get back to the machine tonight, I'll see what I can accomplish with that information, and I may install envyng as suggested by presence1960 just for the purpose of uninstalling the proprietary ATI driver.
 
If I run into problems, I'll post again, and if I do resolve it, I'll return to mark the thread "[SOLVED]."
 
Thank you,
--Banjo_Ben

---

### Post by srs5694 on 2010-03-16
I'm not familiar with the envyng package that presence1960 suggests you try, so I can't comment on it, although a Web search suggests it's a tool to help detect and install the proprietary ATI and nVidia drivers. I can say this, though: The problem with the proprietary driver you were running and that's now failed isn't with the driver per se; it's that the proprietary driver includes a Linux kernel component. When you installed that driver before, it installed that kernel component *for your old kernel,* and it did so *without using Ubuntu's package manager* (APT). Therefore, when you upgraded your kernel via APT, the ATI driver's kernel component was lost and the driver as a whole stopped working. Therefore, you should be able to get the proprietary driver working again just by re-installing it. This will re-install the kernel component and may upgrade the non-kernel software to a newer version, too. In theory, everything should then start working again.

Your xorg.conf file is nearly empty because modern versions of X do a pretty good job of auto-detecting your hardware and configuring themselves; they need options mainly if you want to override the default settings.

---

### Post by presence1960 on 2010-03-16
> **Banjo_Ben said:**
> I want to make sure I understand the effect of executing the code you suggest. Will envyng install the latest version of the ATI proprietary driver? If so, I don't think that will do the trick. According to the AMD/ATI web site, my graphics hardware (ATI Radeon Xpress 200 or 300) is considered "legacy," and the driver hasn't been updated in about a year. That's the driver I was already running when I updated the kernel and/or the X system--the same driver that currently doesn't allow X to draw a working desktop. If envyng installs the latest version of ATI's proprietary driver without regard to the hardware, i.e., the very latest version for the newest card(s), I wouldn't expect that to work, either. I suspect what I might need to do is uninstall the ATI proprietary driver, and replace it with an open-source driver, but I don't know what that entails. I'm guessing some command-line work to uninstall/install, and maybe some editing of the /etc/X11/xorg.conf file, too.
 
Thank you,
--Banjo_Ben

banjo_ben if your ATI card is legacy you will be better served removing the proprietary driver and installing the open source driver. I had no idea your ATI vid card was "legacy".

---

### Post by Banjo_Ben on 2010-03-16
The latest:

This is the graphics hardware:

```
ubuntu@ubuntu:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200] [1002:5a61]

```I did not install envyng, because ATI identifies this product as "legacy," and apparently is no longer updating the proprietary driver ("Catalyst").

I consulted these sources of information on the open-source driver for ATI:

[HTML]https://help.ubuntu.com/community/RadeonDriver
https://help.ubuntu.com/community/RadeonXpress[/HTML]The first source says that the open-source driver supports my chipset (ATI Radeon Xpress 200). The second source says that "Since Ubuntu 8.10 [which I am running] 3D and desktop effects works out of the box with the open source -ati driver."  I followed the directions in the first link to remove the proprietary "fglrx" driver:

```
sudo apt-get remove --purge xorg-driver-fglrx
```continuing with the instructions from that first link, I verified that

```
glxinfo | grep vendor
```Did not show ATI as the vendor (it shows SGI as the vendor).  The link next suggests:

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```Which produced the error seen in screenshot img-3011, attached.  I tried again, this time adding "--fix-missing" as suggested on-screen, and got the error seen in screenshot img-3012, also attached.  If ftp.usf.edu is no longer a valid source, how do I update my software-sources list from the command line?  How do I find an alternative source, again from the command line?  Could the failure to reinstall these two packages even be the problem?

Typing

```
startx
```at the command line produced the error(s) seen in screenshot img-3010.  I have not yet searched for info on the .Xauthority locking file error, but will do so tomorrow.

Thank you,
--Banjo_Ben

---

### Post by srs5694 on 2010-03-17
The apt-get errors look like you've got a network problem. Try using the "host" command to look up the IP addresses of a few hostnames, such as ubuntuforums.org. ("host ubuntuforums.org"). If you get an error, try using "ping" to see if you've got basic network connectivity to local and remote systems, by IP address. (You'll need to know a few IP addresses to do this -- use "host" or "nslookup" on another computer.) If you can ping local addresses (that is, those on your local network) but not remote addresses, chances are you've got a routing issue. If you can't ping anything at all, your network interface may be down. If you can ping by IP address but not by hostname, your hostname resolution is messed up. (You should be able to add the IP addresses of your DNS servers to /etc/resolv.conf.) If you normally configure your network via DHCP, perhaps your DHCP client isn't running.

---

### Post by Banjo_Ben on 2010-03-17
> **srs5694 said:**
> The apt-get errors look like you've got a network problem. Try using the "host" command to look up the IP addresses of a few hostnames, such as ubuntuforums.org. ("host ubuntuforums.org"). If you get an error, try using "ping" to see if you've got basic network connectivity to local and remote systems, by IP address. (You'll need to know a few IP addresses to do this -- use "host" or "nslookup" on another computer.) If you can ping local addresses (that is, those on your local network) but not remote addresses, chances are you've got a routing issue. If you can't ping anything at all, your network interface may be down. If you can ping by IP address but not by hostname, your hostname resolution is messed up. (You should be able to add the IP addresses of your DNS servers to /etc/resolv.conf.) If you normally configure your network via DHCP, perhaps your DHCP client isn't running.
 
 
I may try this when I get back to the computer tonight, but I don't believe my network connection is the problem.  I can't reach [ftp://ftp.usf.edu](ftp://ftp.usf.edu) from work today, either.  I can get to [http://ftp.usf.edu](http://ftp.usf.edu), so maybe usf made that change.  How can I add/change the software source from the command line?  Or, do I really need to be reinstalling libgl1-mesa-glx and libgl1-mesa-dri at all (what part might they play in the problem)?
 
Thank you,
--Banjo_Ben

---

### Post by srs5694 on 2010-03-17
APT archives are recorded in /etc/apt/sources.list. Check [this page](https://help.ubuntu.com/community/Repositories/CommandLine) for information on managing it from the command line. I don't happen to see anything there about finding repositories if yours has gone away, though. I suppose you could try cutting-and-pasting their examples, though. I know that Synaptic enables you to change, and presents a list of possibilities, but I don't happen to know where that's stored on disk.

---

### Post by Banjo_Ben on 2010-03-18
> **srs5694 said:**
> APT archives are recorded in /etc/apt/sources.list. Check [this page]("https://help.ubuntu.com/community/Repositories/CommandLine") for information on managing it from the command line. I don't happen to see anything there about finding repositories if yours has gone away, though. I suppose you could try cutting-and-pasting their examples, though. I know that Synaptic enables you to change, and presents a list of possibilities, but I don't happen to know where that's stored on disk.
 
That looks like just the source I need.  I didn't get to work on this last night, but am going to try to get to it tonight.
 
Thank you,
--Banjo_Ben

---

### Post by Banjo_Ben on 2010-03-20
> **srs5694 said:**
> The apt-get errors look like you've got a network problem. Try using the "host" command to look up the IP addresses of a few hostnames, such as ubuntuforums.org. ("host ubuntuforums.org"). If you get an error, try using "ping" to see if you've got basic network connectivity to local and remote systems, by IP address. (You'll need to know a few IP addresses to do this -- use "host" or "nslookup" on another computer.) If you can ping local addresses (that is, those on your local network) but not remote addresses, chances are you've got a routing issue. If you can't ping anything at all, your network interface may be down. If you can ping by IP address but not by hostname, your hostname resolution is messed up. (You should be able to add the IP addresses of your DNS servers to /etc/resolv.conf.) If you normally configure your network via DHCP, perhaps your DHCP client isn't running.

There may have been (and may still be) a problem at usf's end re: [ftp://ftp.usf.edu](ftp://ftp.usf.edu), but I believe you're right about my lack of network connectivity, too, srs5694.  I tried "host ubuntuforums.org" and received "connection timed out; no servers could be reached."  I also tried to ping my router by IP address and received, "network is unreachable."

I found what seems to be a good guide here:

[HTML]https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic[/HTML]So I'm going to study that sometime when I can get on the computer a bit earlier in the day.  I've also considered just backing up the /home directory, and reinstalling ubuntu 8.10 on its current partition.

I do appreciate all the help from everyone and will try to follow this through to resolution, rather than letting the thread just fizzle out.

Thank you,
--Banjo_Ben

---

