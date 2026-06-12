---
title: "Adding Windows NT / 2000 / XP to existing Linux / Unix installation (where ntldr can'"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by Jonie on 2006-08-19
I know there are many ways to dual boot Linux or *BSD with different bootloaders (FOSS or Microsoft). But it's always been a pain to boot Windows when the first partition is occupied by a diffrent than FAT / NTFS filesystem and so Windows NT (as we'll call it since now) cannot put its startup files on it. Of course, you may for example try to chainload it with GRUB:

rootnoverify (hd0,0)
chainloader +1

but any other minor than 0 (ex. hd0,1) will fail.

The problem as I guess is that Windows NT or XP bootcode expects ntldr to be on the first partition on the drive. Even, if some branded systems use first hidden partition, startup files reside or are remapped so that Win NT sees it's booting from first sector of the second track of the drive.

Of course, there is no problem to load any Win 9x system this way.

With NT, bootup process will just hang. Even restoring standard MS-DOS bootstrap and activating NT parttion won't lead to bootable system.

Let say we have:

hda1 or hd0s1 - Linux / Unix

hda2 or hd0s2 - Windows XP

hda2 is flagged actve.

The only way to boot such system is to have bootable "MS-DOS" or rather NTLDR floppy, with ntldr, ntdetect.com and boot.ini.

Don't try fixboot from the repair console. You may damage filesystem this way and it won't help.

And here comes the SYSLINUX.

Just download XP floppy quick boot disk form bootdisk.com

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)



The tricky part is you have to edit boot.ini on the floppy

example:

......rdisk(0)partition(2)\WINDOWS...

so that it will point to partition where NT resides.

Make image of it:

dd if=/dev/fd0 bs=512 of=/your home folder/xpboot.img

Copy it to the /boot directory.

Dowload SYSLINUX:

sudo apt-get install syslinux

it will create bunch of files in /usr/lib/syslinux

One we need is memdisk.

Copy memdisk to /boot directory

Create entry in GRUB config (grub.conf or menu.lst, whatever distro you have):

title Widnows XP
kernel /boot/memdisk
initrd /boot/xpboot.img

And you're done!

NT will boot from any place on the disk.

There is a drawback: since it is an emulation of floppy, the original floppy will be remapped as B:.
After boot, there will be two floppies in explorer A: and B:. As long as there is floppy in the system, this won't hurt. Floppyless systems may experience explorer lockups when listing drives.


I succeeded to boot XP with Ubuntu 6 this way. Any comments are welcome.

Jon

---

### Post by K.Mandla on 2006-08-20
Very, very clever! I'm making a mental note of this, in case I need it one day. Thanks!

---

### Post by Jonie on 2006-08-20
the problem reminds me of something I once did. The disk was split in half for Win98 - hda1 and hda5. I booted XP from CD, and instead of formatting I deleted and recreated hda1 (so called C: for some people). Since former partitioning from 98's fdisk left no space at the end of disk (a few megabytes is needed for future disk spanning in 2k/XP) the stupid XP partitioner left it...before hda1.
XP installed with no error, but wouldn't boot no more. MISSING OPERATING SYSTEM. Press a key to reboot...

After moving hda1 with Partition Magic the few megs back freshly installed XP booted for the first time :) 

So I think there is no other way for such bootup than using SYSLINUX. Or am I wrong?

---

### Post by Jonie on 2006-08-20
BTW, in XP disk manager, there is no partition flagged system, just boot.

The extra floppy can easily be disabled via device manager.

---

