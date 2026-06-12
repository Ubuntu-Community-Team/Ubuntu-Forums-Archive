---
title: "USBuntu"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by drynish on 2007-03-28
Some reflexion around Ubuntu on a stick:

I would like to build a script to build USB / CDRW upgradable ubuntu.

[LIST]
[*] Built on squashfs + aufs to allow edition of files + session saves. Info will be saved on the USB key / CDRW .
[*] Built with the use of [linux-live]("http://www.linux-live.org/") scripts
[*] Packaging customizable for the base system since we completely build the distribution.
[*] Use of debootstrap for the installation of the base system.
[/LIST]
Steps for the creation in my head:

[LIST]
[*]Install of a base install (debootstrap) into /tmp/livecd
[*]Install additionnal package from a list in a file (allow customization)
[*]Remove Kernel / Kernel modules (we will use Linux-live one) *** Might cause issue ***
[*]Remove unecessary files
[*]Download Live-Linux script
[*]Build the live distrib
[*]Install to CDRW or USB Key
[/LIST]
What are you thoughts around this?

Michel

---

### Post by flywheelbot on 2007-08-30
Michel,

Sounds like a good plan.  I've recently finished something like you suggest (first for 6.10, and now for 7.04), and have a snappy, lightweight GTK2 + Openbox solution booting--total size of the compressed file system is 320 Megs.

I think it's easiest to start from scratch, ie:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Instead of modifying a LiveCD.  It just takes too long to strip out what you DON'T want if you're trying to strip things down.

I've also modified casper (in initramfs-tools scripts) to load the whole OS into RAM in compressed format of SquashFS if possible, as per this HowTo:

[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

and made some other modifications (created a default password, disabled auto logins, modified user groups), all in the /usr/share/inintramfs-tools/scripts

Must admit that I still haven't gotten AUFS working--I'd eventually like to replace UnionFS with AUFS--the prospect of dynamically altering branches offers some neat possibilties.  Installing additional software, without stuffing everything into RAM, that sort of thing.  I believe puppy linux is using AUFS.

Best of luck.  Are you (or anyone else who might read this) actively pursing this goal?

-flywheelbot

---

