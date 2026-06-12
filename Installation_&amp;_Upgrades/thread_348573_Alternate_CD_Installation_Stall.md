---
title: "Alternate CD Installation Stall"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by dorion on 2007-01-29
Hi, I'm having problems in the actual install process of Ubuntu under the Alternate CD. I've finally got the right setup to get the install to boot... remove my overclocks, disable USB in BIOS, and choose OEM mode with no parameters. Now my problem is that the install process freezes at 6% saying:
> Loading Module 'trm290' for 'IDE Chipset Support'

The rest of the post is about problems that I think may be causing this, no need to read if you know my problem right now.

Now I kinda expected this to happen. I'm running 2 SATA drives RAIDed on the VIA chip, I have my SATA DVD-RW Drive running off the Promise chip on my board. Lastly I have a Hard drive(the destination for my install) and a slaved DVD drive running on the PATA of the VIA chip. This is the only way I can have Windows run without blue screening randomly at boot.

**AND**

I have two Alternate CDs that I have been using, one has been burned at 2x, one at 4x. Both pass md5 Summer, but they have 6 errors. Now I have tried to get rid of these errors, 5 of them stem from missing files and one from a erroneous hash. The errors are not my fault as far as I can tell. I have used 3 different burning programs, and 3 different download sources. It could be my drive or the CDs, but I doubt it since I have a stack of identical CDs with identical errors in the trash.

Here are the 6 files that fail MD5Summer
> .\install\netboot\pxelinux.cfg\default ERROR: E:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.
.\pool\main\l\linux-source-2.6.17\firewire-core-modules-2.6.17-10-generic-di_2.6.17-10.33_amd64.udeb ERROR: E:\.\pool\main\l\linux-source-2.6.17\firewire-core-modules-2.6.17-10-generic-di_2.6.17-10.33_amd64.udeb does not exists.
.\pool\main\l\linux-source-2.6.17\pcmcia-storage-modules-2.6.17-10-generic-di_2.6.17-10.33_amd64.udeb ERROR: E:\.\pool\main\l\linux-source-2.6.17\pcmcia-storage-modules-2.6.17-10-generic-di_2.6.17-10.33_amd64.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.17\nic-restricted-firmware-2.6.17-10-generic-di_2.6.17.5-11_amd64.udeb ERROR: E:\.\pool\restricted\l\linux-restricted-modules-2.6.17\nic-restricted-firmware-2.6.17-10-generic-di_2.6.17.5-11_amd64.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.17\nic-restricted-modules-2.6.17-10-generic-di_2.6.17.5-11_amd64.udeb ERROR: E:\.\pool\restricted\l\linux-restricted-modules-2.6.17\nic-restricted-modules-2.6.17-10-generic-di_2.6.17.5-11_amd64.udeb does not exists.

The 5th error bothers me the most.

Anyways what can I do to move on to 7% on the install, that way I can find another problem wrong with my System.

---

### Post by dorion on 2007-01-30
Anything? Is there some higher support I can goto?

---

