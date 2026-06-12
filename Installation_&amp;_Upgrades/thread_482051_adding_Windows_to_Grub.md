---
title: "adding Windows to Grub"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by imaca on 2007-06-23
Hi,
I have a pc which had Ubuntu only installed.
I added an extra hard drive (unplugged ubuntu disk while installing) and installed win98.
I can boot to either by selecting to boot from HD0 or HD1 in bios.

I tried adding windows into grub menu - win disk is 1st partition on hdb so added following menu entry:

title		Windows 98
root		(hd1,0)
makeactive
chainloader	+1

Also added to device.map:
(hd1)   /dev/hdb
(just guessing you might have to do that)

When I select Windows 98 in menu i get:

starting

then nothing happens

Can anyone tell me how to fix this?

---

### Post by feellikeanewman on 2007-06-23
have you tried sudo update grub in a terminal?

---

### Post by reiki on 2007-06-23
Try adding a couple lines to your grub/menu.lst

title Windows 98
root (hd1,0)
[B][COLOR="Red"]map		(hd1) (hd0)
map		(hd0) (hd1)[/COLOR][/B]
makeactive
chainloader +1

That fixed me up here... I have WinXP on an IDE drive and my linux installs are all on Sata drives so my grub menu was getting kinda wonky every time I changed something.

If you start installing onto multiple drives (I now have 3 hard drives in here...) you may also want to learn about using this line in teh grub/menu.lst :

```

configfile   (hd1,0)/boot/grub/menu.lst
```
(that's just a paste from my main grub/menu.lst. Naturally you'd want to point it at the drive containing the menu.lst you want to use so you would adjust "(hd1,0)" to suite your needs)

to have grub on your main boot drive simply look at a grub/menu.lst from another drive. Probably not necessary unless you do a lot of installing and uninstalling, but a nice little trick to have up your sleeve.

---

### Post by logos34 on 2007-06-23
> **imaca said:**
> Hi,
I have a pc which had Ubuntu only installed.
I added an extra hard drive (unplugged ubuntu disk while installing) and installed win98.
I can boot to either by selecting to boot from HD0 or HD1 in bios.

I tried adding windows into grub menu - win disk is 1st partition on hdb so added following menu entry:

title		Windows 98
root		(hd1,0)
makeactive
chainloader	+1

Also added to device.map:
(hd1)   /dev/hdb
(just guessing you might have to do that)

When I select Windows 98 in menu i get:


starting

then nothing happens

Can anyone tell me how to fix this?

You've almost got it.  You correctly added an entry for the new drive to device.map (many forget to do this), but reiki is right in pointing out that you need to add 'map' lines to the win98 entry in menu.lst.  This is because you will be booting first to grub on the linux drive, and to boot **windows on a non-first hard disk** (or 'hd1' as seen by the bios), you must first do a switcheroo to trick windows into thinking it's first in the bios boot order (won't start otherwise).

The only other thing I would do is add a 'savedefault' line to win98 entry, and change the 'default' line near the top of menu.lst to read
> default      **saved**

This will save the last OS you booted into as the new default, meaning it will keep automatically booting into that OS until you specify the other one.  (this is useful in cases where you find yourself booting repeatedly into the non-default OS and don't want to use the keyboard each time to highlight the entry on the menu).

So your win98 entry should look like this:

> title Windows 98
root (hd**[B]1**[/B],0)
[B]map (hd1) (hd0)
map (hd0) (hd1)[/B]
makeactive
**savedefault**
chainloader +1

Note: make sure you put windows entry at the bottom of menu.lst, AFTER the section '### END DEBIAN AUTOMAGIC KERNELS LIST'.  If you put it inside the automagic section, the next time a new kernel is added update-grub will 'boot' it out (pun intended).  

Also, if you haven't already you may want to add an entry to /etc/fstab in order that your fat32 partition mounts automatically in linux:

> **/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0**

Just curious: how big is the drive your installing win 98 on?

---

### Post by imaca on 2007-06-23
Many thanks,
one of the great thing about Ubuntu is the incredibly helpful people in the community:)

---

### Post by madzieph on 2007-06-24
I installed Ubuntu Feisty last night... all went well, except when I tried to boot into Win XP. At first I got the famous NTLDR missing prompt... did some tweaking as suggested in some published forums. Still can´t boot into Win XP.

Read many suggestions already but nothing seems to work... tried reinstalling Ubuntu Feisty... still Win XP won't boot...

It will boot when I change the boot priority in the CMOS settings and have the disk with the Win XP loaded set as primary.

Tried tweaking the boot loader with Super Grub... but still can't seem to boot... didn't really go on much farther with the Super Grub because I might damage the Win XP installation...


**My scenario:**

I got 4 HDDs with the following details:

SDA = 40 GB Primary Master IDE Maxtor where Ubuntu is installed
SDB = 40 GB Primary Slave IDE Maxtor in NTFS with my files
SDC = 160 GB Fourth Master SATA in NTFS as backup data storage
SDD = 37 GB Seagate SCSI where Win XP is installed

heres the result of** fdisk -l**

madzieph@madzlinux:~$ sudo fdisk -l
Password:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 365 2931831 83 Linux
/dev/sda2 366 377 96390 83 Linux
/dev/sda3 378 4998 37118182+ 5 Extended
/dev/sda5 378 742 2931831 83 Linux
/dev/sda6 743 864 979933+ 82 Linux swap / Solaris
/dev/sda7 865 1229 2931831 83 Linux
/dev/sda8 1230 2566 10739421 83 Linux
/dev/sda9 2567 4998 19535008+ b W95 FAT32

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 4997 40138371 7 HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 19928 160071628+ 7 HPFS/NTFS

Disk /dev/sdd: 36.7 GB, 36703934464 bytes
255 heads, 63 sectors/track, 4462 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 3060 24579418+ 7 HPFS/NTFS
/dev/sdd2 3061 4461 11253532+ f W95 Ext'd (LBA)
/dev/sdd5 3061 4461 11253501 7 HPFS/NTFS

**/boot/grub/device.map**

(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc
(hd3) /dev/sdd

**/boot/grub/menu.lst**

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-lowlatency
root (hd0,1)
kernel /vmlinuz-2.6.20-16-lowlatency root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro quiet splash
initrd /initrd.img-2.6.20-16-lowlatency
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
root (hd0,1)
kernel /vmlinuz-2.6.20-16-lowlatency root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro single
initrd /initrd.img-2.6.20-16-lowlatency

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)
kernel /vmlinuz-2.6.20-16-generic root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro quiet splash
initrd /initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,1)
kernel /vmlinuz-2.6.20-16-generic root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro single
initrd /initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.20-15-lowlatency
root (hd0,1)
kernel /vmlinuz-2.6.20-15-lowlatency root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro quiet splash
initrd /initrd.img-2.6.20-15-lowlatency
quiet
savedefault

