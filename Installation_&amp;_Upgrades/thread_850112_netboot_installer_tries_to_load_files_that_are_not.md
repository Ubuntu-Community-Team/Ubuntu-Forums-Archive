---
title: "netboot installer tries to load files that are not on CD"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by silicium on 2008-07-05
I am trying to install ubuntu-studio 8.04 on a diskless PC without internet access.
The ubuntustudio-8.04-alternate-i386.iso was extracted into a HTTP server's root directory. This Windows PC also has DHCP and TFTP servers.
Netboot and beginning of installation are OK. I tell the installer the local IP address of the Windows PC instead of an internet mirror.
Then it tries to download the following files (found with Wireshark) from wrong root directory that I can't change (dists is in / and /dists/hardy-* are not on DVD)
/ubuntu/dists/hardy-security/Release
/dists/hardy-updates/main/binary-i386/Packages.bz2
/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2
/dists/hardy-updates/main/binary-i386/Packages.gz
/dists/hardy-updates/restricted/binary-i386/Packages.gz

Then successful downloads
/dists/hardy/main/binary-i386/Packages.gz
/dists/hardy/restricted/binary-i386/Packages.gz

Last, it freezes on the screen saying something like "updating list of available packages..."

I have tried other ways of installation without success:
1) I removed the DVD drive from another PC, but the ata driver in the installation kernel has a bug with beeing locked to UDMA33 only, and does not even accept the useful parameter cdrom-detect/cdrom_hdparm=-d0 (same error message after trying hdparm in alt-F2 console)
Hey kernel driver writers, not everyone has a cheap recent motherboard with UDMA100 and over, I am using a server motherboard with 64-bit PCI and RAID5 controller, the cheapest IDE controller was chosen for installing software from CD/DVD only !
2) I connected the target PC to the DSL router after netbooting, but downloading everything is very slow, then there were similar errors of failed base system installation.

Should I give up, and copy my previous version of ubuntu-studio to the new disk then perform an upgrade ?

---

