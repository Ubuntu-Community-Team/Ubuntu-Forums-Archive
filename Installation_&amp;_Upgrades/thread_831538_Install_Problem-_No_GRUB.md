---
title: "Install Problem- No GRUB"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by bencho on 2008-06-16
Hi,

Im running MCE 2005 and want to dual boot ubuntu 8.04. I just did it to my laptop, Thinkpad T43p. and it was flawless. Friend helped me get some pretty stuff etc etc and its smooth.

Then tried to do it to my desktop.

AMD X2 4400+
Asus A8N-SLI Premium

It installs fine, but on reboot, I get no GRUB menu. I ran it live and mounted the Ubuntu partition, and the menu.lst already too out the hiddenmenu option with 10sec timeout. I also tried spamming ESC on bootup to force into GRUB but nothing.... whats the problem here?

Thanks!

---

### Post by PmDematagoda on 2008-06-16
Did you instruct the BIOS to protect the MBR by any chance? If so, you may want to remove it.

After making sure that such options are turned off, install GRUB onto the booting drive with the help of [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). You will only need to follow the steps till step 5.

---

### Post by bencho on 2008-06-16
Ummmm... i dont think i told bios to protect MBR... i guess its somewhere in BIOS? Ill go check.

and ill try to install grub now.

will report back.

ty

---

### Post by bencho on 2008-06-16
*updated

so i misread info. grub is now installed.
however I go to boot into ubuntu and it gives me "Error 22 no such partition"

maybe i left out pertinent info >.<"
I have 2 sata hdd's and 1 sata dvd burner. burner is sata1, hdd1 with winxp/ubuntuNOTWORKING is sata2, and hdd2 (ntfs) is just for storage

---

### Post by PmDematagoda on 2008-06-17
Can you post the menu.lst and device.map files here?

---

### Post by bencho on 2008-06-17
**device.map**
(hd0)	/dev/sda
(hd1)	/dev/sdb

**menu.lst**
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
#      password --md5 xxxxxxxxxxxxxxxxxxxxxxxxxx
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
# kopt=root=UUID= xxxxxxxxxxxxxxxxxxxxxxxxxx ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID= xxxxxxxxxxxxxxxxxxxxxxxx ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID= xxxxxxxxxxxxxxxxxxxxxx ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by PmDematagoda on 2008-06-17
Can you also post the output of:-
```
sudo fdisk -l
```

---

### Post by bencho on 2008-06-17
Disk /dev/sda: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xbfb88e33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      620178   312569680+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5c3d5c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       34763   279233766    7  HPFS/NTFS
/dev/sdb2           34764       38913    33334875    5  Extended
/dev/sdb5           34764       38736    31913091   83  Linux
/dev/sdb6           38737       38913     1421721   82  Linux swap / Solaris




also** when i try to boot into windows mce, it stays at "Starting up" and only a hard reboot is possible. so now i cant log into windows

---

### Post by PmDematagoda on 2008-06-17
Change the Ubuntu boot entry to this:-
```
title Ubuntu 8.04, kernel 2.6.24-16-generic
**_root (hd1,2)_**
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID= xxxxxxxxxxxxxxxxxxxxxxxx ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```
Also change the check if the UUID is the same by running:-
```
sudo blkid
```
The entry you will need is the one for sdb5.

About the Windows problem, where is it installed?

---

### Post by bencho on 2008-06-17
I can't change menu.lst

"Could not save the file /media/disk/boot/grub/menu.lst."
It says to check my permissions.

-sudo blkid- resulted in a matching UUID

Windows MCE is installed to the same hdd as ubuntu. I used guided partition and gave ubuntu 10% of drive and some swap.

*im new to linux.. as of yesterday afternoon. got about 6 hours under my belt... how do i get permission from a liveboot to access an installedboot? (like what im doing now) wouldnt that make it hella easy to screw with anyone's laptop?

---

### Post by PmDematagoda on 2008-06-17
You will need to use sudo permissions to edit it:-
```
sudo gedit /media/disk/boot/grub/menu.lst
```

---

### Post by meierfra. on 2008-06-17
PmDematagoda gave you the wrong advice.

Change all three "root (hd1,4)"  to "root (hd0,4)".

Change "# groot=(hd1,4)" to  "# groot=(hd0,4)"

and change your Windows item to 


title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1 


Also open menu.lst with 

```
gksudo gedit /media/disk/boot/grub/menu.lst
```

(for  graphical applications it is better to use "gksudo")

---

