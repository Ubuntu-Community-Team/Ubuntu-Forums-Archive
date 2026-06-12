---
title: "[SOLVED] MBR/Grub is Dead"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by knudsenjoe on 2008-07-01
I'm trying to reinstall Hardy on a former dual boot HD. Problem is MBR/Grub is dead. Super Grub will say its fixed, but it won't boot without SG. So While I have what I assume to be a clean, unupdated for now install, I can't get Grub/MBR to work. So I need someone to either shoot me, or please help me figure how to fix the Grub/MBR.

I could accept a complete wipe of the entire disk and start over, but this hasn't seemed to work.

I could accept someone buying me a new computer with ubuntu preinstalled :)

---

### Post by VMC on 2008-07-01
> **knudsenjoe said:**
> I'm trying to reinstall Hardy on a former dual boot HD. Problem is MBR/Grub is dead. Super Grub will say its fixed, but it won't boot without SG. So While I have what I assume to be a clean, unupdated for now install, I can't get Grub/MBR to work. So I need someone to either shoot me, or please help me figure how to fix the Grub/MBR.

I could accept a complete wipe of the entire disk and start over, but this hasn't seemed to work.

I could accept someone buying me a new computer with ubuntu preinstalled :)

Your saying trying to install and Grub is dead. Confused. If you haven't already installed ubuntu , then go ahead and install it, and Grub will take care of itself.

If you have already installed ubuntu, and you can't boot from it, then lets do this from Terminal:

```
sudo fdisk -l
```

I just want to see your partitions first.

---

### Post by knudsenjoe on 2008-07-01
Hey, 'preciate the help

booted into hardy with Super Grub
sudo fdisk -l is:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc23ac23a

Device boot   Start  End     Blocks    Id  System
/dev/hda1     1      4660   37431488+  83  Linux
/dev/hda2     4661   4865   1646662+    5  Extended
/dev/hda5     4661   4865   1646631    82  Linux swap / Solaris

Used care to make sure Caps were correct.
Also the 3rd line of Blocks does not have a + in it if that means anything.

Will go to your Grub link and check it out. Will be careful about using it until I hear back from you.

Once again, 'preciate the help.

---

### Post by upchucky on 2008-07-01
you should be able to get this working by editing the /boot/grub/menu.lst

if you can't then supergrub can fix it.

it looks like it may be booting to busybox, choking on graphics or net card perhaps, if u can get the command prompt then supergrub has indeed fixed it and u have a different problem

post your /boot/grub/menu.lst

---

### Post by Rallg on 2008-07-01
This won't fix the problem, but it could give you a workaround until the problem is fixed by other means:

Can your computer boot from USB memory stick (does BIOS offer you the choice)? If so, you might try making a blank USB stick bootable, put DOS on it, and GRUB4DOS. Info on how to do that can be found by search (you seem knowledgeable enough to follow the instructions).

If you do that, the GRUB on the USB stick is independent of anything happening with GRUB on your hard drive. So, you can edit the GRUB menu.lst (on the USB) as plain text, and see what happens. Just remember that the USB may think it is hd0 and that your hard drive is hd1.

That method can get you to Linux or Windows, as long as the menu.lst is OK. If it works for you, then you have time to figure out what went wrong on the hard drive, since you won't be locked out of your operating systems.

---

