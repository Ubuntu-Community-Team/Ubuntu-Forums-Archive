---
title: "ubuntu 8.04 &amp;vista bus sp1 dual boot"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by cdx on 2008-08-18
I recently bought a new PB Technologies desktop pc running vista business sp1 on a gigabyte EP45-DS3R motherboard with an intel quadcore Q6600, 4gb ram, a seagate barracuda 500gb SATA HD,pioneer DVR-115DBK DVD writer and a geforce 9600GT graphics card, 32bit.I would like to try linux and thought I would load ubuntu as a dual boot before loading the system with sfuff I don't want to loose.

I started with a 6.10 cd which brought up an installation menu but appeared to not have a graphics driver. I then downloaded and burnt 7.10, 8.04 desktop,& 8.04 server but they wouldn't bring up a menu. Being an ignorant novice and inept is painful. I then tried the alternate cd. I think they were all the 32bit versions. None would let me bring up an os off the cd although several were tried on an older mechine running xp and brought up an os.

The alternate cd wouldn't show any partitions so I went back into vista and ran chkdsk and defrag. The alternate cd could then see the NTFS partition but seemed not to be able to read it and wouldn't downsize it. Back to vista I found a shrink option which reduced  the NTFS partition leaving free space. The alternate cd then put in new partitions for root home and swap. The rest of the installation seemed to go smoothly but when I restarted ubuntu wouldn't come up showing a BusyBox note then 

(initramfs)

Vista will only start after I first run it in safe mode. Running ubuntu recovery mode ended the same as before. The notes displayed included:

[53.332754} scsi 0:0:0:0: CD-ROM     PIONEER DVD-RW DVR-115D 1.13 PQ: ) ANSI: 5
[53.338613] Driver 'sr' needs updating - please use bus_type methods

and

Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev 
ALERT! /dev/disk/by-uuid/14da92f2-7c76-49d0-8f69-1c227ea1dbeb does not exist. Dropping to a shell!

If any of this makes any sense to anyone I would love to find out what to do next?

---

### Post by cdx on 2008-08-31
I have now started from the begining again and burnt a new desktop cd at 1x which brought up a desktop. After manually requesting a generic ide drive I was able to load an operating system. However the install was not able to bring up the the network. I will try to attach a screen shot of my hardware network report. Vista which runs the network fine shows the network card as a Realtek RTL8168C(P)/811CP not a 8168B as in ubuntu. 

I have downloaded a linux driver for a C card uncompressed the iso and copied it to a floppy. However the ubuntu system is not forthcoming about what to do with it now. There doesn't appear to be a setup file with the driver and I wonder if I need to clear eth0? or unmount things before playing around further.

Any help would be appreciated.

---

### Post by cdx on 2008-08-31
trying again-

---

