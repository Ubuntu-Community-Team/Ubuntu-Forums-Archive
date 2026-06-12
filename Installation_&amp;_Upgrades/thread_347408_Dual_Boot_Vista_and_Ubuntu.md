---
title: "Dual Boot Vista and Ubuntu"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by Penguin Power on 2007-01-27
I installed vista, and then ubuntu edgy eft on a separate partition. Now, Vista won't load, although it shows up in the grub screen when i select i get a blank screen of dead. 

Here's menu.lst, vista already has a +1 next to chainloader as a couple of people have told me to do...
[i]
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=02581a12-6a73-4fe1-9b9b-8eb193fbeed5 ro
# kopt_2_6=root=/dev/sda3 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/I]

---

### Post by aliyanage on 2007-01-27
I am not really sure but I think there was a thread a few weeks ago about this, saying vista is not able to do dual boot with any other OS due to security updates that microsoft has done.

Double check it please but that's  something I've definitely read in the forums but I don't know whether that is really true.


regards
aliyanage

---

### Post by Pobega on 2007-01-27
> **aliyanage said:**
> I am not really sure but I think there was a thread a few weeks ago about this, saying vista is not able to do dual boot with any other OS due to security updates that microsoft has done.

Double check it please but that's  something I've definitely read in the forums but I don't know whether that is really true.


regards
aliyanage

Yeah, I would guess that. Lots of people seem to be having trouble with Vista, and as far as I know no one's been able to solve the problem. It's just Microsoft being Microsoft again.

---

### Post by Penguin Power on 2007-01-27
Well... at least there's another good example of microsoft being monopolising and evil - billion dollar lawsuit anyone? Anyways, if anyone finds anything out about how to dual boot the two give me a shout please :(

---

### Post by unisol on 2007-01-27
is it possible to install ubuntu, then vista, then reinstall the grub loader? or wont that work either?

---

### Post by aliyanage on 2007-01-27
yes true that about the monopolising but also to be honest it is kind of a security bridge. If you do have important or confidential data on your windows it would be an easy one to just boot up with a ubuntu cd and access the windows data and have a look into it...

But I think that's just the reason they were looking for to unable the dual boot :(

---

### Post by Penguin Power on 2007-01-27
Security aside aliyanage it's totally unacceptable - if they wanted to make it more secure they should be using linux's file permissions systems instead of completely blocking it being installed on the same computer.

I heard a rumour about an app on the windows vista dvd hidden stealthily somewhere, but i need a working copy of windows to do it! >.<

I think i might do a repair install of vista to get it working... i wanna play some battlefield 2142 and counter strike source ;p

---

### Post by pvilleSE on 2007-01-28
It is possible to dual boot Vista with Ubuntu, atleast the Business version.  Windows claims you need the Ultimate(or what ever the most expensive version is) but it does work.  But you do have to install Vista first.  I had to actually copy my Ubuntu partition to an external harddrive install vista then copy back to my main harddrive and then reinstall Grub and fix my Grub file.  

I think your problem is that you need to remove the savedefault in the windows section.  That is the only difference between my file and yours and mine works.

Best of luck.  I'll try to check back tomorrow and see if that fixed your problem.

---

### Post by unisol on 2007-02-18
i found this somewhere:Dual-Boot Windows Vista and Linux 
After the installation of Windows Vista, you will want to install Linux. DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to. Also, be sure to specify that GRUB is the bootloader to be installed if this is an option. After installation is completed and you will boot into the Linux operating system that you installed (because GRUB over-wrote the Vista bootloader in the MBR). From here, open up a terminal window (the method of doing so will vary across distrobutions/window managers). After you are at the terminal, all commands that are going to be needed to modify the boot menu will need to be run as 'root' so you will need to know how to accomplish this on your system (su or sudo). The first thing that we will do is backup the current boot menu, which can easily be done by doing this (remember to run this as root): 

Code: 
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 


Next, we need to edit the file "/boot/grub/menu.lst" in the text editor of your choice. You will now want to add an entry for Windows Vista. To do so, you need to add three lines to the file at the end of the file. Example entries follow: 

Vista is installed to the first partition of the first IDE hard drive: 
Code: 
title         "Windows Vista" 
root         (hd0,0) 
chainloader      +1 


Vista is installed to the first partition of the first SATA/SCSI hard drive: 
Code: 
title         "Windows Vista" 
root         (sd0,0) 
chainloader      +1 


