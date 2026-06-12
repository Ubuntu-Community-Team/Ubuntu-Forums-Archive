---
title: "Can't access Ubuntu on Ubuntu 18.04/Windows dual boot"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by Kkatt on 2020-09-18
I am running Ubuntu 18.04 / Windows 10 dual boot on ThinkPad L570. The configuration has been working without problems for some years. I don't know what I may have done to break the bootloader, but after turning on the computer, Windows starts normally and I can't see any options to start Ubuntu. I tried running boot-repair from Ubuntu live CD. Here is the output:

[http://paste.ubuntu.com/p/VTWcYx9vPd/](http://paste.ubuntu.com/p/VTWcYx9vPd/)

It says I need to create ESP partition but when I start GParted I can see the partition is already there (the screenshot is attached). 

Any help will be greatly appreciated.

---

### Post by oldfred on 2020-09-18
> The boot of your PC is in Secure mode.

Did Windows update turn UEFI Secure boot on and probably Windows fast start up back on which prevents the Linux NTFS driver from correctly seeing your NTFS partitions.
If ESP still not correctly seen, it may need dosfsck from Linux or chkdsk from Windows.
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1
or:
sudo dosfsck -t -a -w /dev/nvme0n1p1
The -a seems to help in clearing dirty bit

You also have grub installed to MBR and PBR - partition boot sector of p5. You almost never install grub to a partition and since UEFI never install grub to MBR for BIOS boot. As long as you never try to boot in BIOS/Legacy mode, having grub in MBR will not matter. 

You should be able to boot Ubuntu from UEFI boot menu. Which with Lenovo may be     Lenovo - F8, F10, F12, depending on model.

---

### Post by Kkatt on 2020-09-18
Thank you so much oldfred. Disabling secure boot did it. Since I really struggled to disable it, here are the instructions that helped in case someone should have the same problem: [https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/](https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/)

---

### Post by CelticWarrior on 2020-09-18
How much of a struggle was it?
 From the screenshots I can tell it's one of the simplest firmwares I've ever seen. The Secure Boot setting is called exactly that and it's located in the most logical menu (Security).

---

