---
title: "missing upgrade-from-grub-legacy"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by prophet_ on 2010-07-31
Hi!

I am trying to upgrade to grub2 on Ubuntu 8.04 following the procedure in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Everything went fine, I accepted the chainloading of grub2 to test it first, and now I have to install it.
The script is upgrade-from-grub-legacy but it is not installed on my system!?
It should be a part of grub-pc package but it is not!
```

$ dpkg -L grub-pc|grep bin
/usr/bin
/usr/bin/grub-mkimage
/usr/bin/grub-mkrescue
/usr/sbin
/usr/sbin/grub-setup
/usr/sbin/grub-mkdevicemap
/usr/sbin/grub-emu
/usr/sbin/grub-probe
/usr/sbin/grub-install
/usr/sbin/update-grub
/usr/sbin/grub-set-default
/usr/sbin/update-grub2

```
grub-pc version is the latest one for Hardy Heron 

```

robert@rjurinac1:~$ dpkg -l grub-pc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  grub-pc                  1.96+20080203-1ubuntu2   GRand Unified Bootloader, version 2 (PC/BIOS version)

```

Checking on packages site on file list for this package it doesn't contain upgrade-from-grub-legacy script
[http://packages.ubuntu.com/hardy/i386/grub-pc/filelist](http://packages.ubuntu.com/hardy/i386/grub-pc/filelist)

Checking file list for karmic grub-pc package, shows that it contains the script.

So did anybody tried to upgrade using the script from some other version, or used some other way to upgrade to grub2?

Thanks,

p

---

### Post by dino99 on 2010-07-31
this is how i have done it:

- boot the distro i want to install grub2 (grub-pc) on
- remove menu.lst
- open synaptic, search "grub" and remove/purge every installed package found
- install grub-pc and grub-common on the distro mbr when asked (/dev/sdx, where x is the mbr: a or b or c or ...)

that it

---

