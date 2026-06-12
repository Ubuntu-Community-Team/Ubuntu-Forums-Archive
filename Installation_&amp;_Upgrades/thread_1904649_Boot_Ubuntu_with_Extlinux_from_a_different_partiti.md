---
title: "Boot Ubuntu with Extlinux from a different partition"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by Questionario on 2012-01-05
Hi,

I installed a few variants of Ubuntu (Ubuntu Oneiric Ocelot 32bit being one of them) on different logical partitions, after the installation they ran fine with the grub2 bootloader.

However I have installed an Extlinux bootloader on a separate primary partition (to boot all the OSs from) and in the extlinux.conf I added the parameters from grub into extlinux.

But Ubuntu seems to have a problem with the fact that it is loaded from a different partition than the installation. I get a kernel panic saying that it was unable to mount the root fs and to set the root properly.

I tried setting root with the UUID as well as by label, both without success.

I am pretty new to this so any help will be appreciated! =)
PS: I want to stick to extlinux (version 4.0.5) and dont want to use grub2.

Thanks

---

### Post by Questionario on 2012-01-05
Anyone who can help me? :(

---

### Post by Questionario on 2012-01-06
Did I post in the wrong forum? If I did something incorrectly or more information is needed please tell me!
Thanks :)

---

### Post by Questionario on 2012-01-06
Here is some more information: As mentioned I am using Extlinux4.0.5
Here is one of the boot menu entries in extlinux.conf:

```
LABEL Ubuntu
    MENU INDENT 1
    MENU LABEL ^Ubuntu Oneiric Ocelot 11.10
        KERNEL /boot/vmlinuz-3.0.0-14-generic
    APPEND root=label=Ubuntu ro quiet splash
        initrd=/boot/initrd.img-3.0.0-14-generic
```I have a boot partition named boot on which the kernel and initrd reside, I just copied the files from the Ubuntu (ext3) partition.

Both partitions reside on the same physical harddrive while Ubuntu is a logical partition inside an extended partition (the boot is a primary partition with the boot flag set).

The error message is:
```
Kernel panic - not syncing: VFS: Unable to mount root fs on unkown block(0,0)
Pid: 1, comm: swapper Not tainted 3.0.0-14-generic #23-Ubuntu
Call Trace:
[<c151a3f2>] ? printk+0x2d/0x2f
[<c151a2d0>] panic+0x5c/0x151
[<c17bfb2b>] mount_block_root+0xb9/0x14c
[<c1136b2c>] ? sys_mknod+0x2c/0x30
[<c17bfd36>] mount_root+0x59/0x5f
[<c17bfe8a>] prepare_namespace+0x14e/0x192
[<c1127ce5>] ? sys_access+0x25/0x30
[<c17bf89f>] kernel_init+0x136/0x13b
[<c17bf769>] ? start_kernel+0x358/0x358
[<c153517e>] kernel_thread_helper+0x6/0x10
```on a different linux version with kernel 2.6.39.4 (based on Ubuntu) I get a bit further, after it seems to be running for a while it comes with the following error message:
```
VFS: Cannot open root device "label=BT5" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)
usb 4-2.2: new full speed USB device number 3 using ohci_hcd
Pid: 1, comm: swapper Not tainted 2.6.39.4 #1
```followed by a call trace very similar to the previous one.
I also tried to use root with the UUID but that didn't change anything.
About the usb line... I do have a USB device connected but I am not booting off of it.

Please help!:confused:

---

### Post by sledgeas on 2012-01-06
In your extlinux.conf change the line

```
    APPEND root=label=Ubuntu ro quiet splash
```

to

```
    APPEND root=/dev/sdaX ro quiet splash
```

where /dev/sdaX is the partition on which you have your Ubuntu (e.g. /dev/sda4).

Mind that posting here you are changing the rules of the game - by using Extlinux bootloader instead of Ubuntu community's favourite GRUB, hence most of the people don't really know how to help, even if they read your post.

Next time write to Extlinux support list.

Enjoy!

--&nbsp;
sledge

---

### Post by Questionario on 2012-01-06
Hi sledgeas,

thank you for taking the time to help me, unfortunately that didn't solve the problem though. The error stays the same...

Ubuntu worked fine with extlinux and the UUID if the boot partition is the same as the install partition but if the boot is on a different partition it won't work :(

As for not using grub... I started using extlinux because of OpenElec (on their website they have a tutorial on how to set up dual boot with extlinux) and also because of SARDU. Basically now I got a grasp on how to write menus in extlinux...
If I'd be able to do the same in grub or at least had the same working config with grub and I'd have a good tutorial on grub, I'd change to grub.... 