### Post by bencho on 2008-06-17
Nope, changed that one line to "root (hd1,2)"
same Error 22- no such partition


**update
oh... will try that should i change all roots to (hd0,4)? that is for generic and memtest86+?

---

### Post by meierfra. on 2008-06-17
Did you see my previous post?

---

### Post by meierfra. on 2008-06-17
> change all roots to (hd0,4)? that is for generic and memtest86

Yes

---

### Post by PmDematagoda on 2008-06-17
> **meierfra. said:**
> Yes

meiefra, the grub root device is sdb5, which would be (1,4) if not for the fact that there aren't five partitions.

---

### Post by bencho on 2008-06-17
VICTORY!

Many thanks to PmDematagoda for putting up with a noob and meierfra. as well!

This leaves me with just a few more Q's actually.

-What is the difference btw gksudo and sudo then? They both seem to operate the same.

-That "root (hdx,y)" what is it? I assume hd0 is my first hdd(sata2) and hd1 my second(sata3)? If so, then what is y?

---

### Post by PmDematagoda on 2008-06-17
> **bencho said:**
> VICTORY!

Many thanks to PmDematagoda for putting up with a noob and meierfra. as well!

This leaves me with just a few more Q's actually.

-What is the difference btw gksudo and sudo then? They both seem to operate the same.

-That "root (hdx,y)" what is it? I assume hd0 is my first hdd(sata2) and hd1 my second(sata3)? If so, then what is y?

1) sudo is the CLI version while gksudo is the GUI version, but frankly I don't see the big difference except in some cases where they do make a difference. But it is better to keep it like this:-
sudo = provide root privileges for Command Line Interface applications.
gksudo = provide root privileges for Graphical User Interface applications.

2) y is the partition, if it's the first partition then it is 0, if it is the second then it is 1.

---

### Post by bencho on 2008-06-17
Alritey, thanks guys! now off to make it look good.

---

### Post by meierfra. on 2008-06-17
> -That "root (hdx,y)" what is it? I


The first number is the hard drive, the second is the partition. But grub starts counting at zero. So (hd0,4) is the fifth partition on the first hard drive. 

The second number is ALWAYS  one less, then the corresponding number in  the linux device name. So /dev/sdb5 will always  be (hd?,4). 

The first number is more difficult to predict. Grubs  counts the hard drives  in the order as they are listed in the bios. So (hd0) is always the drive your are booting from. But ubuntu does not know the boot order in the bios and so uses a different ordering system. 
As a result there is no real connection between the "b" in sdb  and the corresponding number in (hd?) .  In your case sdb is (hd0) and the correct value for root is (hd0,4).  


And since Ubuntu  does not know the boot order in the bios, it sometimes writes the wrong numbers into "menu.lst". That's what happened to you.

---

### Post by bencho on 2008-06-17
Ummm... Now my Windows MCE wont boot. Gives me error wrong path

Also, every time i boot into Ubuntu, my mouse is frozen. I need to pull it out and plug it back in [Razor Copperhead USB]

---

### Post by meierfra. on 2008-06-17
> Ummm... Now my Windows MCE wont boot. Gives me error wrong path

More details please.  Is WindowsMCE starting to boot? Or do you get the error right after choosing Windows MCE at the  Grub Menu. Could you post the exact error message.


> Also, every time i boot into Ubuntu, my mouse is frozen. I need to pull it out and plug it back in [Razor Copperhead USB]

Sorry, I know nothing about that. I suggest to start a new thread for that.

---

### Post by bencho on 2008-06-17
Windows does not boot.

**sudo blkid**
/dev/sda1: UUID="4A76D60D76D5FA21" LABEL="JukeBox" TYPE="ntfs" 
/dev/sdb1: UUID="80C8265EC8265328" TYPE="ntfs" 
/dev/sdb5: UUID="a3aa4d18-268b-4467-8217-6bad72db0874" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="7167eaf2-a5c1-471f-be64-bf3f5e6539eb" 

**root (hd0,0)**
"Starting Up"... hangs and if you push power button everything shuts off immediately.

**root (hd0,1)** [tried this for shitz nd giggles]
Error 12 - Invalid drive requested

---------------------------------------------------------------------------
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by meierfra. on 2008-06-17
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


Just like that. Don't use  the map lines.

---

### Post by bencho on 2008-06-17
ok, sorry, wasnt sure before so i left those in.

thanks, everythings pretty much stable now cept for that pesky mouse thing.. which i will address tmr.. need sleep.

thanks again!

---

