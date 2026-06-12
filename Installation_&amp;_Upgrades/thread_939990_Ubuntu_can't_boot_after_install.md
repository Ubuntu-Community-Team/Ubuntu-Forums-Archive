---
title: "Ubuntu can't boot after install"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by HalfBrian on 2008-10-06
Hi everyone,

I recently installed Ubuntu on my machine to try it out and test my program on a Linux machine, but when I installed it, it would not boot at all.  It just stayed at a blank screen (as if my monitor was in power-saving mode).

This blank screen comes from my graphics card, I suspect that at a certain color depth and/or resolution, my graphics card does not output anything.

I was able (and still am) able to boot into the Live CD since I can see the language selection screen, but as soon as I select English, the screen goes blank, but I can still press enter and the Live CD starts booting (as seen by hard-drive activity and cd activity) and after about 3-5 minutes, the desktop comes up fine.

After I installed it on my 500gb drive (a 40gb partition on said drive), I rebooted and nothing showed, as described above.  I was unable to boot into any operating system, only the Ubuntu Live CD.  After re-installing grub, things still didn't work.  I booted into Super Grub (on CD), and was able to boot into Windows.  From there, I install EasyBCD and configured the Windows Bootloader.  I also included Ubuntu in the configuration.  I set Ubuntu to default, and rebooted.  I was again unable to get into either operating system.

I then remembered that I could boot into the Windows CD (I had previously forgoten that I had to "Press any key to boot from cd") so I went into the Windows CD and restored the Windows bootloader.  Once into Windows, I copied the contents of /boot/grub/menu.lst into the NeoGrub config (NeoGrub is a feature of EasyBCD) and selected it as the default (for the next reboot only) and rebooted.  Again, the same blank screen and no HDD activity.

So, my question is if there is any way to get Ubuntu to boot?  I can access the files via the Live CD, so if you need me to get a log or something, I can.

Specs:
Windows Vista Ultimate SP1
Ubuntu 8.04.01 32bit
Core 2 Duo
GeForce 8600
2GB RAM
Disk 1: 160gb SATA (w/ Windows)
Disk 2: 500gb SATA (w/ Ubuntu)
Disk 3: 120gb IDE (no OS)

So, in summary is there a way to diagnose Grub/Ubuntu boot problems without using the monitor at all, or to switch it to a higher color-depth during boot to diagnose problem?  (any other suggestions are welcome)

I realize that this is quite difficult to do, so I understand if you can't help me.

menu.lst:
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
# kopt=root=UUID=5c41bb2d-755c-4ac2-89ca-0437525d394c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5c41bb2d-755c-4ac2-89ca-0437525d394c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5c41bb2d-755c-4ac2-89ca-0437525d394c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by me_ben on 2008-10-06
i think you are installing the Ubuntu on hdd1 that is your second hard disk & to make it boot you have to make your booting configuration as hdd1 in booting information

---

### Post by HalfBrian on 2008-10-06
Is that not how I already have it? (hd1,1)= Hard Drive 2, Partition 2 right?

---

### Post by uidb4056 on 2008-10-06
When you boot the grub menu appears? or a message saying ' press ESC to get the menu' ?
If yes you can try to edit pressing 'e' to get the lines of the first option, move the cursor to the kernel line and press 'e' again, go to the end of the line and remove 'quiet splash' press intro and then 'b' to boot with these temporary workaround, if it boots OK you can edit the menu.lst to make the changes permanent.

---

### Post by HalfBrian on 2008-10-06
Unfortuneatly, I can't see the grub menu due to my messed-up graphics card. I'll try to edit my menu.lst and report the changes... I suspect it will be the same (I think I've done this before).

---

### Post by 73ckn797 on 2008-10-06
If you can edit grub menu.lst try changing hd1,1 to hd1,0 and see what happens. That is, if the "/" is in the first partition of hd1.

I have had to do some convoluted grub drive designations because the first physical drive was actually running as hd1 instead of hd0.

---

### Post by HalfBrian on 2008-10-06
Well, it IS in the second partition:

Drive1:[160gb NTFS]
Drive2:[460gb NTFS][38gb ext3][2gb swap] (sizes are approx.)
Drive3:[120gb NTFS]

Should I still try what you recommended?

---

### Post by 73ckn797 on 2008-10-07
hd1,1 should work but like I said, I have had issues where that was incorrect. That is why I suggest trying something else like change hd1,1 to hd0,1. Heck, you might even try changing to hd2,1. Play around with it. What may seem to be the physical connection order may not be how grub sees it. Is this a bug? I have wondered.

All of this can be done following post #4 above.

---

