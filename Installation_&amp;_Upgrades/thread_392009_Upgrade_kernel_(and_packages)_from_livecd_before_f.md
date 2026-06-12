---
title: "Upgrade kernel (and packages) from livecd before first reboot?"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by dan_linder on 2007-03-24
Is it possible to update the installed kernel after the installation completes but _before_ the system reboots?

I'm trying to install Ubuntu Server 6.06-1.  It includes the 2.6.15 kernel, but there is a known issue with that kernel and my hardware (see note 1 below).  What I would like to do is boot from the LiveCD, perform my install, and then immedieatly perform an apt-get upgrade to the latest 2.6.18 (or higher) kernel.

Is this possible with some "chroot" magic at the command line?

Dan

Note 1: It's a Compaq DL360 and the compaq array controller driver can't be loaded as a module during boot in pre-2.6.18 kernels.  See: [http://www.mcnabbs.org/andrew/linux/proliant/](http://www.mcnabbs.org/andrew/linux/proliant/)

---

### Post by dan_linder on 2007-03-24
I answered my own question.  

After thinking about the chroot a bit, I came up with these steps:
1: Boot from the CD (Ubuntu Server 6.06.1 in my case), but choose "Rescue Mode"
2: In the shell that comes up, mount each of the partition "correctly" under /mnt.  I.e. mount the "root" filesystem in /mnt/root, mount the "/boot" filesystem under /mnt/root/boot, mount "/home" under /mnt/root/home", etc.
[INDENT]- If you only have a single "/" filesystem, then just mount it under /mnt/root.
- In my case, /dev/ida/c0d0p3 was /, c0d0p1 was /boot so I used these commands:
 a: mkdir /mnt/root
 b: mount /dev/ida/c0d0p3 /mnt/root
 c: mount /dev/ida/c0d0p1 /mnt/root/boot
[/INDENT]3: Check that you can see the files in /mnt/root/boot, especially config-2.6.15-*, grub/, etc.
4: Run [FONT="Courier New"][SIZE="3"]"chroot /mnt/root /bin/sh"[/SIZE][/FONT]
[INDENT]- This runs the shell, but makes it think that "/mnt/root" is the _**root**_ of the filesystem.
- From this point on, any commands will affect the filesystem on the hard drive and not the temporary rescue filesystem.
[/INDENT]5: Run [FONT="Courier New"][SIZE="3"]"apt-get update"[/SIZE][/FONT] to update the list of available files to download.
6: Run [FONT="Courier New"][SIZE="3"]"apt-get upgrade"[/SIZE][/FONT] to download and upgrade them.
7: Follow the steps to compile a custom kernel for Ubuntu/Debian systems.
[INDENT]- I followed the steps here: [http://www.quietearth.us/articles/2006/09/15/Ubuntu-Compiling-a-custom-kernel](http://www.quietearth.us/articles/2006/09/15/Ubuntu-Compiling-a-custom-kernel)
[/INDENT]8: For my DL380 (and DL360's too), after you copy the correct /boot/config-* file to /usr/src/.config, change the line that states:
[INDENT]CONFIG_BLK_CPQ_DA=m
[/INDENT]to
[INDENT]CONFIG_BLK_CPQ_DA=y
[/INDENT]- The "y" means to compile it _into_ the kernel, not as a dynamically loaded module.
9: Reboot and ensure you boot into the new kernel.

Until the kernels provided through the repositories are 2.6.18 or higher, you'll need to upgrade to the latest kernel, but re-compile it following the QuietEarth.us article.

---

### Post by dan_linder on 2007-05-04
A fellow Debian/Ubuntu user on the local user group mailing list proposed this solution:
1) Add cpqarray to /etc/mkinitramfs/modules
2) rebuild kernel initrd with
  /sbin/mkinitramfs -o /boot/initrd.img-<kernelversion> <kernelversion>

So, now my "/etc/mkinitramfs/modules" file looks like this:
```
root@www:~# cat /etc/mkinitramfs/modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod
cpqarray
```

For the second step, you can run:
```
/sbin/mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
```

Dan

---

