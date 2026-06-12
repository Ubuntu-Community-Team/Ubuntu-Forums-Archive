---
title: "Kernel Upgrade is 52 MB in size - is this Correct?"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-06-02
Does this seem right to anyone - kernel image v3.13.0-87 .... 51.9 MB ?!?!?
That seems like an awful big file. Here is what Tech Desc. shows;

------------------------------
Changes for linux-image-3.13.0-87-lowlatency versions:
Installed version: None
Available version: 3.13.0-87.133
Version 3.13.0-87.133: 
  [ Kamal Mostafa ]
  * Release Tracking Bug
    - LP: #1585315
  [ Upstream Kernel Changes ]
  * Revert "usb: hub: do not clear BOS field during reset device"
    - LP: #1582864
--------------------------------

Installed version - NONE???  This doesn't seem right or logical ! !  I am running v3.13.0-86.
I thought kernels have been upgraded v4+ I see in some posts.
Can anyone verify for me this is correct ?!?!?

---

### Post by Impavidus on 2016-06-02
50MB is about right for a kernel upgrade. Usually there are multiple packages to be upgraded simultaneously when you get a kernel upgrade. 3.13 is one of the kernels available for Ubuntu 14.04. Those running Ubuntu 16.04 are on kernel 4.4. You typically stay with one kernel version the entire life of your Ubuntu release, although you get upgrades for bugs and security patches.

Currently you have not installed a version of linux-image-3.13.0-87-lowlatency. You've installed a version of linux-image-3.13.0-86-lowlatency, which is a different package. In contrast to most other upgrades, most kernel upgrades come in the form of a new package. This is done so that the old version is not automatically removed, to keep that as a backup to keep the computer bootable in case the new kernel doesn't work.

---

### Post by Rick St. George on 2016-06-02
Thanks for clearing that up "impavidus". I will allow the upgrade.
Case Closed!

---