##title Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode)
##root (hd0,1)
##kernel /vmlinuz-2.6.20-15-lowlatency root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro single
##initrd /initrd.img-2.6.20-15-lowlatency

##title Ubuntu, kernel 2.6.20-15-generic
##root (hd0,1)
##kernel /vmlinuz-2.6.20-15-generic root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro quiet splash
##initrd /initrd.img-2.6.20-15-generic
##quiet
##savedefault

##title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
##root (hd0,1)
##kernel /vmlinuz-2.6.20-15-generic root=UUID=6bb9b912-ebce-47ea-950b-74981f9b6271 ro single
##initrd /initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,1)
kernel /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows XP Professional
rootnoverify (hd3,0)
savedefault
makeactive
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1


Sorry for the long post...

Thanks in advance...

---

### Post by madzieph on 2007-06-24
Am thinking of using lilo and install that to the MBR of the disk where Win XP is installed...

Or perhaps install Grub there... 

but am kinda hesitant to do so for fear of destroying my Win XP installation... it takes a lot of time to reinstall everything... tsk tsk tsk

will that be possible? am surmising that since in the BIOS settings, I choose the disk with Ubuntu and the primary boot disk and I can only have 1 hdd as a choice for the booting sequence (just correct me if I'm wrong)...

thanks again... sorry for hijacking this thread..

---

### Post by logos34 on 2007-06-24
> Sorry for the long post...

thanks again... sorry for hijacking this thread..

No, that's quite alright.  Personally I wish everyone would not be shy about posting everything up front--makes it easier to see what's going on. Good troubleshooting practice.  However it might be best to start up a new thread to get as much input as possible because I don't know why windows isn't coming up. 

I can't spot any obvious errors in your config files.  Your device map corresponds to your menu.lst and fdisk, and windows entry in menu,lst looks perfect--map lines and everything (Looks like you changed it to 'rootnoverify' trying to fix the problem.).  Unless sdd5 is another active, bootable windows partition (in which case you'd have to use 'hide' options), windows on sdd1 should boot.   

The only thing I can think of is: did you change the position of sdd in the BIOS?  Because if you moved it up in the list, it may now be '(hd1)' or '(hd2)'.  (sda is still the first drive, (hd0), the one you boot to grub on).  You could try editing device.map, changing the windows disk entry '(hd3) /dev/sdd' to (hd2) or (hd1).  Then change the menu.lst windows entry accordingly.
 
That's all I can think of.
________________

---

### Post by confused57 on 2007-06-24
> **madzieph said:**
> Am thinking of using lilo and install that to the MBR of the disk where Win XP is installed...

Or perhaps install Grub there... 

but am kinda hesitant to do so for fear of destroying my Win XP installation... it takes a lot of time to reinstall everything... tsk tsk tsk

