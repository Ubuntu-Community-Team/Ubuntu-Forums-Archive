---
title: "Bootloading with Triple Boot: Help, please?"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2008-10-24
Hi.  I have Vista HP running as a dual boot with Ubuntu (Vista came pre-installed, so I do not have an install disk).  I was wondering if I install Windows XP to the third partition, 

could I just use Grub4Dos to load all three OSes (installing from within XP)?  Would it automatically detect all three and be able to boot them properly?  Please note that ONLY Vista would be on the "C:" drive.

or do I need to physically repair the Vista Bootloader and then Grub from an Ubuntu install disk?

---

### Post by Pumalite on 2008-10-24
Post:
sudo fdisk -lu

---

### Post by Mark Phelps on 2008-10-24
Just a heads-up ... 

Presuming that you have one physical hard drive, and that you're planning on loading all the OSs onto that one drive, when you install XP, it will automatically overwrite the current MBR, essentially removing the option for booting into Vista.  You will be able to fix that by installing VistaBootPro in XP and then restoring the Vista boot loader.

You may also be able to fix that with Grub4DOS -- but I don't use that, so I don't know.

Also, if you don't have a Vista DVD, look into your computer documentation about how to make recovery media.  If anything happens to your Vista partition (and there's a risk it will if you use GParted to resize your Vista partition to make room for Ubuntu), without a way of booting into Vista Recovery Environment from CD, there will be no way to get Vista back.

---

### Post by Pumalite on 2008-10-24
Make sure you don't install XP inside of an extended partition

---

### Post by caljohnsmith on 2008-10-24
> **BEND IT 7 said:**
> Hi.  I have Vista HP running as a dual boot with Ubuntu (Vista came pre-installed, so I do not have an install disk).  I was wondering if I install Windows XP to the third partition, 

could I just use Grub4Dos to load all three OSes (installing from within XP)?  Would it automatically detect all three and be able to boot them properly?  Please note that ONLY Vista would be on the "C:" drive.

or do I need to physically repair the Vista Bootloader and then Grub from an Ubuntu install disk?
If you are going to install XP, I would highly recommend "hiding" your Vista partition so that the XP installer doesn't put all its boot files in your Vista partition, as this often happens depending on your setup. You can do that from the Live CD with:
```
sudo grub
grub> hide (hdX,Y)
grub> quit
```
Where (hdX,Y) would be your Vista partition in Grub's terms. After you finish installing XP, you can then unhide the Vista partition:
```
sudo grub
grub> unhide (hdX,Y)
grub> quit
```
Also, you could use Grub4DOS to boot all three of your OSes, but to my knowledge (and I use Grub4DOS by the way) Grub4DOS does not have an automatic OS detector or way to automatically set up the Grub menu.lst that it uses. It's not hard at all to configure the menu.lst though. If you decide to use Grub4DOS, I would recommend using its MBR rather than adding Grub4DOS to the Win XP boot.ini file like some people do, because that way you will have just one boot menu on start up instead of two. If you want any help with it, let me know.

---

### Post by ranch hand on 2008-10-27
OK, I'll bite.  How do you configure the grub menu?

---

### Post by caljohnsmith on 2008-10-27
> **ranch hand said:**
> OK, I'll bite.  How do you configure the grub menu?
Well, it depends on what you want to change. :) What do you want to accomplish?

---

### Post by Pumalite on 2008-10-27
[http://www.supergrubdisk.org/wiki/Edit_menu_lst](http://www.supergrubdisk.org/wiki/Edit_menu_lst)

---

### Post by ranch hand on 2008-10-28
> **caljohnsmith said:**
> Well, it depends on what you want to change. :) What do you want to accomplish?

I am new to linux and it turns out to be too much fun.  I have broken Ubuntu several times.

While this is fun and educational it  is not conducive to USING your box.

So I have dual booted Hardy/Hardy.  When I boot the default start is for my play install.  This is not pleasing to the wife, I feel, quite reasonably.

I have a 320 gig HDD and am thinking of loading Ubuntu Studio also.  I would like the default, the first on the list, to be the origanal Hardy install as that is what we both use and where all files we want to keep are.
Thanks

---

### Post by ranch hand on 2008-10-28
> **Pumalite said:**
> [http://www.supergrubdisk.org/wiki/Edit_menu_lst](http://www.supergrubdisk.org/wiki/Edit_menu_lst)

I am currently on my dreaded mother in laws computer in town, downloading ubuntustudio on her dsl connection.  This is faster than our 4.4kb download on dialup.

I have looked at you link and will try it out later today.

By the way, I here people complain about start up speed under Ubuntu.  This machine is plain Vista and it takes forever to load and be ready to use.
Thanks

---

### Post by caljohnsmith on 2008-10-28
> **ranch hand said:**
> I am new to linux and it turns out to be too much fun.  I have broken Ubuntu several times.

While this is fun and educational it  is not conducive to USING your box.

So I have dual booted Hardy/Hardy.  When I boot the default start is for my play install.  This is not pleasing to the wife, I feel, quite reasonably.

I have a 320 gig HDD and am thinking of loading Ubuntu Studio also.  I would like the default, the first on the list, to be the origanal Hardy install as that is what we both use and where all files we want to keep are.
Thanks
Well the first question is, do you know which of your two Hardy's Grub is using? In other words, when you get the Grub menu on start up, that menu is loaded from one of your two Hardy installs; do you know which Ubuntu it comes from? Once you know that, you can modify the Grub menu.lst to make the original Hardy install the default OS. If you can, how about opening a terminal (applications > accessories > terminal), and posting:
```
sudo fdisk -lu
```
And if you know which partitions are the original Hardy and your play Hardy, please let me know. Otherwise post the following:
```
mount | grep " / " | awk '{print $1}'
```
And let me know if you are in the original/play Hardy when you run that command. We can work from there if you want. :)

