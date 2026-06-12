---
title: "UEFI vs. Linux"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by chrosome on 2013-02-07
Hey guys,
I'm quite knew to the world of Linux and want to start using it along side windows, but unfortunattely UEFI is thwarting my plans. I will spare you with all the details of my history of suffering, but I can say that I spent around a day of my life with trying to fix the issue and did not success. I've been looking through many posts and threads on numerous websites, but none of these could fix the probleme and I haven't found a thread by someone sharing the exact problem I have. Sooo.. here's the issue:

Whenver I try to install a Linux distribution(doesn't matter which beause they all don't work: ubuntu, fedora, suse, mint, elemnatary, gparted, partedmagic) my hard drive is not to be detected. It won't appear in the 'choosing directory dialogue' at the very beginning of the installation, neither can I find it using the terminal. I tried numerous commands I found from 'fdisk' over 'gdisk' to I don't know...

Even after intensive research I have no clue how to fix this problem and I'm gonna do everything you guys think I should. All I know is that this is a conflictt between UEFI and Linux. Unfortunately there is no error message I could give you. I wasn't sure which information will be required, so just request the information you need.

---

### Post by darkod on 2013-02-07
Check whether you are running any raid or Intel SRT technology.

---

### Post by The Spectre on 2013-02-07
My Computer has UEFI and I have had no problem with installing and running Linux Mint 13 or Ubuntu 12.10. 

The Motherboard in my Computer is a GIGABYTE GA-Z77MX-D3H.
[http://www.gigabyte.com/products/product-page.aspx?pid=4145&dl=](http://www.gigabyte.com/products/product-page.aspx?pid=4145&dl=)

The problem that you are having might not have any thing to do with UEFI at all and it might have something to do with the new Microsoft Secure Boot.

---

### Post by bfmetcalf on 2013-02-07
Also, on my desktop I had to enable booting from sata 3 devices.  When installing I had the HDD not showing up and finding that option and enabling it allowed me to see and use the HDD.

Edit:  That was an ASRock P67 EXTREME4 GEN3 LGA 1155 Intel P67 SATA 6Gb/s USB 3.0 ATX Intel Motherboard

---

