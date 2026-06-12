---
title: "Ubuntu 12.10 Installation RAID (ICH10) Issues"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by phate408 on 2012-12-11
Hi, so after recently getting into the Steam for Linux beta, I decided I would finally dual-boot my desktop. I've been using Ubuntu/Debian for some time on my laptop, but previous attempts to switch over to Linux on my desktop have been thwarted by the lack of default support for my RAID 5 array. My current hard drive set up is as follows:

ICH10
 - 4 drive RAID 5 array (Data only)
 - Single drive (Windows)
 - Single drive (Intended Linux target)
Marvell 91xx controller
 - Optical drive

Excitingly, there is now support for Intel software raid by default in all the distributions I tried (Ubuntu 12.10, LM14, LMDE, Fedora 17 [All 64-bit]), and they all recognized and could access my RAID volume, but no longer seem to be able to recognize and utilize the individual drives. The installer did not present my Windows drive or the drive I intend to use for Linux as options, but instead only presented the RAID volume and the flash drive I was booting off of. I would greatly appreciate any suggestions anyone may have towards a solution to installing Ubuntu.

Update: Darkod's suggestion below about removing residual metadata did the trick. I suspect it was from when I had the drives on the Marvell controller.

---

### Post by darkod on 2012-12-11
If the disk has been used in raid before, it has meta data remains. The installer ignores disks with meta data thinking they are part of raid.

To remove meta data, you can do from live mode:
sudo dmraid -Er /dev/sdX

MAKE SURE YOU GET THE DISK RIGHT!!! If you use it on one of the raided disks, it will drop that disk from the array.

If there is meta data, it will ask you for confirmation to remove it, after that the installer should work fine.

---

### Post by ronparent on 2012-12-11
Are you proceeding directly to the install? Does the situation exist if you run the 'live cd'.

---

### Post by phate408 on 2012-12-11
> **darkod said:**
> If the disk has been used in raid before, it has meta data remains. The installer ignores disks with meta data thinking they are part of raid.

To remove meta data, you can do from live mode:
sudo dmraid -Er /dev/sdX

MAKE SURE YOU GET THE DISK RIGHT!!! If you use it on one of the raided disks, it will drop that disk from the array.

If there is meta data, it will ask you for confirmation to remove it, after that the installer should work fine.

I will try this and reply with the results.

[QUOTE=ronparent]Are you proceeding directly to the install? Does the situation exist if you run the 'live cd'.[/QUOTE]

I was running the installer from the live instance.

---

### Post by phate408 on 2012-12-11
> **darkod said:**
> If the disk has been used in raid before, it has meta data remains. The installer ignores disks with meta data thinking they are part of raid.

To remove meta data, you can do from live mode:
sudo dmraid -Er /dev/sdX

MAKE SURE YOU GET THE DISK RIGHT!!! If you use it on one of the raided disks, it will drop that disk from the array.

If there is meta data, it will ask you for confirmation to remove it, after that the installer should work fine.

That was it. Perfect. Thank you very much! :)

---

