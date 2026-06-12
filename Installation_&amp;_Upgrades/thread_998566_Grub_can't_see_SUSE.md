---
title: "Grub can't see SUSE"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by Happypants on 2008-11-30
I've recently put OpenSUSE 11 on my machine, then I installed Ubuntu.  Now I can't get Grub to recognize Suse.  I did the partitioning myself and I'm kind of leaning towards that being the issue, but I'm not 100% sure. 

Here's what my fdisk says from Ubuntu:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5120    41126368+   7  HPFS/NTFS
/dev/sda2            5121        5382     2104515   82  Linux swap / Solaris
/dev/sda3            5383       10604    41945715   83  Linux
/dev/sda4           10605       30401   159019402+   5  Extended
/dev/sda5           10605       29691   153316296   83  Linux
/dev/sda6           29692       30401     5703043+  82  Linux swap / Solaris

```

And here's my Grub's menu.lst

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
# kopt=root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=769b8506-4b75-461c-9f9a-7e9e7acfe04c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
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
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Suffice to say I'm a bit of a novice so any ideas would be much appreciated. 

I'll be glad to provide any other info that might be needed.  I'm just hoping this doesn't end up with "have you thought about reinstalling?"lol!

---

### Post by logos34 on 2008-12-01
try this:
[B]
gksudo gedit /boot/grub/menu.lst[/B]

Add this entry to the bottom:

> title OpenSuse 11
configfile (hd0,2)/boot/grub/menu.lstNote: looks like you have two swaps--only need one.  Sharing it will allow you to free up some space!

If you don't want to go through two grub menus to boot suse, you can either enable 'hiddenmenu' line in suse menu.lst (uncomment it) or install grub to sda3 boot sector and use the chainloader method.  Boot into Suse and run
[B]
sudo grub-install /dev/sda3[/B]

then add this entry to ubuntu menu.lst:

>   
title        OpenSuse 11
                                                                             root        (hd0,2)
chainloader    +1

---

### Post by Happypants on 2008-12-01
ALrighty... based on some info I got on the SUSE forums I added this to my menu.lst (got it from ls -lhat /dev/disk/by-uuid/).

```
title OpenSUSE, kernel 2.6.25.5-1.1-default
root (hd0,2)
kernel /boot/vmlinuz-2.6.25.5-1.1-default root=UUID=cc4ba929-5f31-4aab-b2d7-6cd89297895d ro single

initrd /boot/initrd.img-2.6.25.5-1.1-default

```

Now I'm getting an error 15, which in my mind means I'm getting somewhere (Let me have my dreams people!).  

I got the kernel from the LiveCD and not the actual install, so I'm thinking that might be the issue.  TBQH... I don't know how to get the kernel from the install (I'm a bit of a nub).  

Anybody? Thanks in advance.

P.S.  Here's the UUID readout if it's at all helpful and I missed something.

```
total 0
drwxr-xr-x 2 root root 140 2008-11-30 18:26 .
lrwxrwxrwx 1 root root  10 2008-11-30 18:26 769b8506-4b75-461c-9f9a-7e9e7acfe04c -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-11-30 18:26 0b78fd18-9966-4f86-99f1-3f6e8673f773 -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-11-30 18:26 cc4ba929-5f31-4aab-b2d7-6cd89297895d -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-11-30 18:26 4af98ac3-eda6-424c-b462-f940eae1cf29 -> ../../sda2
drwxr-xr-x 5 root root 100 2008-11-30 18:26 ..
lrwxrwxrwx 1 root root  10 2008-11-30 18:26 6054F6A8E07FB76E -> ../../sda1

```

---

### Post by Happypants on 2008-12-01
Thanks for the reply Logos.  

Tried it, but nothing new happened.  Copy-pasted the code from your post, so I know I didn't type it in wrong.

It was worth a shot.

Edit: BTW Logos... I wasn't positive if I needed the extra swap or not, so I played it safe and threw it in there.

---

### Post by logos34 on 2008-12-01
you might try running error check on suse root:

if it's mounted in ubuntu, unmount it 

if suse is formated ext2/3:

sudo fsck /dev/sda3

or for reiserfs

sudo reiserfsck /dev/sda3

---

### Post by Happypants on 2008-12-01
Here's what she told me

```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda3: clean, 75365/2624496 files, 765090/10486428 blocks

```

I guess that means that the disk itself is ok.  

Would that tell me if there were any corrupted files inside SUSE itself that might prevent it from loading?  And if no, how would I check that?

Edit:  It's ext3 by the by.

---

### Post by logos34 on 2008-12-01
it's not going to tell you anything about corrupt individual configuration files or anything like that.

Can you access files in suse partition?

My suggestion at this point would be to see if maybe you can use Suse's grub to dual boot ubuntu.  Overwrite ubuntu grub with suse's and add an ubuntu entry to the latter.  Basically the reverse of what you're doing.  If it doesn't work you can always restore Ubuntu grub (from the ubuntu live cd--see link in my sig).  

Tell grub the location of the / you want it to use to write the bootloader to the MBR:

-mount the suse partition (for example's sake we'll assume '/media/sda3')

then
[B]
sudo grub-install --root-directory=/media/sda3 /dev/sda[/B]

---

### Post by Happypants on 2008-12-01
I can access all the files in the Suse partition, but there is one thing that kinda bugs me (don't know if it means anything or not).  There isn't anything in the 'boot' folder.  Should there be?  

I'll try and get the Suse partition to boot, but, I'll be quite frank, I don't know how to go about doing that.  More fun experimenting!

---

### Post by logos34 on 2008-12-01
> **Happypants said:**
>   There isn't anything in the 'boot' folder.  Should there be?

yes, your suse kernels are supposed to be there!  no wonder it won't boot.

not sure how or why the kernel images would have just disappeared because of ubuntu install...

---

### Post by Happypants on 2008-12-01
> **logos34 said:**
> 
not sure how or why the kernel images would have just disappeared because of ubuntu install...

I wish I knew too, would've saved me and you a lot of time.  

I'm sure I screwed something up somewhere along the line.  Thanks for your help anywho!  Off to reinstall SUSE I go.  :rolleyes:

---

### Post by Happypants on 2008-12-01
I was cruising around the SUSE forums and someone suggested that the /boot for SUSE might have been overwritten during Ubuntu's install.  They suggested that I check the mounting and partitioning.  Unfortunately for me I'm not really sure how to do that and Google's not coming through with a straight answer so far.

Anyone know how I would check to see if the /boot was overwritten and how I could fix it if it was?

Edit:  Also it was suggested that /boot might be in separate partition, but I'm not 100% how to find that out.

---

### Post by logos34 on 2008-12-01
> **Happypants said:**
> I was cruising around the SUSE forums and someone suggested that the /boot for SUSE might have been overwritten during Ubuntu's install.

that's exactly what occured to me early this morning--suse install sets up a separate /boot.  Apparently ubuntu guided installation option erased it.  (if you really wanted to verify that, use TestDisk to scan for buried partitions, but it hardly matters because you can't restore it.)

I would backup your files and reinstall suse (without separate /boot)

---

### Post by Happypants on 2008-12-01
Great news!  I did a reinstall of SUSE and deleted that extra partition now things are working like a dream.  Not 100% sure what happened or if deleting that partition actually did anything, but I'm writing to you from inside SUSE right now so I'm content for the time being.  

Whatever happened it seems to be fixed.  Thanks for all your help!:D  You guys have been awesome for holding this newbies hand.

Edit:  P.S. Ubuntu works too.  Haven't tried Windows, but I won't be crying a river if it's messed up.

---

