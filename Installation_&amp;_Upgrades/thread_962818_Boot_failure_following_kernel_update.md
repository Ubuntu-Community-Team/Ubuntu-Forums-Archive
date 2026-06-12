---
title: "Boot failure following kernel update"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by ChrisPG on 2008-10-29
Hi, I hope someone can help point me in the right direction.  I've been using Ubuntu for a while now, but I'm not so good when things go wrong.  I've managed to solve a few problems by searching the forums, but I've not been able to find a solution to my current problem.

The last couple of times that I've done a kernel upgrade Ubuntu has stopped working so I've now set grub to boot "default 4" when the following are my list of options:

```
Ubuntu 8.04.1, kernel 2.6.24-21-386
Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-19-386
Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
Ubuntu 8.04.1, kernel 2.6.15-52-386
Ubuntu 8.04.1, kernel 2.6.15-52-386 (recovery mode)
```

Now, the problem I have is that if I try either of the newer kernels I just get a black screen.  I saw another forum where someone else was having a similar problem, but theirs was playing the drum sound to indicate that they'd got to the logon page; my PC doens't get that far.

If I select the newest kernel and press [Alt][F1] during boot I get the following on the screen:

```
Booting 'Ubuntu 8.04.1, kernel 2.6.24-21-386'

root (hd0,0)

 Filesystem type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz.2.6.24-21-386 root=UUID=f8
1f27fc-7e08-48c0-a66e-2ea0f051803 ro quiet splash

  [Linux-bzImage, setup=0x2a00, size=0x1c08f8]
initrd  /boot/initrd.img-2.6.24-21-386

  [Linux-initrd @ 0x1f671000, 0x7efeb8 bytes]

Loading, please wait...
(long pause while we wait for it!)
  Check root= bootarg cat /proc/cmdline
  or missing modules, devices:cat
```

It's in a huge font size/low screen res so that fills the entire screen.  I hope that's enough for someone to know what's wrong.

For what it's worth, I have a Dell Optiplex GX260.

Thanks for reading this and I hope you can help suggest what I may be able to do to fix this.
Regards,
Chris.

---

### Post by Crafty Kisses on 2008-10-29
Try removing the words ```
silent
``` And ```
splash 
```From the Grub configuration in ```
/boot/grub/menu.lst
``` See if that works, if that doesn't work, you may want to revert back to an older kernel.

---

### Post by ChrisPG on 2008-10-29
Thanks Codename, that enabled me to see a lot more information. I think the key line is this:

```
Alert! /dev/disk/by-uuid/f81f27fc-7e08-48c0-a66e-2ea0f2
051803 does not exist.  Dropping to a Shell!
```

I presume that there must be some way that I can get it to redownload the relevant files?

---

### Post by Crafty Kisses on 2008-10-29
Try to add the following to the Grub kernel line:```
break=mount
```Once you have done that, reboot and try again.

---

### Post by caljohnsmith on 2008-10-29
That UUID error you got also is the same UUID that was used to boot Ubuntu from your Grub's menu.lst, so it might be that you just have a problem with your menu.lst. When you are in Ubuntu, how about opening a terminal (applications > accessories > terminal), and posting:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /boot/grub/menu.lst
```
And we can work from there.

---

### Post by ChrisPG on 2008-10-31
Hi Guys,

Thanks for those helps - unfortunately I didn't have a chance to try them out last night as my brothers car broke down... All being well, I'll try them out tonight and let you know how I get on.

Thanks again,
Chris.

---

### Post by Crafty Kisses on 2008-10-31
> **ChrisPG said:**
> Hi Guys,

Thanks for those helps - unfortunately I didn't have a chance to try them out last night as my brothers car broke down... All being well, I'll try them out tonight and let you know how I get on.

Thanks again,
Chris.

No problem, please post back, hopefully we can help you.

---

### Post by ChrisPG on 2008-11-01
Well, I've done what both of you suggested and posted the results below; it seems that this computer was once running on mirrored drives - I've only ever had one HD in it since I was given it a while back and the first thing that I did was to get rid of Windows and install Ubuntu.  I'd not realised that it was trying to sort out a RAID thing before - I presume that's not the problem as the older kernel runs fine??

Anyway...I added
```
break=mount
```
and now this is as far as it gets... (I left out all the numbers on the left of each line as I figured that they're just some kind of time thing and it was getting a bit much to type it all out)

```
sd 0:0:0:0: Attached scsi generic sg0 type 0
scsi 1:0:0:0 Attached scsi generic sg1 type 5
scsi 1:0:1:0 Attached scsi generic sg2 type 5
input,hidraw0:USB HID v1.11 Mouse [Saitek SaitekObsidian Mouse] on usb-0000:00:1d.1-1
sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
input: Silitek USB keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/inpit/input3
input,hidraw1:USB HID v1.00 Keyboard [Silitek USB keyboard] on usb-0000:00:1d.1-2
input: Silitek USB keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.1/inpit/input4
usbcore: registered new interface driver usbhid
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
md: md0 stopped.
md: bind<sda>
md: md0: raid array is not clean -- starting background reconstruction
raid1: raid set md0 active with 1 out ot 2 mirrors
```

It stays at this point for ages (left it for a couple of hours to see if anything more would happen), with no sign of any disk activity at all.  Then, the details as requested by caljohnsmith are as follows:

```
chris@ubuntu01:~$ sudo fdisk -lu

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004f5d1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   231432389   115716163+  83  Linux
/dev/hda2       231432390   234436544     1502077+   5  Extended
/dev/hda5       231432453   234436544     1502046   82  Linux swap / Solaris
chris@ubuntu01:~$ sudo blkid -c /dev/null
/dev/hda1: UUID="f81f27fc-7e08-48c0-a66e-2ea0f2051803" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="ac0d0295-72ce-45e6-9746-5e3113a4bf4e" 
chris@ubuntu01:~$ cat /boot/grub/menu.lst
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
default		4	

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
# kopt=root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro break=mount 
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.15-52-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro quiet splash
initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.04.1, kernel 2.6.15-52-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=f81f27fc-7e08-48c0-a66e-2ea0f2051803 ro single
initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Crumbs, this is a monster long post - I really appreciate you guys going through all this code :)  Oh, and just in case you think I'm nuts, the second keyboard is actually a PS2 one that I plugged in so that I could get into the grub menu as I normally just have a USB one!

---

### Post by ChrisPG on 2008-11-10
bump.

---

### Post by caljohnsmith on 2008-11-10
Since your computer did have a RAID setup before, have you checked your BIOS to make sure all your RAID settings are disabled? Also is the "dmraid" package installed? If it is, I would think you would want to uninstall it. You can check with:
```
apt-cache policy dmraid
```

---

### Post by ChrisPG on 2008-11-11
I spent a while going through all the options in the BIOS and couldn't see anything about RAID in there.

As suggested, I entered
```
apt-cache policy dmraid

```

and got the following:
```
dmraid:
  Installed: (none)
  Candidate: 1.0.0.rc14-0ubuntu3
  Version table:
     1.0.0.rc14-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/universe Packages

```

So I don't think that we're any further forward :(

---

