---
title: "GRUB error 2 while booting from USB disk"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by kartik_vad on 2008-09-29
I just installed Ubuntu 8.04 on my USB disk (Linux doesn't detect my internal SATA disc, so I removed it and I'm using my external disc). My mobo is ASUS A8v-mx with a VIA VT8251 southbridge. I installed Ubuntu on the disc, but when I boot, I get the dreaded Error 2 after Grub says it's lading stage 1.5. I tried the following, to no avail:

1. Remove my DVD drive.
2. Change boot order in BIOS.
3. Change SATA controller to EHCI mode.
4. Disable SATA controller.
5. Reinstall linux.
6. Plug the USB drive into a different USB port.

In my device.map, (hd0, 0) maps to sda. I tried changing that to sdb, to no avail.

The partition UUID for the root partition in menu.lst is same as the actual UUID (from blkid) which is same as the one in fstab.

I tried editing menu.lst, increasing the timeout, removing quiet and splash options, disabling a default choice of OS, etc, but there's no change -- I suspect Grub isn't even reading these files. It hangs before it loads stage 2 and displays the boot menu.

When I boot from the live CD, it automatically mounts the partitions on my (USB) hard disc, so I'm sure the partition is not corrupt.

I tried pressing Escape, Alt-F2 and C on boot, but grub ignores these.

As I understand error 2 means disk not found. How do I get grub to display what disc it's looking for, and what discs exist in the system according to grub? Does it have a verbose mode or a console mode? Where is this configuration stored? If grub is saying disk not found before it reads the disc, how does it know which disk to read? Is this configuration in the MBR? [The disc does not have any other OS installed on it].

Should I try LILO?

I've been searching for hours, on this site, and others, to no avail. I'd really appreciate it if someone can help me out. Thanks.

---

### Post by kartik_vad on 2008-10-06
So I set my DVD drive to IDE slave and reinstalled Ubuntu, and now Grub boots into the grub prompt rather than giving error 2. However, my USB hard disk, on which I installed Ubuntu, doesn't appear when I type geometry (hd and tab-complete. There are no BIOS settings for my USB hard disk to change. What can I do to get a bootable system?

---

### Post by caljohnsmith on 2008-10-06
If your USB drive is not even showing up in the Grub CLI using geometry + tab completion, then which drive are you booting from? Whichever drive is booting must have Grub in the MBR, and it doesn't sound like it is your USB drive. If Grub on start up can't even see your USB drive on start up, I don't think there's any hope of booting it. Can you update your BIOS? Maybe a newer BIOS will let you boot the USB drive. If you can, it would be helpful if you would post:
```
sudo fdisk -lu
```

---

### Post by kartik_vad on 2008-10-07
I'm booting from the USB hard disc itself -- my SATA disc is unplugged, and the Live CD is not in the drive. I already have the latest BIOS. I'll post the output of fdisk -l soon when I go home.

---

### Post by kartik_vad on 2008-10-07
Here's the output from fdisk -l:

Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc3f6816

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7       26389   211921447+  83  Linux
/dev/sda3           26390       30279    31246425    b  W95 FAT32
/dev/sda4           30280       30401      979965   82  Linux swap / Solaris


This output is obviously produced when I boot from the live CD and plug in the USB hard disk, since I can't boot from the hard disc. No other hard drives are connected.

So why is Ubuntu unable to boot from the USB hard disc? Thanks.

---

### Post by kartik_vad on 2008-10-07
Oh, sorry, you asked for the output of fdisk -lu rather than fdisk -l. Here it is:

Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc3f6816

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       96389       48163+  83  Linux
/dev/sda2           96390   423939284   211921447+  83  Linux
/dev/sda3       423939285   486432134    31246425    b  W95 FAT32
/dev/sda4       486432135   488392064      979965   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-10-07
So when you only have the USB drive connected, you are now booting into the Grub prompt on start up and not getting a Grub error 2 any more? Also, which are partitions sda1 and sda2? sda1 is only about 50 MB it looks like, so is that maybe a dedicated Grub partition? And is sda2 then the root / Ubuntu partition? 

Also, please post:
```
sudo grub
grub> find /boot/grub/menu.lst
grub> find /grub/menu.lst
grub> quit
```
And post your full menu.lst so I can take a look at it if it's not too much trouble.

