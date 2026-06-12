---
title: "Windows not booting up after installation"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by mridul on 2005-03-11
I just installed ubuntu and now windows is not booting ... i initially had red hat 9 and replaced it with ubunt .... i need some help plz

thanks
mridul

---

### Post by gungaden on 2005-03-11
What version of Windows and which installation of Ubuntu? What symptoms/messages are you receiving on bootup? Do you get to a black and white screen listing the option to continue the boot process in Windows and Ubuntu? Does it "hang" or do you simply boot into Ubuntu?

---

### Post by Kimm on 2005-03-11
I had a similar problem after I installed Slackware once.
when I tried booting windows it said something like: "Unable to boot Operative System" or something like that, Slackware still booted nicely though. I tried reinstalling windows on the entire Harddrive but that didnt help, I believe Slackware acctualy did something that I didnt realy want it to do to the MBR. of that harddrive...

---

### Post by Buffalo Soldier on 2005-03-11
[QUOTE=mridul]I just installed ubuntu and now windows is not booting ... i initially had red hat 9 and replaced it with ubunt .... i need some help plz

thanks
mridul[/QUOTE]

[list=1]
[*] In which harddisk and partition did you install Ubuntu and Windows?
[*] What is your harddisk setting in BIOS? (Large/Auto/LBA/Normal)
[*] At which part of the boot process that you got stuck?
[*] Any error message?
[*] What's the content of your /boot/grub/menu.lst file?
[/list]

---

### Post by MetalMusicAddict on 2005-03-11
[QUOTE=Buffalo Soldier]
2. What is your harddisk setting in BIOS? (Large/Auto/LBA/Normal)
[/list][/QUOTE]
This seems to ba alot of peoples problem. It was mine. Ide try this 1st. Set the HD access mode in your bios to LBA (Large Block Addressing).

---

### Post by Acyd on 2005-03-11
I'm also having trouble booting Windows Xp now that I have installed Ubuntu...

Here is some info... I NEED HELP!!

   1.  In which harddisk and partition did you install Ubuntu and Windows?
Here is a fdisk output
[COLOR=DarkRed]root@ubuntu:/home/warty # fdisk -l

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1      142227    71681998+   7  HPFS/NTFS
/dev/hdc2          142227      148315     3068415   93  Amoeba
/dev/hdc3          148315      154817     3277260   83  Linux
/dev/hdc4          154817      155056      120487+  82  Linux swap

Disk /dev/hdd: 8037 MB, 8037679104 bytes
16 heads, 63 sectors/track, 15574 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       15555     7839688+   7  HPFS/NTFS[/COLOR]

   2. What is your harddisk setting in BIOS? (Large/Auto/LBA/Normal)
its on Auto right now but I have tried LBA and no luck... 
   3. At which part of the boot process that you got stuck?
I was able to get into the Ubuntu install before and now I am getting a GRUB Error 17... I CANT EVEN GET TO THE GRUB OS SELECT
   4. Any error message?
   5. What's the content of your /boot/grub/menu.lst file?

Here is my menu.lst:
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by mridul on 2005-03-11
[QUOTE=gungaden]What version of Windows and which installation of Ubuntu? What symptoms/messages are you receiving on bootup? Do you get to a black and white screen listing the option to continue the boot process in Windows and Ubuntu? Does it "hang" or do you simply boot into Ubuntu?[/QUOTE]

My Windows version is XP
Ubuntu version 4.10

When i boot XP my monitor displays the following 

Booting XP professional
root (hd0,0)
Filesystem type is fat ,partion type 0xc
chainloader +1

............ and then the system hangs up .....

Ubuntu booting goes well ..........

thanks
mridul

---

### Post by Insanely on 2005-03-12
Hello,

Can someone please help me also. I am having the same problem. I just installed Ubuntu Linux 4.10.
When I try and boot back into my Windows XP partition I get this error:

Booting 'Windows XP'

root (hd0,0)
Filesystem type unknown partition type 0x7

savedefault
makeactive
chainloader +1

The system just stops here. Until I reset it.

After I installed ubuntu I used apt-get to get the latest kernel:
2.6.8.1-5-386

Here is a list of my partition table:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 50793 25599546 7 HPFS/NTFS
/dev/hda2 50794 110472 30078216 c W95 FAT32 (LBA)
/dev/hda3 110473 153100 21484512 83 Linux
/dev/hda4 153101 155061 988344 83 Linux