---

### Post by ranch hand on 2008-10-28
I did not have a clue as to which install was loading grub.  I believe, from the results of what you wanted, that it must be this, the first, install.  You will, I am sure correct me if I am wrong.

Here is the result from - sudo fdisk -lu - 

tom@hogwash:~$ sudo fdisk -lu
[sudo] password for tom: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004630f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   292527584   146263761   83  Linux
/dev/sda2       606887505   625137344     9124920    5  Extended
/dev/sda3       292527585   394925894    51199155   83  Linux
/dev/sda4       394925895   606887504   105980805   83  Linux
/dev/sda5       606887568   625137344     9124888+  82  Linux swap / Solaris

Partition table entries are not in disk order

I find this interesting because /dev/sda2 and /dev/sda5 befuddled me when I gparted the HDD.  At that time they appeared to be identical but now I can see that they are not.  Still makes no sense but we learn a little at a time.

/sda1 is where I am now on the first install.  /sda3 is the second and the smallest partition.  I do not understand why /sda4, which should be empty, is listed as Linux unless this is the result of gparting.

The results from - mount | grep " / " | awk '{print $1}' -

tom@hogwash:~$ mount | grep " / " | awk '{print $1}'
/dev/sda1

I am assuming that this is an indication of where grub is booting from.

Now that I have drawn, very probably false, conclusions from this information, feel free to naw on me a bit.

I do make notes on these commands that I hope to make sense of someday.  They say us old people need mental stimulation.  If this doesn't count, at least I am having fun.

---

### Post by caljohnsmith on 2008-10-29
I love the name you have for your computer, Tom. :) Anyway, that aside, while you are booted into sda1, please post:
```
cat /boot/grub/menu.lst
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And we can work from there. :)

---

### Post by ranch hand on 2008-10-29
result from - cat /boot/grub/menu.lst

tom@hogwash:~$ cat /boot/grub/menu.lst
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
hiddenmenu

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
# kopt=root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

This looks like the listing of my origanal install and nothing else.  I will log into other install and post from there. 

result for - sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump

tom@hogwash:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
[sudo] password for tom: 
0000000 ff02                                   
0000002


tom@hogwash:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
[sudo] password for tom: 
0000000 ff02                                   
0000002

---

### Post by caljohnsmith on 2008-10-29
OK, according to that "dd" command you ran, your Ubuntu install on sda3 is the one that controls Grub on start up. If you are still booted into your sda1 Ubuntu as before, then please post the output of:
```
sudo mount /dev/sda3 /mnt
cat /mnt/boot/grub/menu.lst
```

---

### Post by ranch hand on 2008-10-29
results of - cat /boot/grub/menu.lst

thom@playtime:~$ cat /boot/grub/menu.lst
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=splash

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0b6718c5-d816-4bf3-a4ae-73423b53bafd ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

This looks more promising.  Is the extra listing not in the first installs file because it is the first install or because I gparted the drive after the first install?

---

### Post by caljohnsmith on 2008-10-29
[QUOTE=ranch hand]This looks more promising. Is the extra listing not in the first installs file because it is the first install or because I gparted the drive after the first install?[/QUOTE]
The extra listing is because the sda3 Hardy was most likely installed after your sda1 Hardy, so the sda3 Hardy detected the sda1 Hardy and added it to your menu.lst. 

Your menu.lst shows that Hardy on sda3 is the one that gets loaded by default on start up. If you want your sda1 Hardy to boot by default instead, you could just change the "default 0" line in the menu.lst to "default 3". Grub starts counting from 0, so "default 0" means it will boot the first OS in your menu.lst, "default 1" will boot the 2nd OS, "default 2" will boot your 3rd OS, etc. Also, your timeout time is 10 seconds, if by chance you want to tweak that, just change the line with "timeout 10" to however many seconds you want to allow before Grub boots the default OS.

To modify that menu.lst from your sda1 partition where you are now, you can do (assuming you still have sda3 mounted):
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And just change those lines as I've highlighted below:
```
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
[COLOR="Red"]default		3[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10    [COLOR="Red"]<--change the timeout in seconds to whatever you want[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

<snipped>

```
Give that a shot and let me know how it goes. :)

---

### Post by ranch hand on 2008-10-29
That did it.  Boy, do I have things to study.
Thanks agian.

BTY - The hogwash name was used first on the origanal HDD containing Vista HP.  I put that in the bios when I looked in there and found that it was set for remote atart up and to boot from the HDD first.  Great security there and what are pure folks supposed to do when they need to boot from the Dell suplied disk?

The bios password has to do with male bovine excretion.

---

### Post by caljohnsmith on 2008-10-30
> **ranch hand said:**
> 
The bios password has to do with male bovine excretion.
Being as ignorant as I am about agricultural science, I didn't realize there was a difference between male and female bovine excretion. :-k   :biggrin: 

Anyway, glad it worked; cheers and have fun Ubuntu-ing. :)

---

### Post by ranch hand on 2008-10-30
I just rebooted back to hogwash.  This is very nice.  I will probably break playtime in the next week but I can take time to see if I can fix it because I have this.

As to the male/female difference - noone says cowsh*t for some reason.  If you step, or better yet, fall face first in the two varieties you will not find sugnificant differences.

Thanks again.  I can now use Ubunutu and play with it.

---