---

### Post by kartik_vad on 2008-10-07
> So when you only have the USB drive connected, you are now booting into the Grub prompt on start up and not getting a Grub error 2 any more?

Yes, exactly.

Yes sda2 is the Linux root partition and sda1 is the /boot partition. Previously I tried installing with a single partition, and that didn't work, so I tried installing Ubuntu again with a separate /boot partition, but that didn't make any difference.

When I boot from the USB drive and end up at the grub prompt, and type "find /boot/grub/menu.lst", grub tells me it can't find the file.

When I get back from work, I'll post the output of the commands you asked for. Thanks for your help!

---

### Post by kartik_vad on 2008-10-08
Here's the grub output when I boot from the live CD and plug in the USB drive (which automatically mounts):

grub> find /boot/grub/menu.lst

Error 15: File not found

grub> find /grub/menu.lst
 (hd0,0)



Here's menu.lst:
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
# kopt=root=UUID=0245f166-4dff-46d2-bb12-fbaefdd9a770 ro

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
kernel		/vmlinuz-2.6.24-19-generic root=UUID=0245f166-4dff-46d2-bb12-fbaefdd9a770 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=0245f166-4dff-46d2-bb12-fbaefdd9a770 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-10-08
You might have a problem with how your USB drive is configured in BIOS, but try this first: reboot, and when you get dumped into the Grub prompt, do:
```
grub> cat (hd0,0)/grub/menu.lst
```
Make sure you do the above command from the Grub prompt on start up, not from the Live CD. If that command successfully shows your menu.lst without returning an error, then I think you most likely have a BIOS issue at this point.

---

### Post by kartik_vad on 2008-10-08
[INDENT] Here's the grub output when I boot from the live CD and plug in the USB drive (which automatically mounts):

grub> find /boot/grub/menu.lst

Error 15: File not found

grub> find /grub/menu.lst
(hd0,0)[/INDENT]

When I'm booted from the USB hard disc, both the above find commands at the grub prompt give me Error 15: File not found.

cat (hd0,0)/grub/menu.lst when booted from USB disk gives:
Error 21: Selected disk doesn't exist.

---

### Post by caljohnsmith on 2008-10-08
OK, it looks like a BIOS issue is highly likely at this point, but we can try one last thing--you could reinstall Grub to the MBR of your USB drive. So from the Live CD, just do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the exact output of the above commands, then reboot, and let me know if anything changed.

---

### Post by kartik_vad on 2008-10-08
Here's the output. I'm rebooting and will let you know soon how it went.


grub> root (hd0,0)

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

---

### Post by kartik_vad on 2008-10-08
No change :(

Still at the grub prompt after rebooting; "geometry (hd" doesn't tab complete, and find /boot/grub/menu.lst and find /grub/menu.lst still give me Error 15: File not found.

Would you suggest I go out and buy an IDE (PATA) drive? My SATA disc isn't recognized.

---

### Post by caljohnsmith on 2008-10-08
> **kartik_vad said:**
> No change :(

Still at the grub prompt after rebooting; "geometry (hd" doesn't tab complete, and find /boot/grub/menu.lst and find /grub/menu.lst still give me Error 15: File not found.

Would you suggest I go out and buy an IDE (PATA) drive? My SATA disc isn't recognized.
Since your BIOS is at least trying to boot your USB drive at this point, that's at least something, so I wouldn't give up on your USB drive just yet. But given the type of Grub behavior you are seeing, it definitely sounds like you have a BIOS issue with your USB drive at this point, so I think tweaking your BIOS HDD settings would be the best thing to try now.

Go into your BIOS and let me know what settings you have related to your USB drive; go ahead and try changing the related settings one at a time, reboot, and see what happens. Be sure to write down the original settings of anything that you change so you can get back to where you started if need be. Let me know how it goes. :)

---

### Post by kartik_vad on 2008-10-09
I disabled the BIOS EHCI handoff and now it works! Thanks a ton for your help; it made an enormous difference! Thanks once again.

---

### Post by caljohnsmith on 2008-10-09
That's great news you can finally boot your USB drive, and I'm glad I could help out. Cheers and have fun. :)

---

