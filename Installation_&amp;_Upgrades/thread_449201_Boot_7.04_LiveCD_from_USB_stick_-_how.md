---
title: "Boot 7.04 LiveCD from USB stick - how?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by JohnnyS987 on 2007-05-20
Hi, all.

I have a laptop (Thinkpad X23 with 640MB RAM) that I want to put Ubuntu 7.04 onto, and I don't want dual boot; just Ubuntu. The problem is that this system does not have a CDROM I can boot from. There is no way I can get this system to boot from a normal CD, so I'm trying to get the "Live CD" (ubuntu-7.04-desktop-i386.iso) to boot off a 1GB USB stick. 

I followed the instructions from "Preparing Files for USB Memory Stick Booting" from [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html) and I was able to boot part way but I'm now stuck. I get to a point where the hardware is detected, then a long pause and I get the following:

Check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/ram does not exist. Dropping to a shell

Then there's a bunch of info about "Busybox".Then I see the following:

/bin/sh: can't access tty: job control turned off.
(initramfs)

As described in the "Preparing Files for USB Memory Stick Booting" document, I followed the section "Copying the files — the flexible way", I then copied the Ubuntu ISO file "ubuntu-7.04-desktop-i386.iso" to the root of the USB stick. I set up my syslinux.cfg as follows:

default vmlinuz
append initrd=initrd.gz ramdisk_size=12000 root=/dev/ram rw

I also tried it as follows:

default vmlinuz
append initrd=initrd.gz ramdisk_size=120000 root=/dev/ram rw

However, this made no difference.

Can anyone tell me what to do next? Why is the RAMdisk not loading up? Do I need to put the name of the ISO file in syslinux.cfg?

Thanks in advance for any help.

John S.

---

### Post by JohnnyS987 on 2007-05-20
Anyone? I have googled and read all the documentation I could find on this topic but had no luck. Any help will be greatly appreciated!!!

TIA for any help!

---

### Post by TheOnlyEnglishRose on 2007-05-20
what operating system are you currently using?

---

### Post by JohnnyS987 on 2007-05-20
Thanks for your reply!

Right now the hard disk in the laptop is blank. I do have a couple of other desktop systems. One runs Ubuntu 7.04 and the other runs XP. i have been using those systems to configure the US key, which is a 1GB key.

What I'm hoping to do is to boot up the USB key and run the installer to put 7.04 on my nice clean new hard disk. :>

---

### Post by TheOnlyEnglishRose on 2007-05-20
I wish my BIOS supported USB booting... I don't think I have any way to install Ubuntu.

---

### Post by JohnnyS987 on 2007-05-20
Anyone? I'd really like to get this working, and I'm sure lots of people would like to be able to get a USB stick booting.

:)

---

### Post by calinb on 2007-05-20
John,

Here's another howto that I've found to work:

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

Keep in mind that persistence (unionfs) is currently broken in 7.04.  Use 6.10, if you need persistence.

[http://ubuntuforums.org/showthread.php?p=2687688#post2687688](http://ubuntuforums.org/showthread.php?p=2687688#post2687688)

Also, USB boot can be problematic on many, even new, computers.  Try "hard disk" emulation first, if your BIOS supports it.  Then try all the others.  You say you don't have a CD-ROM drive.  How about a floppy drive?  I put grub on a floppy disc (and CD) and can use either to boot to a Ubuntu USB stick.  However, Grub still uses BIOS but it can provide a workaround, sometimes.  If you have rawrite or some other way to write the image, I can make my very simple grub floppy image available to you.  If I find time, I'll post the steps needed to create it.  I'm sure you can find a wiki on installing grub to a floppy somewhere.  I converted the Ubuntu LiveCD syslinux.cfg file to a menu.lst/grub.conf file for grub.  Just point grub to your USB device.  Grub allows you to edit the boot command line at each boot, if the device isn't where you thought it would be when you wrote the menu.lst file.

-Cal

Here's a grub image I made with RawWrite for windows.  It's the only machine I have, ATM, with a floppy drive.

---

### Post by JohnnyS987 on 2007-05-21
Cal,

Thanks. The info on pendrivelinux.com was exactly what I needed to solve the problem. I was able to get the 7.04 liveCD onto the 1GB USB thumb drive, boot from it and install to the ThinkPad X23. As a matter of fact, I'm posting this from the laptop right now! Whee!!!

Now I just need to figure out how to get the MadWifi driver to use 802.11a instead of 802.11g. I'll just go and start reading up on the Wiki...

Thanks very much!

JS

---

