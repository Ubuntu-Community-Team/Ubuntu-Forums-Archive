---
title: "MBR problems"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by sIgnwaVe on 2008-11-15
Hello, I am new to Linux, & am having problems installing Ubuntu on my pc. I have been reading all about setting up grub in the MBR of the 1st hdd, while install Ubuntu on another hdd. I am trying to install this OS on 1 single SATA 160GB hdd. I have reinstalled many times trying different  places such as (hdd0) & also /dev/sda the only 2 choices it gives me. Both ways show that the OS installs fine, but on reboot it tells me that no boot device or Grub install. Can someone help this windows dummy, I have been told that Linux is the way to go.  P.S. I am trying to install 8.10 x-86. Thank You.

---

### Post by Gausian on 2008-11-15
Are trying to install Ubuntu as a single OS on 1 HDD?  If so all you need to do is to choose to format and install ubuntu on the entire drive.

---

### Post by cdtech on 2008-11-15
Just to offer some helpfull information, be sure to burn a copy of the Live CD. You will use this when you run into problems booting or anything to do with your primary drive.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by caljohnsmith on 2008-11-15
> **sIgnwaVe said:**
> Hello, I am new to Linux, & am having problems installing Ubuntu on my pc. I have been reading all about setting up grub in the MBR of the 1st hdd, while install Ubuntu on another hdd. I am trying to install this OS on 1 single SATA 160GB hdd. I have reinstalled many times trying different  places such as (hdd0) & also /dev/sda the only 2 choices it gives me. Both ways show that the OS installs fine, but on reboot it tells me that no boot device or Grub install. Can someone help this windows dummy, I have been told that Linux is the way to go.  P.S. I am trying to install 8.10 x-86. Thank You.
So do you only have one HDD, or are you want to install Ubuntu to an external drive? From your Live CD, how about opening a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
I think I know what your problem is, but the above output will confirm it or not. We can work from there if you want. :)

---

