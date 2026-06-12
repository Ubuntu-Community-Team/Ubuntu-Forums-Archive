---
title: "Corrupted Packages inside /var/cache/apt/archives ?"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Mr_VeRiTy on 2010-05-17
Hi, sometimes when installing a package that I un-installed a while ago, it installs it from /var/cache/apt/archives but whenever it does that it always fails, and says something about "short read buffer [location]" if i download the package manually at packages.ubuntu.com then install it, it works fine, is this because the packages in /var/cache/apt/archives are corrupted, and if so how do I clear them?




Thanks.

---

### Post by davidgutu on 2010-09-26
someone please help. i'd like to know too.

thanks:KS

---

### Post by plucky on 2010-09-27
> **davidgutu said:**
> someone please help. i'd like to know too.

thanks:KS

From a terminal (Applications > Accessories > Terminal) ```
sudo apt-get clean
``` will clear out the .deb files from /var/cache/apt/archives.

Read ```
man apt-get
``` in the terminal window to find out what apt-get does.

Good Luck

---

### Post by Mr_VeRiTy on 2010-10-07
> **davidgutu said:**
> someone please help. i'd like to know too.

thanks:KS
@davidgutu
Since I first made this thread I've already figured out what was causing the corruption, it turns out that my hard drive had lots of bad sectors, and they were spreading, so if I were you i'd check your smart status by going to System>administration>disk utility, and locating your hard drive, as bad sectors can cause your whole hard drive to go corrupt.

---

