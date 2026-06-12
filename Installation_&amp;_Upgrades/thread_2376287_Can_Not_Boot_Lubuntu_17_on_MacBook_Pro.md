---
title: "Can Not Boot Lubuntu 17 on MacBook Pro"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by tomihasa on 2017-11-01
I have tried installing Lubuntu 17 to a USB hard drive (8 GB, FAT32) using a Windows 10 computer with Rufus. I only see GRUB when booting with MacBook Pro.

Then I tried to install Lubuntu to the same USB hard drive with MacBook Pro using commands:

```
sudo diskutil unmountDisk /dev/disk2
sudo diskutil unmountDisk /dev/disk2s1
sudo dd if=$HOME/lubuntu-17.04-desktop-amd64.iso of=/dev/disk2 bs=1m conv=sync
```

The results are the same: I only see the GRUB, but launching Lubuntu does not work.

Information about my MacBook Pro: MacBook Pro Early 2011, processor 2.0 GHz Intel Core i7, first video card AMD Radeon HD 6490M 256 MB GDDR5, second video card Intel HD Graphics 3000 384 MB DDR3 SDRAM, screen resolution 1440 x 900, memory 4 GB, and hard drive 500 GB 5400 rpm Serial ATA.

Any suggestions?

---