### Post by knudsenjoe on 2008-07-01
USB is not an option for me unfortunately:(

I installed startupmanager with no success

I can get it to boot using Super Grub, but for some reason it just won't boot without it.

'Preciate it.

---

### Post by upchucky on 2008-07-01
ok since it will boot using supergrub the install is ok, you need to pass the info that supergrub is using to boot it to the /boot/grub/menu.lst so it will boot.

the menu.lst that supergrub is using has the info for your drive.


as you can see from this, my ubuntu root is on hd0,5  yours may be the same or on a different drive.

title		Ubuntu 7.10, kernel 2.6.22-15-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-386
quiet 

the following is my grub/menu.lst   do not use it but compare settings for your system, the entries for the boot should be similar.


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
# kopt=root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 7.10, kernel 2.6.22-15-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by jumponskis on 2008-07-01
My problem is kind of like this.  It's a long story.  First: I couldn't boot to windows so logos told me to use testdisk.  I did that but it did not help at all.  So I tried it again and played around with it a bit and finally ubuntu can see the HP_PAVILION partion in the places menu but it cannot mount it.  He gave me two strings of code to try but they didnt work. they made it worse.  he recommended trying the xp install cd.  I ran chkdsk with it in recovery mode.  That made it FAR worse.  now when I boot up it goes to the BIOS POST screen where it checks the memory and whatnot, and the next screen is all black with a flashing underscore mark in the top left corner.  The only way to use my computer now is to turn on the computer and open the cd drive to put the 8.04 live cd in and close the drive, turn the computer off with the switch (ouch), turn it back on and boot into ubuntu with the option that says try ubuntu without making any changes.  PLEASE HELP

EDIT: FORMATING IS NOT AN OPTION


PS: upchucky would you please use the [CODE] tag? (the # button)

---

### Post by upchucky on 2008-07-01
everything is fine no need to format.

supergrub can fix it, takes a bit of reading to understand how.

the flashing cursor is called busybox, which means the sys is confused. and thinking.... actually it is a very limited shell command prompt that we dont need. to fix this problem.

since you can boot using supergrub then when you have the sys booted you need to edit the /boot/grub/menu.lst of your install to have the correct drive information so it can boot both xp and ubuntu.

look carefully at my menu.lst the first entry is ubuntu the last is win xp.

get your drive info from partimage, it shows you where Linux is and win is.

when you are booted in ubuntu do

```
 sudo fdisk -l 
```

this also tells you where linux is.


read help file about editing grub and supergrub, once you understand it you will never forget it.

---

### Post by Licurgo on 2008-07-01
Knudsenjoe:
I'm thinking some questions:
- First You said that was a dual boot
- In the output of fdisk -l I can only see 3 partitions, that's  consistently with ONE installation

The problem that you have is very easy to resolve:
-Install the liveCD or DVD and run it
- Go to Applications-Accessories-Terminal
-Type: sudo grub
-Then appears >
-Type: find /boot/grub/stage1
-Appears an output
- Type: root (hd?,?) Substitute ? with the result of the output
- Type: setup (hd0)
-Type: quit
- Reinstall and Voilá your system is ready
:lolflag:

---

### Post by mvdberg112 on 2008-07-01
> **jumponskis said:**
> The only way to use my computer now is to turn on the computer and open the cd drive to put the 8.04 live cd in and close the drive, turn the computer off with the switch (ouch), turn it back on and boot into ubuntu with the option that says try ubuntu without making any changes.  PLEASE HELP

Just an addition to the previous answer: you can start ubuntu, so you should be able to start grub in a command shell: Accesories->Terminal Start grub.
```
sudo grub (give your password)
```
Do you know your linux partition? I mean the number? Then start grub and try this:
```
grub
grub>device (hd1) /dev/sda1
grub>root (hd1,0)
grub>setup (hd1)
```
I do not know of course what you harddisk is. Very often you will have linux on partition 1 of disk 1 if it is the first installed OS.
Note: after you have done this, your system will boot grub. Grub will boot linux. But you have Windows, so the grub menu needs to have an entry to boot windows too. I do not know how to configure such an item. Advice: create first a boot CD or floppy or USB-drive to be able to Windows.

btw: what you did with chkdsk was probably "chkdsk /mbr"  or something like that. this will write a new bootrecord on your harddisk and then it should look for and find Windows at the next boot. Why it does not come up with the Windows menu to choose which Windows you want to start, i do not know. Maybe it does, but the timeout is 0, meaning it does try to start, but it is looking for Win on the wrong place. 

Or download SuperGrub? If you don't and can't find it, let us know. Now, I just used a few days ago to test if it would work in emergencies. It has function with which it creates the lines which are normally in menu.lst.
Supergrub: [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

PS: let us know your partition information, let us know if boot CD can mount all partitions. 

PS: You perhaps know this, but in the first sector of the first track on your HDD there is a MBR Master Boot Record. The bios looks here to boot, and it tells from which partition to start. A boot floppy (or CD or USB) has its own MBR and it tells for example to start windows from C:. That is why we can have a boot floppy while the OS is actually still on the HDD.

---

### Post by jumponskis on 2008-07-01
here is my results for 'sudo fdisk -l'

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
[COLOR="Blue"]/dev/sda2   *         968       18428   132005160    7  HPFS/NTFS[/COLOR]
/dev/sda3           18429       20673    16972200    5  Extended
/dev/sda5           18429       20573    16216168+  83  Linux
/dev/sda6           20574       20673      755968+  82  Linux swap / Solaris

```

the highlighted partition is my C: drive which is windows XP.  I've used supergrub and it worked fine and fixed the grub menu but I still cannot open windows.  If I choose windows from the grub menu It just hangs like it did before.  Windows is on the second partion only becuase the first is a recovery partion than I would just as well not have If I was able to modify it which I am not.  What happened was that one day I acidentally chose the recovery partition in grub listed under other os's (windows me/2000/xp) when the correct selection was Windows XP home.as i say the recovery screen appear and a meesage stating that it was starting formatting and all data on the c: drive would be returned to factory settings (s-s-SAY WHAT?!), I used the switch at the back of my computer to immediately shut off the computer and halt microsoft(-in-the-head)'s evil plot to force me to format all my beloved files (song, movies, essays, and pretty much everything else important in my life).  As soon as someone can help remedy my actions (stupid hard shut-off, why are you so brutal to my computer) I can proptly start perusing the forums for a way to delete hp(ea-brain)'s stupid f*****g recovery partition.  What an awful invention. More like data-loss partition.

No I can't mount the correct partition with manual mount auto mount or with supergrub livecd.  I tried it with the supergrub cd and it says that the filesystem (e.g. ntfs, nts, FAT32 etc...) is unknown.  I believe this is the problem but I have yet to come across something that will let me edit the file system type.  Man I heard getting the cube was hard but I got it in a day an a half.  If that was hard for everyone else how do they cope with this s**t?!

PS:  formatting is NOT an option

PPS: neither is paying an exuberant amount (or its it exorbitant, w/e you know what I mean) to have some corporate data loss company do the same thing that a bit of perseverance and good open-source programming can do for free :)

---

### Post by VMC on 2008-07-02
I'm thinking your XP partition maybe be trashed. What with all the testdisk and chkdisk you did. Lets just find out for sure.

Output this from a Terminal:

```
cat /boot/grub/menu.lst
```

So we can see where grub thinks XP is hiding.

---

### Post by knudsenjoe on 2008-07-02
> **Licurgo said:**
> Knudsenjoe:
I'm thinking some questions:
- First You said that was a dual boot
- In the output of fdisk -l I can only see 3 partitions, that's  consistently with ONE installation

The problem that you have is very easy to resolve:
-Install the liveCD or DVD and run it
- Go to Applications-Accessories-Terminal
-Type: sudo grub
-Then appears >
-Type: find /boot/grub/stage1
-Appears an output
- Type: root (hd?,?) Substitute ? with the result of the output
- Type: setup (hd0)
-Type: quit
- Reinstall and Voilá your system is ready
:lolflag:

I tried this and nothing seems to have changed

---

### Post by Bliepo32 on 2008-07-02
Try and change your menu.lst to this (make a back-up first).

To do so type (in the terminal):

```

sudo nano /boot/grub/menu.lst

```

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
# kopt=root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 7.10, kernel 2.6.22-15-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.22-15-386

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1
boot

```

Note: I am quite sure Windows will boot with these options. However, I am not certain about Ubuntu. I will have to see your original menu.lst.

---

### Post by jumponskis on 2008-07-02
@vmc:  here is the results I get

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
# kopt=root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a438ed98-2cb9-4d5c-b8b2-a5a704bd99d6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by VMC on 2008-07-02
Acording to the fdisk display above , you have one NTFS on second partition. The grub menu shows two Windows. One XP the other Home edition points to the correct fdisk..

---

### Post by jumponskis on 2008-07-02
> **VMC said:**
> Acording to the fdisk display above , you have one NTFS on second partition. The grub menu shows two Windows. One XP the other Home edition points to the correct fdisk..

I know that the one that say's home edition is the correct partition to choose.  When I choose it is says starting up... and the second line says _ and the line blinks repeatedly (I think this is the busy box thing I've been seeing around the forums lately) but nothing every happens.  It just freezes there.  The first partition is the manufacturer recovery partition that I accidently booted to, which set off the formatting of c: (partition 2)

---

### Post by jumponskis on 2008-07-05
bump

---

### Post by bigdee973 on 2008-07-05
i have the same exact problem where grub does not want to install or does absolutely nothing to my box..i tried this
-Type: sudo grub
-Then appears >
-Type: find /boot/grub/stage1
-Appears an output
- Type: root (hd?,?) Substitute ? with the result of the output
- Type: setup (hd0)
-Type: quit
- Reinstall and Voilá your system is ready
 but still its as if i never did anything to my computer. windows still boots up and i get no grub.  i rmemeber this use to work before but in gutsy.  i had vista installed but i deleted vista and installed windows xp and now im stuck...what did u do extactly to solve ur problem? do i have to reinstall ubuntu regardless?

---

