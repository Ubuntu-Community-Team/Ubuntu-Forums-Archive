---
title: "Install to USB Drive or Separate Partition"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by prcm311 on 2011-07-25
So here's the deal.  I am looking at building a small home server for a friend.  The system will be used as network storage for two laptops (i.e. shared drive).  With the possibility of also streaming music and videos.  I would like opinions between the two following options (I understand two hard drives would be ideal):

1: Install OS to a hard wired USB drive
2: Install OS to a separate partition on the hard drive

In the case of option 1 "hard wired" means "installed internally".  I haven't decided exactly how I would like to build it.  I most likely will solder on a lead to the USB drive, connect it to one of the two sets of USB pins, and secure it to the case somehow (duct tape).

The build is planned as follows:
- Foxconn SFF R30-D4 Intel Atom D525 (1.8GHz, Dual-core) Intel NM10 Intel GMA 3150 Barebone
- Kingston ValueRAM 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Dual Channel Kit Desktop Memory Model KVR667D2N5K2/2G
- SAMSUNG Spinpoint F3 HD103SJ 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive
- Patriot Xporter XT Boost 8GB Flash Drive (USB 2.0 Portable) Model PEF8GUSB

I am curious if anyone has tried this.  I myself have installed Ubuntu from USB drives, although I have never installed *to* a USB drive or attempted to configure a BIOS to boot, by default, from a USB drive.  So that's all new territory for me and any help is appreciated.

---

### Post by oldfred on 2011-07-25
If BIOS lets you boot USB drive then it may be possible, not sure, but you still could install grub2's boot loader to the internal drive and boot from USB or partition. We only suggest installing grub2's boot loader to external since it usually is removeable. I boot from any of sda, sdb or sdc and most of my installs are on sdc.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Understand that USB port is a lot slower than SATA or even PATA port. So response may be better if installed to a partition.

Are you thinking of installing to flash USB drive??

---

### Post by prcm311 on 2011-07-25
Yes, I was thinking of installing Ubuntu to a USB Flash Drive.  The idea, and I could be mistaken, was that it would be cheaper than a second hard drive and provide better performance than installing to a second partition on the hard drive.

---

### Post by oldfred on 2011-07-25
Flash is slower than a hard drive and USB port is slower also. I have an full install in a 16GB flash drive and it is functional, but by no means speedy.

Partitions on hard drive would be much better if you can do that. If it is a smaller server why not two hard drives?

---