This is how my extlinux.conf looks like (I like the backgrounds, colors, submenus, etc.)

```
#
ui vesamenu.c32
MENU title     Media Center (Last Update January 2012)
#
MENU BACKGROUND ./PBXBMC
MENU TABMSG  Media Center MENU
MENU COLOR HOTSEL 30;47      #40000000 #20ffffff
MENU COLOR SEL 30;47      #40000000 #20ffffff
MENU COLOR SCROLLBAR 30;47      #40000000 #20ffffff
MENU COLOR HELP        37;40      #c0ffffff #00000000 std
MENU WIDTH 76
MENU MARGIN 10
#
MENU ROWS 15
MENU TABMSGROW -10
MENU CMDLINEROW 23
MENU ENDROW -1
#
MENU TIMEOUTROW -8
#
#MENU HELPMSGROW 21
#MENU HELPMSGENDROW -1
MENU HIDDENROW -2
MENU HSHIFT 4
MENU VSHIFT 4
MENU HIDDEN
MENU SAVE
PROMPT 0
TIMEOUT 20
#
#
LABEL -
    MENU LABEL Operating System's
    MENU DISABLE
#
#Boot from Windows XP
LABEL XP
    MENU INDENT 1
    MENU LABEL  Boot from Windows ^XP
    KERNEL chain.c32
    APPEND hd0 3
#
#
#Ubuntu
LABEL Ubuntu
    MENU INDENT 1
    MENU LABEL ^Ubuntu Oneiric Ocelot 11.10
        KERNEL /boot/vmlinuz-3.0.0-14-generic
    APPEND root=label=Ubuntu ro quiet splash
        initrd=/boot/initrd.img-3.0.0-14-generic
#UUID=f11e1612-2d22-43d2-91e5-f21f6cf014d2
LABEL -
    MENU LABEL Media Center's
    MENU DISABLE
#
#OpenElec Fusion
LABEL OpenElec
    MENU INDENT 1
    MENU LABEL Open^Elec Fusion
    KERNEL /boot/OpenElec/OEFusionKERNEL
    APPEND boot=LABEL=OEFusionSystem disk=LABEL=OEFusionStorage  quiet
#
######################################
MENU BEGIN Tools
MENU TITLE    Tools
MENU SEPARATOR
MENU BACKGROUND ./OPEN
MENU COLOR HOTSEL 30;47      #40000000 #20ffffff
MENU COLOR SEL 30;47      #40000000 #20ffffff
MENU COLOR SCROLLBAR 30;47      #40000000 #20ffffff
MENU COLOR HELP        37;40      #c0ffffff #00000000 std
MENU WIDTH 76
MENU MARGIN 10
#
MENU ROWS 15
MENU TABMSGROW -10
MENU CMDLINEROW 23
MENU ENDROW -1
MENU TIMEOUTROW -8
MENU HSHIFT 4
MENU VSHIFT 4
LABEL <==Back
    MENU EXIT
######################################
MENU BEGIN BT5
MENU TITLE BackTrack5 R1
MENU SEPARATOR
MENU BACKGROUND /boot/BackTrack/splash.png
MENU COLOR HOTSEL 30;47      #40000000 #20ffffff
MENU COLOR SEL 30;47      #40000000 #20ffffff
MENU COLOR SCROLLBAR 30;47      #40000000 #20ffffff
MENU COLOR HELP        37;40      #c0ffffff #00000000 std

MENU ROWS 15
MENU TABMSGROW -10
MENU CMDLINEROW 23
MENU ENDROW -1
MENU TIMEOUTROW -8
MENU HSHIFT 4
MENU VSHIFT 4
LABEL <==Back
    MENU EXIT

LABEL BT5
    MENU LABEL ^Backtrack5 R1
    MENU INDENT 1
    KERNEL /boot/BackTrack/vmlinuz-2.6.39.4
    APPEND root=label=BT5 ro text splash vga=791
    initrd=/boot/BackTrack/initrd.img-2.6.39.4
LABEL BT5R
    MENU LABEL Backtrack5 R1 (^recovery)
    MENU INDENT 1
    KERNEL /boot/BackTrack/vmlinuz-2.6.39.4
    APPEND root=label=BT5 ro single
    initrd=/boot/BackTrack/initrd.img-2.6.39.4
LABEL BT5MEMTEST
    MENU LABEL ^MemTest
    MENU INDENT 1
    KERNEL /boot/BackTrack/memtest86+.bin
    APPEND console=ttyS0,115200n8
#root=UUID=384d3967-872e-40f8-a53f-9f572401c263 


#
LABEL <==Back
    MENU EXIT    
#
#

MENU END
######################################
#
LABEL SuperGrubDisk2
MENU LABEL ^SuperGrubDisk2
MENU INDENT 1
      KERNEL memdisk
MENU INDENT 1
    APPEND ramdisk_size=100000 initrd=./super_grub_disk.isz
#
LABEL SuperGrubDisk
MENU LABEL ^SuperGrubDisk
MENU INDENT 1
      KERNEL memdisk
MENU INDENT 1
    APPEND ramdisk_size=100000 initrd=./super_grub.imz
#
LABEL HDT
MENU LABEL ^Hardware Detection Tool (HDT)
MENU INDENT 1
KERNEL memdisk
    APPEND iso
    INITRD ./hdt.isz
#
#
LABEL Boot from TestDisk / PhotoRec / LiloPwd
MENU LABEL Boot from ^TestDisk / PhotoRec / LiloPwd
MENU INDENT 1
      kernel memdisk
    APPEND initrd=./TestDisk.imz
#
LABEL PLoP Boot Manager v5.0.13
MENU LABEL ^PLoP Boot Manager v5.0.13
MENU INDENT 1
KERNEL memdisk
MENU INDENT 1
    APPEND ramdisk_size=100000 initrd=./plpbt.imz
#
LABEL FreeDOS
MENU LABEL ^FreeDOS
MENU INDENT 1
KERNEL memdisk
    APPEND iso
    INITRD ./odin.isz
#
#
LABEL <==Back
    MENU EXIT    
#
#

MENU END
######################################

#reboot
LABEL Reboot
    MENU LABEL ^Reboot
    KERNEL Reboot.c32
#

#boot next hdd
LABEL Next
    MENU LABEL Boot ^Next Device
    LOCALBOOT -1




```

