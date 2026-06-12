---
title: "unable to install grub"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2006-11-16
My Kubuntu installation proceeds normally until it gets to installing grub, where it fails with no explanation, just "grub bootloader failed to install" and "this is a fatal error" or words to that effect.

I have tried to install grub from a live-cd shell:
sudo grub-install /dev/hda
but I get: ```
Cannot create directory '/boot/grub': No space left on device
```
but that seems ridiculous: /boot is on /dev/hda5, a 40mb partition and contains only about 7mb, and / is on /dev/hda7, a 20gb partition and less than 10% used.


(I also tried "sudo grub-install /dev/hda5" and "sudo grub-install /dev/hda7" with the same result.)

When I run (from the live cd shell):
grub
it says:
```
Probing devices to guess bios drives.  This may take a long time.
Error opening terminal: bterm
```and exits.


This is a new installation of kubuntu dapper on an "old" machine with an Abit KR7A-133R motherboard.  Windows XP is already installed & working normally.  I have previously had RH9 running on it for several years without problems.  Also, when this problem first occurred I tried installing Debian "testing" on it and it installed with no difficulty.  But I'd rather have Kubuntu.  The box has only a single 80gb ide drive; I disabled raid in the bios.

At first I thought it's a problem with the Kubuntu installer, but that doesn't account for the "no space left on device" error.  And yet, Debian Etch installs ok.  Any ideas?

Ed: problem was simply insufficient space on /boot partition due to reiserfs overhead;  see new thread:
[http://ubuntuforums.org/showthread.php?p=1767646#post1767646](http://ubuntuforums.org/showthread.php?p=1767646#post1767646)

---

