---
title: "Issue: Dual boot - Grub with &quot;Error 22&quot; on SATA"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by m i k e on 2007-12-30
In my machine I have the SATA drive that I am using for the dual boot and an IDE drive formatted NTFS that I use purely for file storage.  I wiped the SATA drive, installed Windows XP on the first partition and it worked fine.  Once I got Windows configured to my liking I went to use the rest of the space on the drive to install Ubuntu.  I made a swap partition and the ext3 partition and everything seemed to work just fine.  Then when I restarted it booted straight to Windows XP without showing me the Grub menu.  After some searching and posting I came to the conclusion that grub didn't get assigned to the MBR so I did:

sudu grub
find /boot/grub/stage1
root (hd1,2)
setup (hd1)
quit

I did this from the live CD as someone in another thread suggested.  I thought it would work as the process seemed to run like it was supposed to.  The Grub screen did now show up except I now get this **"Error 22: No such partition"** when I try to boot Ubuntu and I cannot boot into Windows either as it says: 

"Stating up...
NTLDR is missing
Press Ctrl+Alt+Del to restart"

After this happened I tried one more thing.  I remembered that in the regular install, when I clicked "Advanced" on the last step it said it was going to install to hd0 when I now realized that the SATA drive was hd1.  So I did a reinstall and changed it to hd1 but I still get the exact same "Error 22" and cannot boot into XP.

Can someone please help me out here by giving me some specific information on how to remedy the problem.  If you could avoid only referring me to links I would appreciate it as I feel I have looked at most everything.  Thanks very much for any help.

---

### Post by ajgreeny on 2007-12-30
Boot into the ubuntu live CD and show us the output of ```
sudo fdisk -l
``` then mount the ubuntu partition on the hard disk (it's the ext3 one shown on the above output) which I think you can do from the file manager (nautilus) by double clicking on the disk icon showing in the left hand panel.  Open up the /boot/grub/menu.lst file from your installed ubuntu partition and show us that as well.  We should be able to tell you how to edit the menu.lst to get both to boot OK.

---

### Post by m i k e on 2007-12-30
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
# kopt=root=UUID=76b4e890-3302-47f7-bbfc-92659bbe551d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=76b4e890-3302-47f7-bbfc-92659bbe551d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=76b4e890-3302-47f7-bbfc-92659bbe551d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

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
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Well there is my menu.lst file.  However, since my first post I have successfully booted into Ubunto and Windows.  What I had to do was go into my bios and switch the order of my hard drives.  So now the IDE with purely files is 1 instead of 2 and is listed 3rd (after floppy and CD rom) to boot.  Once I did this I could successfully boot each operating system.  So it seems that the installation installed Grub onto the IDE hard drive.  My question is now: Should I leave it?  Is there any reason that it would be better to boot from the SATA drive that actually contains the OS's?  Thanks for the help.

---

### Post by ajgreeny on 2007-12-30
If it ain't broke, don't fix it!  I would leave things as they are for the moment, at least.  Perhaps next time you need to install a new version of ubuntu would be the time to put grub on the master disk, but for now leave things alone.

---

### Post by m i k e on 2007-12-30
Good advice.  I'd rather not work on it anymore either.  I would just like to know how to remove Grub from my other (SATA) HD.  I would to get it back so that if I boot that drive up it will just go directly into Windows like it did before.  How would I go about doing that?

---

### Post by wagoner on 2007-12-30
To remove grub from the SATA drive, you will need to rewrite the MBR for that drive with windows.  I did this once by booting off of the windows install cd, getting to a command prompt and typing fixmbr and then fixboot.  I don't recall how to do this exactly, so do a search on fixmbr.

---

### Post by m i k e on 2007-12-30
Thanks for your help.  Can anyone else tell me what specific parameters I would have to put in for my situation?  It's not something I just want to try as I don't want to wipe grub from the wrong drive.  Also do I need to do fixboot as well as a fixmbr?

---

