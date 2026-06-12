---
title: "What a mess. Need help please!"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by one angry dad on 2006-12-23
My son called me at work two days ago wanting to know if he could download the ubuntu live cd to check it out. I said sure, knock yourself out. He's been getting into computers a lot more than me lately, and he's 15 so I figured let him poke around.

Later that evening at home he tells me he has a problem. Instead of just running the live cd, he installed it, and now he can't anything to work. I powered it up and we tried reinstalling. It get to the screen after the reboot where it says 'grub loading' and hangs. At this point he tells me he can't locate the restore disk for the computer, either (a sony vaio vgc rc210g - two drives in raid 0).

So I grabbed a copy of winxp pro and tried that, but it won't install either (says it can find any hard drives)... so I can't even try fixmbr.


He screwed up big time... he didn't even bother to save any files he had on this thing (I am using said computer to type this, running the live cd).

Any advice? I hate to pay sony for a restore disk if it's not even going to work (like the winxp pro)... thanks

---

### Post by bulldog on 2006-12-23
Hi angry dad,well that's why we have kids,to keep you busy in restoring their mistakes.:D 

Can't promise anything because,if I'm well informed,Raid 0 is all about speed and no safety copy of your data.

Can you type in the terminal [ALT + F2 and type gnome-terminal]```
sudo fdisk -l (l as in like)
``` and copy the outcome to the forum?

---

### Post by one angry dad on 2006-12-23
> **bulldog said:**
> Hi angry dad,well that's why we have kids,to keep you busy in restoring their mistakes.:D 

You got that right!

Here's what I got:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by bulldog on 2006-12-23
I'm afraid there's not much data left on sdb.
We can try to mount it but I'm afraid it's wasted time.
How about the raid settings,is this done in the BIOS?
As I understand raid0 writes his data on both disks and if one of them fail,all your data is gone,is that the right assumption?
If so,why is ubuntu on just one disk? is the raid disabled?

Let's try to get ubuntu running.
Can you give me the menu.lst?
To get there we have to mount your ubuntu first.
Make a mount point,```
sudo mkdir /mnt/rescue
```
To mount,```
sudo mount /dev/sda1 /mnt/rescue
```
To access the menu.lst,```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```
Copy this menu.lst to the forum,maybe we can get ubuntu to boot properly.

---

### Post by one angry dad on 2006-12-23
> **bulldog said:**
> How about the raid settings,is this done in the BIOS?

I don't know. You'd think so, but I can't access bios on this thing... tried every F key there is.

> **bulldog said:**
> As I understand raid0 writes his data on both disks and if one of them fail,all your data is gone,is that the right assumption?
If so,why is ubuntu on just one disk? is the raid disabled?

lol... I questioned him at length about the installation, and he doesn't remember much. I couldn't say how he did this.](*,) 

Here is the list... didn't know which section you needed, so I'll paste the whole thing. Thanks

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
timeout		3

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
# kopt=root=UUID=6da18bb9-447f-4225-b97c-b211a984969b ro
# kopt_2_6=root=/dev/sda1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bulldog on 2006-12-23
Find this section in the menu.lst and change it the way I did.
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
Now you will see the grub menu when you boot for 10 seconds.

I should disconnect the sdb drive [just disconnect the red cable from the drive] so this can't disturb anything.

Try to select the second option in the menu.lst (recovery mode) to see if it will boot.

---

### Post by one angry dad on 2006-12-23
Nothing... still hangs at grub loading

Is there any way to make the drives visible to windows so I can install the xp pro disk I have? I appreciate your help.

---

### Post by bulldog on 2006-12-23
Just boot from the XP install cd and format the partitions or erase all partitions if you like.
Windows should see your disk without a problem.
Can't help you with the raid thingy though,never used such a thing.:D

Booting means you must have set in the BIOS your cd-rom is the first boot device.
So you have to get into the BIOS I'm afraid.
Don't you have any documentation of the computer?

If the computer boots up pay close attention to your screen,most often is displayed how to enter the BIOS setup [mine uses the DEL key]

---

### Post by one angry dad on 2006-12-23
Unfortunately, no, the computer came no documentation and I've never seen any kind of options during boot.

The xp cd is useless as it is right now... *sigh* guess I have to call sony.

Thanks for your help anyway!

---

### Post by bulldog on 2006-12-23
Your son should know how it's done.
He did need it to boot from the live ubuntu cd to install it.
So grab him by the ears and ask how he did it.:D

---

### Post by scrooge_74 on 2006-12-23
start pressing ESC, F1 or any of other of those keys, usually one of those is bound to give you an error message or a option message.

I think Compaq used to puit on F8 or F10 on a laptop I had

---

### Post by Tanker Bob on 2006-12-24
The key press to get into the BIOS varies with the BIOS types.  The two most common for desktops are F2 and Del.  The time to press it is during the initial splash screen presentation, which should also have the Setup key listed at the bottom of the screen.  Depending on how the time delay is set, you may have to press the correct key repeatedly during the initial boot to get it recognized at the right time.

---

### Post by phormion on 2006-12-24
angry dad, I've installed a Win XP pro on a SATA hard drive with a RAID-capable controller (but no RAID defined) a few days ago. For this I needed to use a diskette with the controller driver (you must press F6 during install). Apparently that's how it works for some configurations which the installer doesn't support. 

One of the mobo CDs was bootable and provided the option of making a driver disk. It was also stated in the mobo manual that you will need this driver disk. 

Don't know about the Ubuntu problem, though, I'd look up on grub/RAID interaction problems.

---

