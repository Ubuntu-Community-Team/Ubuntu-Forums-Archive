---
title: "warning: 9.10 upgrades yesterday screwed up laptop"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2009-09-16
I have been running 9.10 for a month, yesterdays upgrades screwed up laptop (i think init was switched to ubstart and the allmount package) 

After loading grub and before displaying the screen for disk decryption password it starts giving the errors and beeping the builtin speaker insanely:

[udevd 963] unknown key SYMLINK{unique} in /lib/udev/rules.d/50-udev-default.rules:3

[udevd 963] unknown key SYMLINK{unique} in /lib/udev/rules.d/50-udev-default.rules:4

I was able to load the grub selector and go with kernel recovery mode, then in networked root shell do an aptitude upgrade which install allmount that was missing before, after restart my full disk decryption password was not accepted anymore!!!

It gives the error /dev/mapper/x-root does not exist. Which I think could be related to it not being access the encrypted drive and drops me to the limited built-in shell (ash).

Any help or ideas appreciated.

---

### Post by slakkie on 2009-09-16
Hi, have a look in the karmic forum. This has been the #1 topic..

---

### Post by jackmetal on 2009-10-15
> **slakkie said:**
> Hi, have a look in the karmic forum. This has been the #1 topic..

I am having this same exact problem and have been searching the net and the ubuntu forums but haven't found a solution yet.  I did a clean install of 9.10 beta, encrypted all filesystems (except /boot of course) and all was working great.  After I did an apt upgrade, it no longer boots and drops me to the initramfs shell.  The error it gets before dropping to shell is "ALERT! /dev/mapper/sda3_crypt does not exist."

Thank-You very much for any help!

---

