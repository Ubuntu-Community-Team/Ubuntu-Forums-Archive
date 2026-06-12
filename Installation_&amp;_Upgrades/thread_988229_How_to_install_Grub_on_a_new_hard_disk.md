---
title: "How to install Grub on a new hard disk?"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-11-20
I have installed Windows on a small hard disk and I want add Grub to it, so that I can use other harddisks with other systems as well.

The Windows harddisk is just 8GB and Windows takes 4GB. I don't want to install Linux on the rest, but Grub. How can I do that?

bye

R.

---

### Post by caljohnsmith on 2008-11-20
You can use Grub4DOS inside of Windows; I'm using it now to boot all my OSes, and it works great. Here are the steps:
[LIST=1]
[*]Download the [Grub4DOS-0.4.4]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip") package and also the the "[grubinst]("http://download.gna.org/grubutil/grubinst-1.1-bin-w32-2008-01-01.zip")" package.
[*]Move the "grldr" file from the Grub4DOS-0.4.4 package to your C:\ root directory
[*]Use the "grubinst_gui.exe" program to install the Grub4DOS MBR (Master Boot Record)
[*]Save the following menu.lst to your C:\ directory:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

#splashimage=(hd0,1)/boot/grub/splashimages/firework.xpm.gz
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
timeout		5

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL 

title		Windows XP
find --set-root /ntldr
chainloader /ntldr



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
# kopt=root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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


### PUT FUTURE LINUX ENTRIES IN THIS SECTION ###

### END DEBIAN AUTOMAGIC KERNELS LIST
```
[/LIST]
And that should be it. It would be a good idea to make sure you have a Linux Live CD handy that you can boot in case something goes wrong and you can't boot Windows. It's easy to fix Grub4DOS from the Live CD if necessary. Good luck and let me know how it goes. :)

---

### Post by ELMIT on 2008-11-20
Thanks for your suggestion, I will keep it as reference if I need it.

In my case I cannot use it, because the harddisk is not the first one, and I need to swap the hard disks via Grub to get Windows to start. 
I need to find a way to install Grub withouth using the Windows partition yet.

bye

R.

---

### Post by caljohnsmith on 2008-11-20
> **ELMIT said:**
> Thanks for your suggestion, I will keep it as reference if I need it.

In my case I cannot use it, because the harddisk is not the first one, and I need to swap the hard disks via Grub to get Windows to start. 
I need to find a way to install Grub withouth using the Windows partition yet.

bye

R.
You originally said you wanted to put Grub on the same drive as Windows, so I was just suggesting a solution of simply putting Grub inside your Windows partition. You can create a dedicated Grub partition on your Windows drive and install Grub to that, but using Grub4DOS accomplishes the same thing without having to use another partition. So are you not booting the Windows drive? What do you mean exactly when you say:
> In my case I cannot use it, because the harddisk is not the first one, and I need to swap the hard disks via Grub to get Windows to start. 
So are you saying Windows is not the boot drive?

---

### Post by ELMIT on 2008-11-20
ok, lets start over again.

I have installed Windows on NOT the first drive and it cannot boot. It only shows the logo of Windows, the blue screen of death (as a flash so that I cannot read anything) to reboot immediately.

I read that I can fix that by swapping the drives, something like I did on another machine (/boot/grub/menu.lst)

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


Therefore I want to install Grub to be able to add map lines ...

bye

R.

---

### Post by user481516 on 2008-11-20
Hey man, I am with you.  I have tried to do this before to no avail.  I would REALLY like to know how to just install grub on any hard drive.  BUMP.

---

### Post by caljohnsmith on 2008-11-20
Deleted.

---

### Post by ELMIT on 2008-11-20
Here are my drives:
/dev/sda1 linux
/dev/sda2 linux
/dev/sda3 W95 FAT32
/dev/sda4 EFI (FAT-12/16/32)

/dev/sdb1 linux

/dev/sdc1 linux     <=== this one I boot 

/dev/sdd1  *   208845 16016804 793980  6  FAT16
/dev/sdd2          63   208844 104391 83  Linux


/dev/sda and /dev/sdb  we cannot use 
/dev/sdc is my currently used Ubuntu
/dev/sdd is a new drive, where I have inserted at the beginning a 100 MB ext3 partition (sdd2) and sdd1 is the windows installation.

/dev/sdc is for booting with Grub to select either the sdc version of Ubuntu or the /dev/sda other Linux version

/dev/sdc should be replaced with the newly created /dev/sdd to boot Windows and the /dev/sda other Linux version


I have used grub-install /dev/sdd.
It reported:
/boot/grub/device.map
(hd0)  /dev/sda
(hd1)  /dev/sdb
(hd2)  /dev/sdc
(hd3)  /dev/sdd

replacing /dev/sdc with sdd and boot results in a Grub loading error
(that for sure, because the 100 MB I created are not used)


bye

R.

---

### Post by ELMIT on 2008-11-23
bang, and this thread is dead again, without a solution!

---

### Post by VastOne on 2008-11-23
I feel for you on this and have suffered the same fate... Several posts with 0 responses...

I read how great this Ubuntu Forum is but it appears to me that there are far greater fires than firemen....

A greater concern is how many people are trying to get away from windows and find themselves in the same court you and I are in, outside looking in... At least in the windows world, RTFM held some truths...With Ubuntu, we must rely on this forum and those like it...

Off the soapbox...





> **ELMIT said:**
> bang, and this thread is dead again, without a solution!

---

### Post by bulldog on 2008-11-23
Installing GRUB on any hdd,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.
More about GRUB and how to use it:

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

---

### Post by ELMIT on 2008-11-26
Just a quick question:

what is hd0,0  and  hd0,1  and hd1,0   and  hd1,1  ???

Is it harddisk 0 or 1 and partition 0 and 1 ???

In my case I will have:
/dev/sda1 & /dev/sda2
/dev/sdb1
/dev/sdc1 & now I add /dev/sdc2

/dev/sdc is the first drive in bios, sda the second, sdc the third.

Am I correct, that:
/dev/sdc1  == hd0,0
/dev/sdc2  == hd0,1
/dev/sda1  == hd1,0
/dev/sda2  == hd1,1
/dev/sdb1  == hd2,0

---

