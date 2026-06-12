---
title: "GRUB difficulties after convoluted installations and several noobish mistakes"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by Fuzzo on 2010-07-16
Hi everyone,

I'm currently in the middle of trying to convert my external hard drive from a normal Ubuntu 10.04 LTS installation to a Live USB installation. However, I'm having some problems with GRUB. I first installed Ubuntu 10.04 from CD onto my hard drive (which was NTFS-formatted.) Then I realized that I could only boot Ubuntu from this computer, making the externalness of the hard drive pointless. So I used Startup Disk Creator from the live CD to FAT32-format the hard disk and install Ubuntu 10.04 LTS, with a 4GB casper-rw file. I then realized that this left most of the terabyte useless for persistence, so I deleted the casper-rw file and used gparted to create an ext2-formatted partition, labeled casper-rw.

The only problem now is that when I boot without the CD (regardless of my external hard drive), I get a GRUB error.

> no such device: 565970nf-fde8-41d5-a273-51faff9393dr
grub rescue>What should I do so I can take my external hard drive with me and boot from USB anywhere, while it's still possible to boot Windows without the external hard drive in? Right now all I know how to/can do is boot from live CD. Thanks!

---