will that be possible? am surmising that since in the BIOS settings, I choose the disk with Ubuntu and the primary boot disk and I can only have 1 hdd as a choice for the booting sequence (just correct me if I'm wrong)...

thanks again... sorry for hijacking this thread..
Your problem is very similar to the issues of the OP in this thread:
[http://ubuntuforums.org/showthread.php?t=450329&page=3](http://ubuntuforums.org/showthread.php?t=450329&page=3)

---

### Post by logos34 on 2007-06-24
> **confused57 said:**
> Your problem is very similar to the issues of the OP in this thread:
[http://ubuntuforums.org/showthread.php?t=450329&page=3](http://ubuntuforums.org/showthread.php?t=450329&page=3)

Oh, so then it's the **boot.in**i file that needs to be changed...

default=multi(0)disk(0)rdisk([COLOR="Red"]**3**[/COLOR])partition([COLOR="Red"]**1**[/COLOR])\WINDOWS  [edit]

Is that how you see it Confused57?

---

### Post by confused57 on 2007-06-24
> **logos34 said:**
> Oh, so then it's the **boot.in**i file that needs to be changed...

default=multi(0)disk(0)rdisk([COLOR="Red"]**3**[/COLOR])partition([COLOR="Red"]**1**[/COLOR])\WINDOWS  [edit]

Is that how you see it Confused57?
I've never personally edited my boot.ini file, but I was wondering if he could add your suggestion as an additional boot entry to his boot.ini & see if it works...I'm hesitate to offer specific advice for editing boot.ini, especially since I don't have any experience with it...would adding the second entry give a menu in the Window's bootloader to choose which to boot?

---

### Post by logos34 on 2007-06-24
> **confused57 said:**
> I've never personally edited my boot.ini file, but I was wondering if he could add your suggestion as an additional boot entry to his boot.ini & see if it works...I'm hesitate to offer specific advice for editing boot.ini, especially since I don't have any experience with it...would adding the second entry give a menu in the Window's bootloader to choose which to boot?

yeah, a menu should pop up with a choice (mine has mult. entries and it does).  so that might be the way to go.

---

### Post by madzieph on 2007-06-24
> **confused57 said:**
> Your problem is very similar to the issues of the OP in this thread:
[http://ubuntuforums.org/showthread.php?t=450329&page=3](http://ubuntuforums.org/showthread.php?t=450329&page=3)

Thanks for the link... we really are on the same boat...

am reading it now... kinda confusing but will try to make something out of it...

---

### Post by logos34 on 2007-06-24
madzieph,

can you just quickly post your boot.ini file?  We were just wondering if maybe that was the problem and you could edit that to get windows to boot...it seems to be a ntldr, not grub, problem since it gets that far.

boot.ini is on C:\ 

if you don't see it in nautilus enable view> 'show hidden files' option

---

### Post by madzieph on 2007-06-24
> **logos34 said:**
> 
The only thing I can think of is: did you change the position of sdd in the BIOS?  Because if you moved it up in the list, it may now be '(hd1)' or '(hd2)'.  (sda is still the first drive, (hd0), the one you boot to grub on).  You could try editing device.map, changing the windows disk entry '(hd3) /dev/sdd' to (hd2) or (hd1).  Then change the menu.lst windows entry accordingly.
 
That's all I can think of.

When I tried changing the position of sdd to be the first boot disk, Windows would come up and boots fine... 

It was kinda easier with LILO before (when I was installing Mandriva Spring Free) because there was an option if I wanted to place LILO in the MBR of the Win XP drive... didnt find that option in Grub.

However, Mandriva was so unstable in my system so I tried other flavors and came up with Ubuntu which runs very stably but sadly I cant load Win XP in Grub...

---

### Post by madzieph on 2007-06-24
> **logos34 said:**
> madzieph,

can you just quickly post your boot.ini file?  We were just wondering if maybe that was the problem and you could edit that to get windows to boot...it seems to be a ntldr, not grub, problem since it gets that far.

boot.ini is on C:\ 

if you don't see it in nautilus enable view> 'show hidden files' option

Here&#347; my boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by logos34 on 2007-06-24
> ...didnt find that option in Grub.

Must have used the live cd, in which case I'm not surprised because it's not clearly mearked (you used to have to click on the 'hd0' button to change it; in feisty I think you click 'advanced' at the bottom of the screen).  

Well at least we know that win bootloader is alive and well on sdd.  So it looks like Confused57 was right on target with the link suggestion and the cultprit is boot.ini.

Try changing it to what I wrote in post #10, or do like confused57 suggested and just add another line:
> multi(0)disk(0)rdisk(3)partition(1)\WINDOWS="Microsoft Windows XP Professional(2)" /fastdetect /NoExecute=OptIn

Then change it back in the boot order to what it was and boot to grub and choose windows.

---

### Post by madzieph on 2007-06-24
> **logos34 said:**
> Must have used the live cd, in which case I'm not surprised because it's not clearly mearked (you used to have to click on the 'hd0' button to change it; in feisty I think you click 'advanced' at the bottom of the screen).  

Well at least we know that win bootloader is alive and well on sdd.  So it looks like Confused57 was right on target with the link suggestion and the cultprit is boot.ini.

Try changing it to what I wrote in post #10, or do like confused57 suggested and just add another line:


Then change it back in the boot order to what it was and boot to grub and choose windows.

Will give it a try...

BTW, just a quick question... **does Ubuntu follow the drive ordering in the BIOS**? 

My BIOS drive order is

[B]Primary Master [40 GB IDE where Ubuntu is]
SCSI [where Win XP is]
Secondary Master [40 GB IDE]
SATA[/B]

which makes the SCSI drive hdd1 but it&#347; HDD/SDD 3 in Grub...

---

### Post by logos34 on 2007-06-24
> does Ubuntu follow the drive ordering in the BIOS?

My BIOS drive order is

Primary Master [40 GB IDE where Ubuntu is]
SCSI [where Win XP is] -->[**SDD = 37 GB Seagate SCSI where Win XP is installed**]
Secondary Master [40 GB IDE]
SATA

which makes the SCSI drive hdd1 but it&#347; HDD/SDD 3 in Grub...

wait, you're mixing grub notation and linux...linux sees the scsi winxp drive as 'sdd' (fourth drive), and the IDE as 'sda' (first drive)--not 'hda'--because Feisty is using the new libata scsi subsystem drivers to denote drives (everything is 'sdx')...Bur grub uses the 'hdx' notation for everyhting (starting with hd0), regardless of whether its des, sata, usb, etc.  

Just change it back to the exact order it was at install time and try it.

---

### Post by madzieph on 2007-06-24
> **logos34 said:**
> Must have used the live cd, in which case I'm not surprised because it's not clearly mearked (you used to have to click on the 'hd0' button to change it; in feisty I think you click 'advanced' at the bottom of the screen).  

Well at least we know that win bootloader is alive and well on sdd.  So it looks like Confused57 was right on target with the link suggestion and the cultprit is boot.ini.

Try changing it to what I wrote in post #10, or do like confused57 suggested and just add another line:


Then change it back in the boot order to what it was and boot to grub and choose windows.

tried as suggested... didnt work :(  still got the missing NTLDR prompt...

now am stuck that Win XP wont boot coz it tries to look for the boot files at drive #4 [rdisk (3) partition (1)]....

I edited the boot.ini at Win XP... **any idea how to edit it in Linux? boot.ini is read-only even when I am in root... the whole partition is read-only....**:(

---

### Post by logos34 on 2007-06-24
> does Ubuntu follow the drive ordering in the BIOS?

to answer your question better:
it is more correct to say that GRUB follows the drive ordering in the Bios...which is why when you switch hard disk boot order in the bios it screws everything up.

---

### Post by logos34 on 2007-06-24
> tried as suggested... didnt work  still got the missing NTLDR prompt...

now am stuck that Win XP wont boot coz it tries to look for the boot files at drive #4 [rdisk (3) partition (1)]....

I edited the boot.ini at Win XP... any idea how to edit it in Linux? boot.ini is read-only even when I am in root... 

darn

edit: sorry, forgot you may not have ntfs-3g!  I do that a lot...might want to get it--gives write access to ntfs in linux. great tool

sudo apt-get install ntfs-3g ntfs-config

---

### Post by logos34 on 2007-06-25
> now am stuck that Win XP wont boot coz it tries to look for the boot files at drive #4 [rdisk (3) partition (1)]....

unless i'm mistaken 'rdisk (3) partition (1)' should work IF the drive is listed last in the bios hard disk boot priority.

Grub windows entry is 'root (hd3, 0)' / sdd1-- the fourth and last disk in the chain.  So we're just editing boot.ini to point to the first partition on the fourth disk, '3, 1' -- windows, like grub, starts counting devices with '0', but differs by counting partitions starting with '1'. 

ok, so maybe try 'rdisk (1)' or 'rdisk (2)'...

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> unless i'm mistaken 'rdisk (3) partition (1)' should work IF the drive is listed last in the bios hard disk boot priority.

Grub windows entry is 'root (hd3, 0)' / sdd1-- the fourth and last disk in the chain.  So we're just editing boot.ini to point to the first partition on the fourth disk, '3, 1' -- windows, like grub, starts counting devices with '0', but differs by counting partitions starting with '1'. 

ok, so maybe try 'rdisk (1)' or 'rdisk (2)'...

I was thinking about this before I read your post... so what I did was:

1. Change the order of the drives in my bios to:

PM [Ubuntu]
PS [files]
4S [sata drive]
05 [scsi win xp]

2. Booted using PM as primary boot device:

3. Choose Win XP to boot in Grub.

4. Got this prompt:
Windows could not start because the following file is missing:
<Windows root>\System32\hal.dll
Please reinstall a copy of the above file.

Am I going somewhere with this? :D

---

### Post by logos34 on 2007-06-25
> Am I going somewhere with this?

lol, yes but not exactly where we planned.

Well, I thought for sure that would work.  'hal.dll'...why the fock that message?   

Look, we've gotta be close and I hope it's clear to you basically what we're trying to do.  Or maybe I haven't explained well enough, i don't know. Grub is not the problem (at least I don't think); it's windows ntldr and boot.ini that are wrong.   

Did you try all three possibilites--rdisk (3), rdisk (2), rdisk (1) ? 

IF the boot order is back the way it was originally--which is what it appears to be--then one of these variations should work.  Unless the mapping is causing a problem.

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> l

Did you try all three possibilites--rdisk (3), rdisk (2), rdisk (1) ? 

IF the boot order is back the way it was originally--which is what it appears to be--then one of these variations should work.  Unless the mapping is causing a problem.

problem is, I still can't edit boot.ini... can't access the drive when I try to boot using a DOS disk... haven't tried booting WinXP CD yet but will try that as last resort (might do more damage to the MBR... still hoping to edit boot.ini in Linux...

installed the ntfs-3g but **the partition where boot.ini is still in read-only** even with root... **can't change permissions also**...

I get the prompt:

[I][B]"The permissions could not be changed.

Couldnt change the permissions of "System" because it is on a read-only disk."[/B][/I]

I won't be able to go back to windows (by directly booting into it) because  as expected, Windows would always like to be the first drive and it won't boot because boot.ini is still pointing to drive 4 [rdisk (3) partition (0)]

---

### Post by logos34 on 2007-06-25
> problem is, I still can't edit boot.ini

installed the ntfs-3g but the partition where boot.ini is still in read-only even with root... can't change permissions also...

oh, ok, then just do 
[B]
sudo ntfs-config[/B] 

and tick the box to enable write support for internal devices.

Then reboot.  Now see if it works.

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> oh, ok, then just do 
[B]
sudo ntfs-config[/B] 

and tick the box to enable write support for internal devices.

Then reboot.  Now see if it works.

**still read-only...** :(

---

### Post by logos34 on 2007-06-25
ok,,let's see your fstab.  post it please.

But I really need to go soon.  Can we pick this up tomorow?  We'll get this fixed so help me. Maybe confused57 will have a suggestion.

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> ok,,let's see your fstab.  post it please.

But I really need to go soon.  Can we pick this up tomorow?  We'll get this fixed so help me. Maybe confused57 will have a suggestion.

no problem... tomorrow then... am trying to boot winxp cd to do a recovery first... good thing, i got this other pc working... otherwise am dead..

thanks a lot...

Ubuntu community really is great... :D

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> ok,,let's see your fstab.  post it please.

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=04accfed-b079-41cf-8db8-d82b9000a179 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=af570503-b20f-4422-ba28-b2a0af4b408e /boot ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=1d613905-2258-4ec5-8995-44ef33c830c0 /home ext3 defaults 0 2
# Entry for /dev/sdb1 :
UUID=DE747D74747D506F /mnt/data01 ntfs-3g defaults,locale=en_PH.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=355A-CA09 /mnt/data02 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdc1 :
UUID=94E8378FE8376F1C /mnt/sata ntfs-3g defaults,locale=en_PH.UTF-8 0 1
# Entry for /dev/sdd5 :
UUID=04CC2E75CC2E6162 /mnt/win_installers ntfs-3g defaults,locale=en_PH.UTF-8 0 1
# Entry for /dev/sda8 :
UUID=257bb79d-c782-47a0-9334-1b9056fb450f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by madzieph on 2007-06-25
Oh my bad...

I guess I see what&#347; wrong... the partition <System> which is my Win XP partition is not here... now how do I put it in fstab?

---

### Post by madzieph on 2007-06-25
> **madzieph said:**
> Oh my bad...

I guess I see what&#347; wrong... the partition <System> which is my Win XP partition is not here... now how do I put it in fstab?

Got it... run ntfs-config again... and here&#347; **fstab** now....

[SIZE=1]# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=04accfed-b079-41cf-8db8-d82b9000a179 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=af570503-b20f-4422-ba28-b2a0af4b408e /boot ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=1d613905-2258-4ec5-8995-44ef33c830c0 /home ext3 defaults 0 2
# Entry for /dev/sdb1 :
UUID=DE747D74747D506F /mnt/data01 ntfs-3g defaults,locale=en_PH.UTF-8 0 1
# Entry for /dev/sda6 :
UUID=355A-CA09 /mnt/data02 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdc1 :
UUID=94E8378FE8376F1C /mnt/sata ntfs-3g defaults,locale=en_PH.UTF-8 0 1
# Entry for /dev/sdd5 :
UUID=04CC2E75CC2E6162 /mnt/win_installers ntfs-3g defaults,locale=en_PH.UTF-8 0 1
# Entry for /dev/sda8 :
UUID=257bb79d-c782-47a0-9334-1b9056fb450f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sdd1 /media/System ntfs-3g defaults,locale=en_PH.UTF-8 0 0

[SIZE=2]Now, to get a copy of the hal.dll ... and try to boot win xp....

[SIZE=3][COLOR=Red]Ubuntu Community really is GREEEEEEEEEAAAAAAAAAAATTTTTTTTTTTT!!!!!![/COLOR][/SIZE]
[/SIZE][/SIZE]

---

### Post by logos34 on 2007-06-25
i'm back for just a minute.

Well, at least sdd1 mounted...was beginning to wonder.

So, wait, before you get hal.dll, 

You've tried the rdisk (3)--edited frm windows the first time--but not the other two?  and it threw that error last time

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> i'm back for just a minute.

Well, at least sdd1 mounted...was beginning to wonder.

So, wait, before you get hal.dll, 

You've tried the rdisk (3)--edited frm windows the first time--but not the other two?  and it threw that error last time

yup... got it edited in windows...

I was able to edit it only once because after that I could not log on to windows anymore...

---

### Post by madzieph on 2007-06-25
I am guessing that I am already entering the proper partition where windows is... the only thing is that there seems to be some trouble with boot.ini and hal.dll ... doing some reading about this now...

---

### Post by logos34 on 2007-06-25
could rootnoverify be causing a problem?  i don't know, but maybe try changing menu.lst back to original, 
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows XP Professional
**root** (hd3,0)  
savedefault
makeactive
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

and then with boot.ini set as as 'rdisk (3) partition(1) try it once more.

Then if negative, we can try towmorrow other variations...But at least at this point you can use ubuntu AND have write access to windows partitions.

---

### Post by logos34 on 2007-06-25
> **madzieph said:**
> I am guessing that I am already entering the proper partition where windows is... the only thing is that there seems to be some trouble with boot.ini and hal.dll ... doing some reading about this now...

yeah, agreed, you're getting there, it's just some small pointing error which is causing the hal.dll stuff...Clarify: did it mess up the winxp bootloader so you can't boot to it direct like you did before?  If not, don't try to fix hal.dll yet.

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> yeah, agreed, you're getting there, it's just some small pointing error which is causing the hal.dll stuff...Clarify: did it mess up the winxp bootloader so you can't boot to it direct like you did before?  If not, don't try to fix hal.dll yet.

am checking this out in a while... seems that I can't access the win xp partition again after a reboot...

---

### Post by madzieph on 2007-06-25
Set the boot.ini back to rdisk (0) partition (1)...

Changed bios boot sequence to Win XP partition as first boot drive....

Win XP boots perfectly...

back to square one again... How to make Win XP installation in drive 4 boot in GRUB...

whew!!! at least I got the xp back for now...

---

### Post by confused57 on 2007-06-25
Wow, you guys were busy last night...logos34, great advice using NTFS-3G to get Windows booting again.

madzieph, you might want to read over this page for common Window's error messages:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Common_Booting_Errors_and_Some_Possible)

You might want to check out this utility & make a floppy or cd, then if you try some different boot.ini entries, this should get you back into Windows:
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
although you were able to repair boot.ini from Linux, still may be a good idea to have a copy on disk

I read back over the thread of the person who was having similar problems and was wondering if you made your Ubuntu drive first in bios and your Window's drive second...add a 2nd Window's entry to menu.lst:
```
title              Windows XP test
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
see if it works or not, won't hurt to add this 2nd entry temporarily.

Here's a thread with how to edit your menu.lst:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by madzieph on 2007-06-25
[SIZE=1]*Wow, you guys were busy last night...logos34, great advice using NTFS-3G to get Windows booting again.*[/SIZE]

[COLOR=Green] logos34 was really much help... though I still got problems with the booting, I learned a lot... kudos to the Ubuntu Community...[/COLOR]

[SIZE=1] madzieph, you might want to read over this page for common Window's error messages:
[http://users.bigpond.net.au/hermanzo...  ome_Possible]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Common_Booting_Errors_and_Some_Possible")[/SIZE] 

[COLOR=Green] this reading really confuses me... i guess it is directed toward the problem if one is not able to boot into Windows which I can... with the switching of boot drives in the bios settings.[/COLOR]

[SIZE=1] You might want to check out this utility & make a floppy or cd, then if you try some different boot.ini entries, this should get you back into Windows:
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
although you were able to repair boot.ini from Linux, still may be a good idea to have a copy on disk[/SIZE] 

[COLOR=Green] Actually, I had the SGD already burned to CD... the menu choices are confusing me for now so I put it aside as my last option. Still trying to understand the descriptions of each command through the Help Menus but descriptions are quite cryptic to me.. still has to read more before I dare...[/COLOR] ;)
[SIZE=1]
I read back over the thread of the person who was having similar problems and was wondering if you made your Ubuntu drive first in bios and your Window's drive second...add a 2nd Window's entry to menu.lst:
[/SIZE]      [SIZE=1]Code:[/SIZE]
     [SIZE=1]title              Windows XP test
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1[/SIZE] 
[SIZE=1]see if it works or not, won't hurt to add this 2nd entry temporarily.[/SIZE]

Tried it to no avail... I even added another option to test hd2...

[COLOR=Green] As was mentioned in one of my earlier post...[/COLOR][COLOR=Green][COLOR=Blue] I was already able to get past the Missing NTLdr prompt and got into the "Missing or corrupted Hal.dll"[/COLOR] [/COLOR][COLOR=Black][COLOR=Green]which to my understanding puts me a step forward. It's just that when I boot into windows with the windows partition chosen as the first drive in the bios, I am able to boot windows flawlessly, which again implies that hal.dll is not missing nor corrupt.[/COLOR]

[COLOR=Blue]Would you suggest that I uninstall GRUB and install Lilo in the MBR of the windows drive? Sadly, I will lose the splash scree features of Grubl :([/COLOR]

[COLOR=DarkGreen] Never had problems with this when I was using Mandriva Free. Lilo booted both Windows and Mandriva perfectly and when I uninstalled Mandriva, uninstalled Lilo and simply run fdisk /mbr to restore the MBR of the windows partition/disk.[/COLOR]
[/COLOR]

---

### Post by confused57 on 2007-06-25
Another option that "might" work is the GAG bootloader:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

You could make a GAG boot floppy or cd, see if it can boot your Window's drive...if it does, you might consider installing it to your Ubuntu drive's mbr...to boot Ubuntu, you'd need grub installed to Ubuntu's root partition...you can do this with the live cd, see instructions in the link.

Added:  You might try changing your device.map when changing the bios hard drive boot order:
```
(hd0) /dev/sda
(hd1) /dev/sdd
```

if you try this:
> I read back over the thread of the person who was having similar problems and was wondering if you made your Ubuntu drive first in bios and your Window's drive second...add a 2nd Window's entry to menu.lst:
Code:
title Windows XP test
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
see if it works or not, won't hurt to add this 2nd entry temporarily.

I've read other posters report that this worked for them.

---

### Post by logos34 on 2007-06-25
> It's just that when I boot into windows with the windows partition chosen as the first drive in the bios, I am able to boot windows flawlessly, which again implies that hal.dll is not missing nor corrupt.

Just as I suspected.  So no need to go messing with hal.dll because you can still boot straight into windows fine.  So the mbr is ok.

Confused57's suggestion to try (hd1,0) is what I was thinking too...I mean windows boots from the second drive via grub almost all the time using the mapping switch, I thought maybe it was just having to much trouble dealing with a drive in fourth position. But even that doesn't work, nor does (hd2,0)...Maybe there's something else in boot.ini we can add or take out..

Wait--when you tried the above 'to no avail' (hd1,0) and (hd2,0), did you also change DEVICE.MAP?  i.e. 

(hd**1**) /dev/sdd

---

### Post by confused57 on 2007-06-25
> **logos34 said:**
> Just as I suspected.  So no need to go messing with hal.dll because you can still boot straight into windows fine.  So the mbr is ok.

Confused57's suggestion to try (hd1,0) is what I was thinking too...I mean windows boots from the second drive via grub almost all the time using the mapping switch, I thought maybe it was just having to much trouble dealing with a drive in fourth position. But even that doesn't work, nor does (hd2,0)...Maybe there's something else in boot.ini we can add or take out..

Wait--when you tried the above 'to no avail' (hd1,0) and (hd2,0), did you also change DEVICE.MAP?  i.e. 

(hd**1**) /dev/sdd

I must have been editing my post when you replied with your suggestion to change the device.map...hopefully, it will work.

I thought it would be a good idea to have a copy of the NTLDR repair cd, if he decides to edit his boot.ini:
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
it's intended to be burned on a working Window's installation, but might come in handy...even if he's able to restore his boot.ini through Linux

---

### Post by logos34 on 2007-06-25
And you would change boot.ini back to original:
> **rdisk(0),partition(1)**

because that is how it works with otherwise in dual-boot, dual-drive setups in which you grub boots windows on a non-first hard disk--we never have to mess with boot.ini.  Am I right or do I need some more coffee?

---

### Post by logos34 on 2007-06-25
> I thought it would be a good idea to have a copy of the NTLDR repair cd, if he decides to edit his boot.ini:
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

yeah good idea

---

### Post by confused57 on 2007-06-25
> **logos34 said:**
> And you would change boot.ini back to original:


because that is how it works with otherwise in dual-boot, dual-drive setups in which you grub boots windows on a non-first hard disk--we never have to mess with boot.ini.  Am I right or do I need some more coffee?
I agree that he shouldn't have to edit his boot.ini...by the way, great job helping get his Windows working again.  

Sounds like a good idea, believe I'll have another cup of coffee.

---

### Post by madzieph on 2007-06-25
[SIZE=1] Wait--when you tried the above 'to no avail' (hd1,0) and (hd2,0), did you also change DEVICE.MAP?  i.e. 

(hd**1**) /dev/sdd[/SIZE] 

Was thinking about this before I closed my eyes to sleep last night but was already too sleepy.... :)

After having a quick read of your replies as soon as I got up... I finally got the idea... so this is what I did:

[B][COLOR=Blue]1. Edited device.map to this:

[/COLOR][/B][COLOR=DarkGreen](hd0)    /dev/sda
**(hd1)    /dev/sdd**
(hd2)    /dev/sdb
(hd3)    /dev/sdc[/COLOR]

**[COLOR=Blue]2. Edited menu.lst to this:[/COLOR]** [COLOR=Blue]*[SIZE=1](just copied the revisions to make the post shorter)[/SIZE]*[/COLOR]

[COLOR=DarkGreen]title        Microsoft Windows XP Professional SP2
[B]root        (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
savedefault
makeactive
chainloader    +1[/COLOR]

**[COLOR=Blue]3. Rebooted, changed my drive ordering to this:[/COLOR]**
[COLOR=DarkGreen]
Primary Master [Ubuntu drive]
**SCSI [Windows XP drive] ***[SIZE=1](as originally where it was during Ubuntu setup)[/SIZE]*
Secondary Master [Data Storage]
4th Master [SATA Storage Drive][/COLOR]
[COLOR=Red][B]
FINALLY, Houston WE HAVE LIFT OFF....

I was able to boot both Ubuntu and Windows flawlessly!!!!

Thanks a million guys!!!

[SIZE=5]Ubuntu Rules!!!![/SIZE]
[/B][/COLOR]

---

### Post by logos34 on 2007-06-25
That's great!

So now we know it works as it is supposed to -- i.e. windows in second position using the mapping switch.  

I thought that device,map must have had something to do with it--you know, you were so close and had eveyhting else right that it was just some small oversight somewhere.  

You persistence is really impressive--most people would have thrown in the towel a long time ago.  I was sure ready to!

Kudos to confused57 for the links about boot.ini and assistence--who knows, you might still be sitting here with 'hal.dll' error staring at you!  I still have a lot to learn but that part is becoming a little clearer (I think).

So enjoy!

P.S.--Tomorrow we can sort out trying to get it to boot from LAST position in the bios order!  ;-) lol!

---

### Post by madzieph on 2007-06-25
> **logos34 said:**
> P.S.--Tomorrow we can sort out trying to get it to boot from LAST position in the bios order!  ;-) lol!

Yeah.... been thinking about that... maybe later :D

for now, I&#314;l have to see what I can do here... check out whether am finally ready to trash Bill Gates :D:D:D

---

### Post by confused57 on 2007-06-25
> **logos34 said:**
> That's great!

So now we know it works as it is supposed to -- i.e. windows in second position using the mapping switch.  

I thought that device,map must have had something to do with it--you know, you were so close and had eveyhting else right that it was just some small oversight somewhere.  

You persistence is really impressive--most people would have thrown in the towel a long time ago.  I was sure ready to!

Kudos to confused57 for the links about boot.ini and assistence--who knows, you might still be sitting here with 'hal.dll' error staring at you!  I still have a lot to learn but that part is becoming a little clearer (I think).

So enjoy!

P.S.--Tomorrow we can sort out trying to get it to boot from LAST position in the bios order!  ;-) lol!
I think it was certainly a "tag-team" effort...it seems I learn something new every day about Linux & Ubuntu and I'm enjoying every minute of it.

madzieph,
   Great to hear you got your dual boot working...you'll definitely be an asset around here.  I'm sure you'll enjoy it as much as I have for the past 18 months.

---

### Post by madzieph on 2007-06-25
> **confused57 said:**
> I think it was certainly a "tag-team" effort...it seems I learn something new every day about Linux & Ubuntu and I'm enjoying every minute of it.

madzieph,
   Great to hear you got your dual boot working...you'll definitely be an asset around here.  I'm sure you'll enjoy it as much as I have for the past 18 months.

Thanks for all your help...

I know I will enjoy my stay here...

---

### Post by TXBDan on 2007-06-26
Hey guys,

I'm also trying to get my Windows XP to boot. If you have some time, please take a look. :)

Here is my situation:

I have windows XP installed on my only SATA HD. 

I also have an IDE HD that used to be an old windows install. I reinstalled my new windows install as above. This IDE drive has since been just storage, but it did hold on to its "C:" name if that matters. So my primary windows drive is actually called F: in windows. This IDE drive has the boot priority in the bios.

I just installed ubuntu onto the old IDE HD that i was using for storage. ubuntu boots up and loads fine.

Somehow i missed something in setup and ubuntu never tried to configure my system as a dual boot. It was setup as a ubuntu only boot. So i'm trying to add the windows part to GRUB.

My device.map looks like:
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb

I don't know what /dev/sdb is. i only have one SATA HD.

I added this to my menu.lst:

title           Windows XP
rootnoverify    (hd1,0)       (i tried root and rootnoverify)
map (hd0)(hd1)                 (i tried flipping the order of this line and below)
map (hd1)(hd0)
makeactive
chainloader +1


The problem is when i select Windows XP in the boot menu, i get the Error 11: Device string not found or something like that.

I'd much appreciate any input. Thanks!

---

### Post by logos34 on 2007-06-26
TXBDan, 

It would probably be best to start a fresh thread.  You'll get more responses that way.  

edit: after you start the new one, paste a 'moved' link to it here so you don't get flagged for double posting. (isn't that how it's done?)

---

### Post by TXBDan on 2007-06-26
Ok, will do, thanks.




New thread here: [http://ubuntuforums.org/showthread.php?t=485022](http://ubuntuforums.org/showthread.php?t=485022)

---