If your setup is not the same as either of the examples above, you will need to modify one to match your current setup. The only area that should need modification is the line that starts with "root". The item that will likely need modification is the drive and partition information. For editing the drive that Windows Vista is installed on, you will have to change the first '0' to the number of the drive. If it is the primary or first drive, it will be a '0', the secondary or second drive would be '1', and so on. The same numbering scheme is followed for the partition information, which is the second '0'. First partition on the device is '0', second partition is '1' and so on. If you do not know what drive/partition you should put into the list, you can find this out with a disk or partition management program that may be installed with the system. If you know the device that Vista is installed on, you can also translate that to the GRUB menu. For instance, if Windows Vista is installed to "/dev/hda3" then the "root" entry would be "(hd0,2)" and if the device was "/dev/sdc5" the "root" entry would be "(sd2,4)". A general note here as well, if you have Windows Vista installed to a logical partition within an extended partition, the extended partition counts as a partition. Because of this, what would be thought of as the "second" partition, if it is logical, would actually be the third, as the whole extended partition counts as '1'. If you do not know what the entry should look like, please ask as the only stupid question is the one not asked. It will likely save time and frustration on your part. After you have the file modified, save it and now restart the system to test it out. 

Multi-Boot Windows XP, Windows Vista, and Linux 
The "triple-boot" scenario is actually not difficult, although one might suspect otherwise. The installation sequence is specific though for an easy setup. The installation procedure will be, first, install Windows XP as you normally would. After setup has finished and you are done setting things up the way you want them to be, you will want to install Windows Vista. This will alter the bootloader, and will have the Vista bootloader with an entry for Vista and Legacy OSes (XP and earlier). Once you are done with installing and configuring Windows Vista, you need to install the Linux distribution of your choice. During testing, Ubuntu 6.06 was used, and the GRUB boot menu was properly edited during installation to include an entry for Windows. Although the entry was labelled "Windows XP Professional", when this entry was selected during boot, it would bring up the Windows Vista bootloader and you could then boot either Windows Vista or a legacy operating system. There is a chance however that the installation of Linux will not automatically add an entry for Windows Vista/XP. In such a situation, one should follow the first section about adding an entry for Windows to the GRUB boot menu. 

Installation of Linux before Windows Vista 
While this situation is not the ideal situation, it is not hard to fix. This should just involve re-installing GRUB. This can be done by using the following directions. First, open up the terminal and run the following command as 'root': 
Code: 
grub 

This will bring up the GRUB shell, which will allow you to re-install GRUB. From here, you will need to specify the drive and partition that GRUB is going to be installed (or reinstalled) to. We can do that by using the following command: 
Code: 
root (hd0,1) 

There may be a few changes that need made here depending upon the current setup. First, you need to make sure the drive type is correct. If GRUB is going to be installed to an IDE hard drive, then 'hd', as shown in the example, is going to be used. Otherwise, it will be 'sd', for a SATA or SCSI hard drive. The next item, the '0', is the drive number. Zero (0) specifies that it is the first hard drive in the sequence. If it is the second hard drive, this would be changed to '1' (one) and so on. Keep in mind that numbering starts at '0' so you would take the drive number and decrease it by one for the number used here. The last number, '1' in the example, is the partition where GRUB is to be installed. This partition should be the one that contains the '/boot' directory, and again, numbering of partitions starts at '0', so the above example is installing to the 2nd partition on the physical disk. The last step would be to install GRUB to the MBR, which can be done with the last command: 
Code: 
setup (hd0) 

Which could also require editing, depending on the setup. The drive type would need changed as described above along with the disk number. Since we are installing to the MBR, you will want to specify the drive that currently contains the boot information that is used by Windows Vista. 

From here, we are now done installing GRUB to the MBR and we can exit the GRUB shell by typing: 
Code: 
quit 

After exiting the shell, we can restart the computer and test out to see if the reinstallation of GRUB was successful. If you do not have any entries for Windows, you will need to follow the instructions above in the section on dual-booting as this describes the process of adding Windows Vista/XP to the GRUB boot menu.

---

### Post by bulldog on 2007-02-18
That's a very nice post,thank you.
I'll never use Vista,but I'm sure a lot of people will do, so this is very usefull to them.

I have a remark however,you stated if you use a Sata/Scsi device,you have to use (sd0) instead of (hd0) in your menu.lst.
I'm not sure if that is correct.
In my understanding GRUB makes no difference between IDE and Sata disks,only when pointing to a specific partition it would use sda1 or hda3 or what ever.
But in pointing to a hdd,IDE or Sata,it would use just (hd0),(hd1) and so on.

But I could be totally wrong on this,if so,correct me please.:)

---

### Post by unisol on 2007-02-18
bulldog, i dont use vista either. i triple-boot winxp,ubuntu, and debian etch. i found this on one of the other forums and figured it would help someone. but if i ever get vista for my family, i hope the info is helpful.

---

