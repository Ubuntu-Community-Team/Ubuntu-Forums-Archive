---
title: "Fresh install hangs at &quot;mounting root filesystem&quot;"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by akiratheoni on 2007-09-24
Okay this is really making me mad. 

I was quad booting Windows Vista, Ubuntu, Fedora, and Mandrive. No idea why. Don't ask. Everything was fine, except Vista's partition was 300GB on a 500GB hard drive; Ubuntu had only about 15GB. Considering that I'm using Ubuntu more, I had too little room and was constantly running out of space. So I got a 500GB external hard drive and transferred files over, and decided to reinstall Windows Vista and Ubuntu (I want a fresh install anyway).

So I installed Vista first (because of the whole overwriting MBR thing) then I install Ubuntu. First of all, the Live CD resolution was only 640x480 and wouldn't change, so on my screen, it was really hard to go through the installer, because the installer wouldn't fit on my screen. I had to drag some panels around to  view the bottom portion of the installer. 

But anyway, that's not really the problem (though I am pissed at it). I assume my problem is with the partition table.

My partition table looks like this (or at least from the Gparted Live CD I'm currently booted into):
/dev/sda is 465.GB

/dev/sda1 ntfs 50.78GB <--- Vista install
/dev/sda2 ext3 48.42GB <-- current operating system (Linux Mint, I'll explain in a moment)
/dev/sda3 swap 4.28GB <-- I was always told to make my swap 2x my RAM, I have 2048MB RAM, and this is almost the same amount before I did a fresh install.
/dev/sda4 extended with:
----/dev/sda5 ext3 96.86GB <-- When I installed I put the mount point as '/home'... I think that's right, or maybe that's the problem? I want my /home partition on another drive.
----/dev/sda6 fat32* 141GB <-- Drive so I can share my files between Ubuntu and Vista
----/dev/sda7 fat32* 125.85GB <-- See above. Ubuntu/Linux Mint install wouldn't allow me to create anything bigger than like 150GB so I just divided it.

My problem? When I boot up, it just hangs there. I edited the GRUB so it would display the text as it booted up. It would go to 'mounting root file system' and just hang.

So I got pissed at Ubuntu and threw in my Linux Mint CD I had lying around. I installed it, using the same exact partition table and guess what -- it did the same thing. Hung at the SAME EXACT part.

What the heck is wrong with this? Ubuntu has been working FINE for the past couple months, and now this? Please help, or I'll keep bumping this topic until I get help :(


EDIT: It just changed a bit. But I don't know what it means. I'll type out the text:

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda1 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian: 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh" can't access tty; job control turned off
(initramfs)_

And that _ is a blinking cursor. What do I do? I don't know where it got the /dev/hda1 because my hard drive is /dev/sda1...

---

### Post by dabl on 2007-09-24
Probably your /boot/grub/menu.lst boot menu does not match your /etc/fstab file, in terms of identifying which partition has the Linux kernel on it.  You say (in fstab) that it is on /dev/sda2, but Grub is looking for it on /dev/sda1 (which Grub calls hda1).

To fix what you've got, you need to edit /boot/grub/menu.lst.  Here are a couple of links -- note that the Grub naming convention for hard drives and partitions is not quite the same as that used for /etc/fstab.

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Here are a couple of pointers, if you decide to re-partition and re-install:

"swap" can safely be set at 0.5GB on these new systems if you have 1GB or more of RAM, and won't likely see it used at all.

"/" can be 6 or 7 GB

You are wise to make "/home" a separate partition -- spares your data when stuff goes wrong with the OS.  :)

---

