---
title: "GRUB Error 2"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Menyus on 2008-11-01
I installed Ubuntu server (LAMP) v8.10 from CD/ISO image, which worked fine. However, after booting from hard drive, I get 

GRUB Loading stage 1.5.

GRUB Loading, please wait ...
Error 2

At this point the system hangs. I tried rebooting a couple of times with the same result. My system is an eight year old home-built PC, midtower case with 350W PS, ASUS P3B-F MoBo, Intel Pentium 3 450MHz CPU, 1GB RAM, PNY GeForce FX5500 DDR 128MB video card, a couple of IDE drives, CD/DVD drives, floppy drive and 10/100TX Ethernet card. This same exact system ran without any problem under Ubuntu  server (LAMP) v7.10. 

Any help or suggestion will be appreciated.

---

### Post by caljohnsmith on 2008-11-01
Since you have a new install of Intrepid server, I think it is highly likely that your Grub error 2 could be due to a problem with your HDD configuration in BIOS; this is exactly what has happened to some people in the past with Grub error 2 when the issue was not due to simply a faulty Grub configuration. Look for HDD settings in your BIOS related to auto-detect, LBA, CHS, RAID, AHCI vs. IDE, ACPI, DMA, etc, try changing them one by one, reboot, and see if Grub then boots. I would also recommend writing down the original setting of anything you change in BIOS so you can always revert back to your original settings. 

But we should probably also check to make sure you don't have any other obvious problem causing the Grub error 2. Do you have a Live CD? If so, please boot it, open a terminal (applications > accessories > terminal), and post:
```
sudo fdisk -lu

```
And we can work from there. :)

---

