---
title: "Cloned HDD Boot problem"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by olympic on 2012-01-18
Trust I am placing this query in the correct forum.

I have a triple boot hdd (320GB)with Win7, Linux Mint 11 and Ubuntu 11.10 installed and am using BURG to boot.

Yesterday I obtained a spare 320GB hdd and used Clonezilla to make a disk to disk copy.  All seemed to go well, but when the backup hdd was installed I got the follwoing messages:

"Grub loading
Grub error"

I ran a Ubuntu 11.10 live CD and ran "Boot-repair"

This again ran without any errors and after rebooting, I got the normal grub menu with the following options:

"Linux Mint 11
Linux Mint 11 recovery mode
Memtest
Memtest
Windows Vista/7 recovery
Windows Vista/7 boot Loader
Ubuntu 11.10"

I can boot into Win7 and Linux Mint 11 but not into Ubuntu.

When I select Ubuntu, I get the normal Ubuntu (purple) splash screen with the logo centered and the row of dots below which show the normal progression from red to white through three changes.  At that point my hdd shows some activity and then stops
at a black screen.  No further activity.  Any thoughts anyone.

---

### Post by olympic on 2012-01-19
:D  SOLVED

For some reason Clonezilla picked up an early version of the kernel for Ubuntu 11.10.

The version which I am using is "3.0.0-13-generic-pae"

Clonezilla picked up "3.0.0-12" without the -pae ending.

I reran Clonezilla and this time it picked up both versions plus the recovery modes.

---

