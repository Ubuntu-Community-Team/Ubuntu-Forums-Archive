---
title: "Grub stuck at &quot;loading please wait&quot;"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by Benja.f on 2008-07-21
Hi, I'm new to this whole Linux thing.
I wanted to install Ubuntu 8.04 on a new partition, so I used Gparted on the live cd to resize my original ntfs partition. But 2/3 of the way through copying files, it froze. I waited for a while, but as nothing happened, I forced a reboot. This (not surprisingly) fried my ntfs partition, which can no longer be read from the live cd and cannot boot windows.
After installing Ubuntu, I rebooted, and Grub hangs on "Grub loading please wait".
I tried repairing with the Super Grub cd, but it couldn't seem to find any of my partitions. If I boot with the live cd, however, I can see them.
sda1 : ntfs (cannot be mounted)
sda2 : ext3 /
sda3 : swap 

This means I am currently stuck with no access to my ntfs partition, and an Ubuntu installation that does not start..

I'm running a laptop with a sata drive. Anyone got some bright ideas? Please?

---

### Post by coffeecat on 2008-07-21
I don't remember coming across the "Grub loading please wait" message before. With a fresh install of Ubuntu, that shouldn't happen. I wonder if the corruption to your NTFS partition has corrupted the main partition table in way that allowed the Ubuntu installer to proceed but is confusing Grub.

I think it's worth trying to repair Grub with the live CD, not supergrub. Here's the procedure. Boot up with the live CD and open a terminal. Now do:

```
sudo grub
```You get the grub prompt, which is 'grub >'. Now do these three commands one after the other:

```
root (hd0,1)
setup (hd0)
quit
```and you are returned to the bash prompt. What that did is to re-install grub stage 1 to the mbr and grub stage 1.5 to the otherwise unused part of the HD immediately after the mbr, redirecting grub to stage 2 in /boot/grub in sda2 - your root partition. And yes, (hd0,1) and (hd0) is correct - grub has a different partition numbering convention.

Now reboot into the hard drive and see what happens. If you can boot into your Ubuntu installation, you *may* be able to repair your NTFS partition with ntfsfix, but I fear it may be a goner.

If that doesn't work, you may need to reformat the whole hard drive and start again, but before you do this, can you get hold of a Windows install disc? I mean a proper Microsoft one, not a manufacturer's image/restore disc. If you can you could boot up with this, go into the recovery console and see if you can repair the NTFS partition.

**Edit:** About those three grub commands. I should have said to press return after each. And, if my thought about a corrupt partition table is correct, you may get a grub error message after the first or second. If you do, post back with what it says. It may give a clue.

---

### Post by Benja.f on 2008-07-21
I just tried what you described, and it didn't work.. I got no errors, it appeared to re-install just fine. But after reboot the same happened, "Grub loading stage 1.5", "grub loading, please wait..", and then nothing.. I have a few XP discs lying around i a drawer somewhere, perhaps I should try one of those now.
By the way, this is my menu.lst (don't know if it's any use)
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
# kopt=root=UUID=d2b99f1d-68a3-431e-84d4-daa73eb63989 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d2b99f1d-68a3-431e-84d4-daa73eb63989 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d2b99f1d-68a3-431e-84d4-daa73eb63989 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by coffeecat on 2008-07-21
That menu.lst looks fine to me. With the reinstall of grub the way I told you, it *should* have worked OK - all other things being equal - but it didn't. We could spend a lot of time checking a few other things, such as the UUID in the kernel line, but I get a sense that there is a major problem with the main partition table. The XP disc may be able to repair the NTFS partition and it may be able to repair the partition table. I don't know. Let's hope so.

**If** you are contemplating scrubbing the whole thing, reformatting the hard drive and reinstalling both Windows and Ubuntu, may I suggest the following sequence? I do so because I'm not sure how flexible the Windows installer is in giving you a C: partition less than the size of the whole HD. Whenever I've installed Windows, I've always prepared an NTFS partition for it first. So here goes:

