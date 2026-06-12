---
title: "Linux does not appear in boot option menu..."
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by stv453 on 2006-07-18
I've just installed ubuntu to a second hard disk on my pc.  I want to dual boot with Xp on my first hd.  

I used the graphical installer and during the partitioning phase, i didn't see an option to set the new ext3 partition as bootable.  It might be the problem because once i reboot the system, it goes straight to winXP without showing the GRUB loader.  

Is there anyway to set the linux partition as bootable using the liveCD?  maybe from gparted... ? :-k 

thanks...

---

### Post by coffeecat on 2006-07-18
Linux partitions don't have to be made bootable the way Windows ones are. I think the problem is more likely that Grub stage 1 hasn't been written to your mbr. Goodness knows why - it shouldn't happen, but does sometimes. Happened to me once with SuSE. So long as your installer has set up the /boot directory properly it's very easy to install Grub to the mbr and get you booting, but first we need some information.

Boot up with the live CD and get and post the details of you HD partition layout - you can use Gparted. Don't change anything! Secondly, get the contents of /boot/grub/menu.lst and post it as well. Then I (or someone else) can tell you the grub commands you can use in a terminal with the live CD to get grub properly installed.

By the way, if someone posts and tells you to use the command 'grub-install', **DON'T**. It's unreliable. Even the official Grub manual advises against using it.

---

### Post by stv453 on 2006-07-18
thanks for the reply...

ok, the two hard disks are partitioned as follows:

/dev/sda1    NTFS            142Gb
/dev/sda2    linux-swap      1.5Gb 
/dev/sda3    ext3            8.5Gb   <--- ubuntu

/dev/sdb1    NTFS            14Gb    <--- winXP
/dev/sdb2    Extended
/dev/sdb5    NTFS            25Gb
/dev/sdb6    NTFS            113Gb


the menu.lst

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
# kopt=root=/dev/sda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by coffeecat on 2006-07-18
OK. Your menu.lst looks fine to me and it can't be a hiddenmenu issue, and besides, even if it were, you'd boot into Ubuntu. So I guess it must have been a failure to load grub to the mbr. Here's what to do:

Boot up with the Ubuntu live CD. Open a terminal and issue the command:

sudo grub

You'll now see the > Grub prompt. Type 'root (hd0,2)' - without the quotes and make sure there is a space between root and (hd0,2). And that's a zero, not o.

Now type 'setup (hd0)' - again no quotes and make sure there is a space.

Now 'quit' and you should be returned to the Linux prompt. Hopefully, Grub will now be installed to the mbr configured to pick up the menu from sda3. Reboot without the live CD and it should all work. Let us know how you get on.

---

### Post by stv453 on 2006-07-18
ok, tried it... but it still boots straight into XP.

what if i try to overwrite the mbr on the Xp disk and force GRUB instead of the xp bootloader?

maybe 'setup (hd1)' ? is that worth a try or would that seriously mess up my system...?

edit: nope can't do that either... 

](*,)

---

### Post by coffeecat on 2006-07-18
What I didn't mention was that sometimes (for reasons I cannot fathom) grub stage 1 doesn't get written to the mbr when you issue those commands from a live CD. I didn't mention this before because I didn't want to be pessimistic. I've re-installed or repaired grub quite a few times now (I've got two machines with multiboots and every time I install a new variant of Linux I have to go through this rigmarole to get grub to use a root partition of **my** choosing. Sometimes using the live CD works and sometimes not. Pass. :?

If we could only get you into your new installation I know the grub commands I gave you will work. Normally I'd recommend downloading SmartBootManager, but for some reason the SmartBootManager home page is neglected and when you click on downloads, the url changes, but not the displayed page. You make a bootable disk of SMB and it can usually find all the installed OSs and boot into the one of your choice. Try googling around. There might be another source for the ISO. Also, I don't know where you are posting from, but if you can get hold of a copy of a UK magazine - Linux Format - (it's distributed to many countries) the ISO for SBM is on the cover disk most months.

Another way of getting you into the Ubuntu install. Do you by chance have the Acronis Suite in your Windows install? (Or can you 'borrow' it?) There's an addon called OS selector (something like that) for Disk Director. It installs its own bootloader and it can recognise Linux partitions. I've used it to repair a Windows mbr when fixmbr from the Windows CD failed (thank you Bill), and to deal with situations not unlike yours.

Finally, there's the [Ultimate Boot CD]("http://ubcd.sourceforge.net/"). I've no experience of it but I believe it's good. Might get you into your Ubuntu installation from which you'll be able to install Grub properly as per my previous suggestions.

Best of luck. I'll think about this more for you.

---

### Post by stv453 on 2006-07-19
thanks for the help coffeecat... unfortunately something went berserk with the partition table and having the do some data recovery.  I guess i'll have to leave ubuntu for some later date... :D

---

### Post by nashjc on 2006-07-20
Is there some sort of script run during the Ubuntu bootup that can alter menu.lst? I've got Ubuntu and WinXP coexisting on a couple of machines, but have had several instances of WinXP entry in menu.lst disappearing. Then I have to put it back. I've done this enough that I now have a copy around and just cp it, but it's a nuisance.

Also some activity during bootup saying the 2 copies of the boot FAT (may not have exact nomenclature here) being different. This has bappened on both the machines I'm dual booting. The bootup always seems to do a Dosfsck which chews up time too.

Suggestions welcome to try to figure this out and stabilize the machines.

JN

---

