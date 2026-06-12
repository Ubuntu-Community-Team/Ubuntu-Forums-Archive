---
title: "How to Remove Windows dual boot and Install Only Ubuntu"
date: 2014-12-25
forum: Installation &amp; Upgrades
---

### Post by vincej on 2014-12-25
H - I have been running a dual boot Ubuntu 14 with Windows 7. I want to remove the Dual boot loader so at boot time my system boots directly into Ubuntu. I intend to install an SSD and install Ubuntu on that. This means that the current HDD will be used for data only.  Then I will install virtualbox and install Win7 on that allowing me to access Win7 off the VM on Ubuntu . 

I am looking for some advice on the best way of achieving this. Specifically I need some advice on the best way to reinstall Ubuntu so I do not have the Boot loader. 

 My thinking was to do the following: 

- remove and store all useful data from the windows and ubuntu HDD partitions. 
- install the SSD
- reinstall Ubuntu on the SSD.
- Once it is installed I will reformat the HDD 

I'm not sure that this process will eliminate all dual boot loaders. 

Any suggestions ?? 

Many thanks !

---

### Post by Bucky Ball on 2014-12-25
Install the SSD. Boot from Ubuntu install media. Try Ubuntu and get to a desktop. Launch Gparted and wipe the HDD (create new partitions at the same time if you like). Install Ubuntu to the SSD. That should do it. 

Make sure you install grub to sda (which should be the SSD, if it's not, remove the HDD and that way the SSD definitely will be sda).

---

### Post by Impavidus on 2014-12-25
You'll always have a boot loader, but if there is no Windows on the system when you install Ubuntu, the boot loader menu will be skipped be default, making the boot loader invisible. You can always change that later.

---