1 Boot up with Ubuntu live CD. Use Gparted (System > Administration > Gnome Partitioner) to erase the whole drive and then create one NTFS primary partition with the boot flag set. Leave the rest unformatted. Shut down from the live CD.

2 Boot up with the Windows CD and install Windows to partition 1.

3 Boot up the Ubuntu live CD again, open the installer and let it partition up the unformatted space the way it wants, **or** choose your own Linux partition scheme in the unformatted space. Let it install grub.

If that all goes OK you should have a working dual-boot.

---

### Post by Benja.f on 2008-07-23
Update:
After running chkdsk /f from a Vista dvd a few times, I have regained access to the files on the ntfs drive when using the Ubuntu live-cd, and apparently only ~10 GB (of 80 GB) were lost. However, as the partition is still corrupted, gparted will not touch it.
Grub is still stuck loading after stage 1.5, even after using the windows Fixmbr and Fixboot and then another re-install.

For some reason my XP cd's won't boot, so guess i'm left with using the recovery cd..
Overall not an awfully encouraging start with Ubuntu, but think I'll try again anyway.
Thx a lot for the help!

---

### Post by Benja.f on 2008-07-23
2nd Update:

Used gparted to remove the ext3 and swap partitions, no problems.
After doing this, the XP cd was willing to boot. I used it to run another chkdsk, fixmbr and fixboot. All fine.
After reboot, I used the XP cd to remove the ntfs partition, which left me with an empty disc. I then created a new ntfs partition (70 GB) at the beginning af the disc, and started installing windows. After reboot, nothing. Just empty screen with marker flashing a few lines down.
Used Ubuntu Live cd to make ext3 ( / ) and swap and install ubuntu using manual selection of partitions. After reboot, same problem as before: 
Grub loading stage 1.5
Grub loading, please wait..
And nothing. Don't think it sees my HDD, SuperGrub cd certainly can't..
Help! Have I fried my drive completely??

---

### Post by coffeecat on 2008-07-24
First, I'm glad you managed to get most of your data off the corrupted Windows partition.

As far as I can make out you have done everything you needed to, but neither Windows nor Linux will boot. Neither does the Supergrub CD see the HD. I'm beginning to wonder if you have a failing hard drive. Hard drives don't necessarily fail all in one go suddenly. There's often a period of steadily increasing errors. Perhaps that's why Gparted froze when trying to resize the NTFS partition. Usually Gparted is reliable at resizing NTFS partitions.

I really have no further suggestions to offer - sorry. All I can say is that if I were in your position I would replace the hard drive and try to install Windows and Linux to that. Please don't judge either Linux or Ubuntu on the basis of this unfortunate experience.

One other suggestion for you. If you haven't already done so, it's worth investing in some sort of ghosting/imaging software for Windows. If you do regular backups, you can easily go back to the last backup if you have a hard-drive failure or partition corruption. I have an earlier version of Acronis and it's very good. I've never had a disaster like yours, but I've used it successfuly on several occasions when I needed to do such a radical cleanup of the hard drive that it was easier to wipe everything out and restore Windows from an image. And my Linux installs from .tar.gz files - but that's another story.

---

### Post by Benja.f on 2008-07-24
Well, thanks a lot for trying to help me!
Think I'll blame it on LG and try to have them replace the disc, still have a few months left on the warranty.
Again, thanks a lot!

---

### Post by coffeecat on 2008-07-24
> **Benja.f said:**
> Think I'll blame it on LG and try to have them replace the disc, still have a few months left on the warranty.

Best of luck. Hint - don't tell them you installed Linux. They might try to use that as an excuse for not honouring the warranty. There was a famous (infamous?) case here in the UK a few months ago where a nationwide computer chain called PCWorld (spit!) tried to blame an obvious hardware fault on Linux. Not sure what came of it in the end, but PCWorld got a lot of bad publicity among Linux users for the effort. Not that Linux users here in the UK could have thought any less of them in the first place. :wink:

---