any solution to get this working nice and properly would be good..

---

### Post by Questionario on 2012-01-08
am I the only one trying to boot several linux distros and wants to create his own menu?

---

### Post by sledgeas on 2012-01-08
I have MeeGo 1.2 running on my Asus EeePC netbook, with extlinux loader, and it can boot fine another MeeGo 1.1, Ubuntu 10.10 and WinXP.

Here's how the modified extlinux.conf looks like (I copied all missing kernels to my /boot/extlinux directory -- different from you copying them to just /boot(!) Don't forget the initramfs file too for Ubuntu's case, what I assume you did, and double-check the paths!):

```
prompt 0
timeout 1

default vesamenu.c32
menu autoboot Starting MeeGo...
menu hidden

menu resolution 1024 600
menu background splash.jpg
menu title Welcome to MeeGo!
menu color border 0 #ffffffff #00000000
menu color sel 7 #ffffffff #ff000000
menu color title 0 #ffffffff #00000000
menu color tabmsg 0 #ffffffff #00000000
menu color unsel 0 #ffffffff #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000
label meego12
	menu label MeeGo 1.2 (2.6.37.2-8.27)
	kernel vmlinuz-2.6.37.2-8.27
	append ro root=/dev/sda10 quiet vga=current
	menu default
label meego11
	menu label MeeGo 1.1 (2.6.35.13-23.1)
	kernel vmlinuz-2.6.35.13-23.1-netbook
	append ro root=/dev/sda6 quiet vga=current
label ubuntu
	menu label Ubuntu 10.10 (2.6.35-30)
	kernel vmlinuz-2.6.35-30-generic
	append ro root=/dev/sda6 quiet splash initrd=initrd.img-2.6.35-30-generic
label winxp
	menu label WinXP
	kernel chain.c32
	append boot 1

```

Good luck!

--&nbsp;
sledge

---

### Post by Questionario on 2012-01-15
Hi sledgeas,

thanks for your help!
I don't know why but for some reason extlinux does not seem to like if put the absolute paths to the files, I first tried copying the files to the extlinux directory annd adjusted the path but that didn't help.
Once I left out the path completely like in your example, it works! :)
If anyone knows why this is the case I would definitely be interested (especially as this only seems to be a problem with *buntu) in knowing the details :)

Anyhow, thanks for the help.

---

### Post by DJ 1 on 2012-08-28
Hi, a bit of a Linux newbie here... 
I've recently set up extlinux to multi-boot openelec and win7,..... I also wanna get my instal of Xbmcbuntu to boot from extlinux

What's the best thing to stick in my extlinux.configure file
Do I need to put in the full path ?,
What's the #GUUID ?....do I need it ? How would I find that?

I tried 
APPEND /Dev/sda5/ 

.... I get a list of files/ options when I try booting.

---

### Post by DJ 1 on 2012-08-29
P.S.. sorry for resurrecting an old thread, but the topic was spot on for what I was looking for....
Anyone?
Cheers.

---

