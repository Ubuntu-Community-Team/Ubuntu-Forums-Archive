---
title: "upgrading without Internet fails damagingly"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by engine on 2007-12-27
Tried upgrading from 7.04 to 7.10 with an alternate CD and without an Internet connection. Inserted CD in drive with 7.04 running, accepted "Upgrade" and sat around while the "failed" messages scrolled past :-{

Install failed, with message "file bug-report against update-manager".

These are some of the problems I've noticed since; note that "About Ubuntu" is happily convinced I have 7.10 installed and nothing more to worry about ...

[LIST]
[*]Synaptic won't start
[*][presumably, therefore] Alternate CD no longer recognised as containing an upgrade
[*]USB stick not recognised [see below]
[*]Firefox crashes if I touch the space-bar
[*]PC seems to have lost "boot from CD" awareness
[/LIST]
Help much appreciated!

_____________________________________________________________________

USB message:

Unable to mount the volume.
mount: wrong fs type, bad option, bad superblock on /dev/sdf/1, missing codepage or helper program or other error
In some cases useful info is found in syslog


[  639.228602] sdf: Mode Sense: 0b 00 00 08
[  639.228606] sdf: assuming drive cache: write through
[  639.236990] SCSI device sdf: 250800 512-byte hdwr sectors (128 MB)
[  639.237708] sdf: Write Protect is off
[  639.237713] sdf: Mode Sense: 0b 00 00 08
[  639.237717] sdf: assuming drive cache: write through
[  639.237725] sdf: sdf1
[  639.238842] sd 4:0:0:0: Attached scsi removable disk sdf
[  639.238923] sd 4:0:0:0: Attached scsi generic sg5 type 0
[  639.659916] FAT: Unrecognized mount option "usefree" or missing value

---

### Post by wolfen69 on 2007-12-27
it sounds like too much to try and fix.(although someone may attempt to help) i would re-install. as far as "boot from cd" awareness, did you enable boot to cd in your BIOS?

---

### Post by engine on 2008-01-01
7.10 finally installed, and almost all my data and settings painstakingly restored...

The Alternate CD is fine, so from watching the error messages scrolls past it looks to me as the whole thing was screwed up by transient repository problems. I cannot believe that not being able to install Indic fonts is sufficent grounds for aborting a complete installation! "skip" would perhaps be a handy option.

---

