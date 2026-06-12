---
title: "Kernel Panic with dmraid and samba"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by 8baal on 2007-09-04
I have pieced together leftover parts to make a Frankenstein computer to install Ubuntu server and play with it in my home.  As far as I can tell, I'm running the latest BIOS updates for all the hardware, which have been listed to fix microcode problems on the motherboard and even enable SATARAID5 support on my add-in Sil3114 card, which I'm pretty sure is about as useful as a piece of garbage.

Anyways, after becoming more educated on exactly HOW these cheap, horrible "raid" cards work, I've discovered a few how-tos to install dmraid, partition, and mkfs, and also throw it into my fstab.  I'm booting from a single IDE hard drive, with intention to use the cheap "raid" card simply to store files on a samba share.  I have had no problems sharing the mountpoint with samba so that my Windows machine can see it.

All above working wonderfully, no mount problems, no filesystem errors, no trouble whatsoever.

My Kernel Panic came in originally under 6.10 when xcopying a HUGE pile of files from a Win2k server to the samba share, so I decided to change my sources.list to feisty and do a dist-upgrade.  Again, worked fine, however kept getting the Kernel Panic AGAIN only when force-feeding the computer HUGE amounts of data from my M$ server.  I'm basically trying to dump my data off the M$ server to get rid of it.  This data is coming in over gigabit lan from one static host to another, and usually after 40-60 gb of data transfer, the kernel panics.  This is still true from a FRESH install of 7.04.

Ubuntu 7.04, apt-get ALL updates, installed LAMP, DNS, samba, ssh, dmraid, Webmin 1.360.
P4 1.8ghz, ASUS P4BGL-VM, 768mb RAM, 160mb IDE drive, Sil3114 add-in "SATARAID" card with 2x 250gb SATA drives in mirror using dmraid, Realtek 8169 gigabit lan card.

I'm new to the linux thing after being on a Mac for the last few years watching OS X prosper.  Required to be a Windows tech at my job.

---