The parition are all primary partitions ( I don't know if that was the correct thing to do ).

This is my grub version:
grub --version
grub (GNU GRUB 0.95)

This is my menu.1st file:
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color black/yellow yellow/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro noapic

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## ## End Default Options ##

title Ubuntu, kernel 2.6.8.1-5-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.8.1-5-386 root=/dev/hda3 ro noapic quiet splash
initrd /boot/initrd.img-2.6.8.1-5-386
savedefault
boot

title Ubuntu, kernel 2.6.8.1-5-386 (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.8.1-5-386 root=/dev/hda3 ro noapic single
initrd /boot/initrd.img-2.6.8.1-5-386
savedefault
boot

#title Ubuntu, kernel 2.6.8.1-3-386
#root (hd0,2)
#kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda3 ro noapic quiet splash
#initrd /boot/initrd.img-2.6.8.1-3-386
#savedefault
#boot

#title Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
#root (hd0,2)
#kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda3 ro noapic single
#initrd /boot/initrd.img-2.6.8.1-3-386
#savedefault
#boot

title Memory test
root (hd0,2)
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

I am running an Athlon-64 but I am using the i386 install of ubuntu. I had already had my Hard Drive set to LBA. I have no issue booting Ubuntu.
Thank you for any help.

---

### Post by Insanely on 2005-03-13
OK,

I tried to use the windows XP recovery console to fixmbr and fixboot to get back into my windows xp partition. I had no luck. Only had Error Loading Operating System.

So I reformatted my system and created 1 primary partition. The rest are logical. I then installed Ubuntu 5.04 Hoary 

/dev/hda1 = Windows XP (NTFS)
/dev/hda5 = /Home
/dev/hda6 = / (Ubuntu 5.04 Hoary)
/dev/hda7 = SWAP

Grub is working and I have windows xp and ubuntu working smoothly dual boot.

Either warty (4.10) has a boot loader installation bug or does not like 4 primary partitions. Hoary seems a lot better OS anyway. Automatic updates and X.org kill warty for preformance. I have had no issue with it being a beta. Then again it has been only one day!

So here is my fix for people who want windows and ubuntu dual boot.

---

### Post by zukeft on 2005-03-21
[QUOTE=mridul]My Windows version is XP
Ubuntu version 4.10

When i boot XP my monitor displays the following 

Booting XP professional
root (hd0,0)
Filesystem type is fat ,partion type 0xc
chainloader +1

............ and then the system hangs up .....

Ubuntu booting goes well ..........

thanks
mridul[/QUOTE]
I had the **exact** same problem; as said above, changing to Large or LBA should fix your boot problem.

---

### Post by Buffalo Soldier on 2005-03-21
[color=Black][QUOTE=Acyd]fdisk -l:```
[/color][color=Black]Disk /dev/hdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1      142227    71681998+   7  HPFS/NTFS
/dev/hdc2          142227      148315     3068415   93  Amoeba
/dev/hdc3          148315      154817     3277260   83  Linux
/dev/hdc4          154817      155056      120487+  82  Linux swap

Disk /dev/hdd: 8037 MB, 8037679104 bytes
16 heads, 63 sectors/track, 15574 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       15555     7839688+   7  HPFS/NTFS
```[/color]menu.lst:```
# This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/hdc1
 title        Windows NT/2000/XP
 root        (hd0,0)
 savedefault
 makeactive
 chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/hdd1
 title        Windows NT/2000/XP
 root        (hd1,0)
 savedefault
 makeactive
 chainloader    +1
``` [color=Black][/QUOTE]
I notice that you have two entry for Windows in your GRUB menu. Assuming your WinXP is in the first harddisk, try deleting the second entry. If that fails too, try changing [/color][color=Black]** root (hd0,0)** to[/color][color=Black]  **rootnoverify (hd0,0)**.[/color]

---

### Post by alainhenry on 2005-03-22
I have the same problem as described in this thread, windows installed, then Ubuntu.  And then GRUB can't launch windows (or Mandrake, which I installed after Ubuntu).  
I checked my BIOS to turn the LBA flag on, but I have only two choices offered: auto or disabled, there is no way to force LBA manually.  I have a motherboard ASUS P4P800S-X.  
Any other suggestion?

---

### Post by Ubuntu_User on 2005-04-19
Hi!

I get to a black and white screen listing the option to continue the boot process in Windows and Ubuntu, but it doesnt boot nowhere. 

I tried to "fixmbr" then "fixboot" and after that "bootcfg /rebuild". It doesnt help.
I`ve tried to install again ubuntu but it`s doesnt work then too.

---

### Post by alainhenry on 2005-04-20
I am not sure this would apply to your case, but what I did in the end was to put my hard drive in another PC (from which I had removed the other drives), format it with the WinXP installation cdrom (and subsequently instal Win XP on that disk and PC, but that was not important).  then, I put the HD back into the new PC, installed winXP from afresh, and then Ubuntu.  Since then, Everything worked fine.  Apparently, the order of events was important.  I would not claim I understand the logic behind this, but it worked.  Sounds as if Windows does not like to see any other OS on the PC where it installs.  

Alain

---

