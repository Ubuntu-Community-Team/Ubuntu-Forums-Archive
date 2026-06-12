---
title: "[SOLVED] isolinux trouble"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by beauman on 2008-10-03
Hi!

I have Ubuntu installed on a USB-Stick and
I would like to boot it on my MacBook.

The usual Boot-CD I use on computers that
have problems booting directly from the stick does 
not work. It is grub based and it says: "Loading stage 2"
and freezes.

Anyway, since a normal Ubuntu installation CD boots perfectly,
I chose to compile a new boot CD, based on the bootloader
from the install-CD, isolinux.

It boots, I can choose a boot label at the prompt.
Then the kernel from the CD is unpacked und the kernel 
output quite a lot of message about loaded drivers.

But it panics, when it trys to mount the root file system.
It says "can't execute /casper/scripts".

If I boot the MacBook with the ubuntu installation-CD,
the USB-Stick is device /dev/sdb6

Here is my isolinux.cfg:

```


display message.txt
prompt 1
timeout 0

LABEL a
  kernel /casper/vmlinuz
  append  root=/dev/sdb6 boot=casper initrd=/casper/initrd.gz load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6464

LABEL b
  kernel /casper/vmlinuz
  append  root=UUID=4ac9f56c-984a-438d-ae06-b44ad09d1540 boot=casper initrd=/casper/initrd.gz quiet  --

LABEL c
  kernel /casper/vmlinuz
  append  root=UUID=4ac9f56c-984a-438d-ae06-b44ad09d1540 boot=casper initrd=/casper/initrd.gz load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6464



```

and the content of the boot cd:

```


 ~/temp/bootcd$ ls -Rh cdroot/
cdroot/:
casper  isolinux.bin  isolinux.cfg  message.txt

cdroot/casper:
initrd.gz  vmlinuz


```

Has anybody an idea, how the correct boot entry in isolinux.cfg
would look like?

Thanks a lot. It would really be of great help to me, if
you get this issue fixed. I need Ubuntu running on the laptop
quite urgently...


Thanxs a lot!!

Greetings, beauman

---

### Post by ghantoos on 2008-10-03
It seem like you shouldn't  specify the root as a hard drive.

Take a look at this:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I have a persistent Ubuntu on my USB that I use for use and installation purposes.

Here is what my syslinux.cfg looks like, if this can give you some idea:
```

DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL persistent
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```Hope this helps,

Cheers,

---

### Post by beauman on 2008-10-12
Hi! I found the solution. I just didn't read the instructions
from 
[http://www.linuxroute.de/howto/isolinux_bootcd.php]("http://www.linuxroute.de/howto/isolinux_bootcd.php")
carefully enough.

It must be:

```

display message.txt
prompt 1
timeout 100
default a

LABEL a
  kernel /casper/vmlinuz
  append  root=/dev/sdb6  initrd=/casper/initrd.gz load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6464


```

What I tried was wrong:
```


LABEL does_not_work
  kernel /casper/vmlinuz
  append  root=/dev/sdb6 boot=casper initrd=/casper/initrd.gz load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=6464

```

So it was just the boot=casper (that I took from the isolinux.cfg of the ubuntu installation cd) :):)

It now works really cool. If the usb-stick is not pluged in during
boot, it will even wait for it! 

There is one thing I like to mention:
I don't use the persistance mode. Is that a good thing?

I would like to explain the details of my Ubuntu-on-a-USB-stick
"project" a little more detailed:

My idea was to clone an existing system on a stick. Now my
new hobby is to boot this stick on every machine I can get :)

I took a 16GB Stick, and repartitioned it with gparted. 
I resized the ntfs partition to 1G, to be able to work
with the stick under windows. I then created an extended
partition containing a swap and an ext3 partition.

Then I copied an up-to-date version of Ubuntu onto the stick:
I used the Ubuntu Install CD to boot a linux, but not the
installed version on the disk. I then mounted the stick and 
the harddrive partition, that contains the system I like to
clone. With "cp -a" (to preserve the file attributes) I
copied the complete system to the stick.

Then I edited three files:

 - /etc/fstab
 - /boot/grub/menu.lst
 - /etc/X11/xorg.conf

To clone a ubuntu system, you just have to adjust the so called UUIDs
(unique IDs for a certain partition on a unique storage device like
a hard drive or usb stick) in /etc/fstab and /boot/grub/menu.lst.
You can use the command 
```
sudo blkid /dev/partionion_XYZ
``` to get that id. In
/etc/fstab you have to adjust the partition of the root and the swap 
partition, in /boot/grub/menu.lst its just the UUID of the root
partition.

The file /etc/X11/xorg.conf quite often contains "hardwired"
information about the hardware, that runs the installation.
This is especially the case, if you run a dual-head setup or
desktop acceleration.

Therefor I use a "standard" configuration in /etc/X11/xorg.conf,
that should run everywhere:

```


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

This is it. The system is now cloned onto the stick.
Now the question is, how to boot from this this stick?
I am using three different techniques:

 - boot from the MSR of the stick
 - boot with a boot cd based on supergrub
 - boot with a boot cd based on isolinux

1.) To boot from the MSR of the stick:
Mount your stick, redirect /dev, /proc and sysfs to the stick:
```

mount --bind /dev /target/dev
mount -t proc proc /target/proc
mount -t sysfs sysfs /target/sys

```

and "chroot" into the cloned installation. Then install grub.

This variant works on all PCs, that have a BIOS-boot menu.
During boot you have to press a special key to get into this boot-menu.
Choose the USB stick, and boot it.

2.) Variant: Boot CD based on supergrub: Quite a lot PCs have
problems booting directly from a usb stick. But all PCs
support booting from CD. Thats why I generated a boot cd, which 
lets you select the device (like the BIOS boot menu in variant 1.)
and then boots from the stick.
See
[http://forum.ubuntuusers.de/topic/grub-unabhaengig-von-physikalischer-position-/]("http://forum.ubuntuusers.de/topic/grub-unabhaengig-von-physikalischer-position-/")

Go to my post from the 26. September. I explained in english how it works
and what you have to do, to make your own supergrub-based boot cd.

3.) Variant: As mentioned, grub hangs an a MacBook. So
I created a second boot cd based on isolinux, which does the trick.

Does anybody think, this subject should be written down in a
real tutorial? If so, can somebody explain, how to write such an
tutorial? (How to get the web space and so on)
Before I would go in public with such an tutorial,
I would like to have some people reading it and proposing
improvements for quality insurance.

With friendly regards,
beauman

---

