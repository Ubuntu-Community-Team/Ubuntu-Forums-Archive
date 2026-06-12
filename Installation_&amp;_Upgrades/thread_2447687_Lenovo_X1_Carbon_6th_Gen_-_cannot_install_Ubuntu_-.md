---
title: "Lenovo X1 Carbon 6th Gen - cannot install Ubuntu - nvme / ext4-fs problems?"
date: 2020-07-23
forum: Installation &amp; Upgrades
---

### Post by jaydublu2 on 2020-07-23
I've been trying several days to install Ubuntu on my X1 with a Liteon CA3-8D512 SSD, which has been happily running Windows 10, but I've gone as far as I can with WSL and virtualisation - I really need to transition to full Linux.


I have tried Ubuntu 20.04, Ubuntu 18.04 and Linux Mint 20 booting from freshly downloaded ISOs on USB - all hit the problem at the same point after repartitioning the drive and trying to format partition 2.


Example of the various messages that come up if you open the installer detail pane:


```
nvme nvme0: I/O QID 1 timeout, reset controller
nvme nvme0: Abort status: 0x371
```

... then after some time ...

```
EXT4-fs error (device nvme0n1p2): __ext4_find_entry:1531: inode #2: comm mkdir: reading directory lblock 0
```



I deleted the partitions, reinstalled Windows, used the Lenovo System Update tool to update BIOS to latest (1.49), updated SSD NVMe Firmware, tried with secure boot on and off in the BIOS, and various other suggestions from various posts found online.


I tried contacting Lenovo support but they're saying it's OS as Windows is working, and there have been no suggestions on the Lenovo forum.


Any thoughts or suggestions would be greatly appreciated.

---

### Post by jaydublu2 on 2020-07-30
Turns out it was the SSD - I took a chance and bought a Samsung 970 EVO Plus and swapped out the Liteon that came from Lenovo - Ubuntu 20.04 install worked as expected.

---

### Post by kurt18947 on 2020-07-30
> **jaydublu2 said:**
> Turns out it was the SSD - I took a chance and bought a Samsung 970 EVO Plus and swapped out the Liteon that came from Lenovo - Ubuntu 20.04 install worked as expected.

I'm glad you were able to get Ubuntu installed. I'm curious as to why the Liteon wouldn't cooperate with the Ubuntu installer. Some sort of custom firmware that Lenovo installed on the Liteon drive? I've installed various Ubuntu varieties on SSD both brand name and no-name, SATA III and NVMe.  No issues with either type.

---

### Post by ander-san on 2020-11-12
Hi, I have a Thinkpad M720q with a LITEON CA3-8D256 with the same problem, so I believe is not a speficic problem with only one SSD, i think all SSD NVME's from Liteon (CA3 Series) has this problem.
Workarround: Install Ubuntu in a VM with almost same size of the SSD, create an image with Clonezilla and them restore the image into SSD. Works, but if you later use parted, growpart, resize2fs, gparted, gnome-disk and etc to shrink or expand the partition, you'll have problems.
Edit: I do have done all firmware updates (BIOS and SSD)

---

### Post by ander-san on 2020-11-13
I Had success using xfs as File System instead ext4. May be a good alternative.

---

