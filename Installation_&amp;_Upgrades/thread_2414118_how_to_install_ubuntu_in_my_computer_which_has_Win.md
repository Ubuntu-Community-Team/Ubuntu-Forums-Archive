---
title: "how to install ubuntu in my computer which has Windows 10 as OS?"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by tangara on 2019-03-06
I have downloaded Ubuntu Desktop version 18.0.42 but I am surprised that I can't install it, even after reading the instruction.

What I want to achieve ?

I have partitioned Windows 10 and now I want to install Ubuntu in this new partitioned space.
However, I do not know the drive for the new partitioned space.

After installation, I hope to log in using Ubuntu straight away and hopefully I will be able to use the command line to call out my App like Eclipse IDE, doing customization using linux which alot claim wonderful to use.

Please direct me a easy to understand tutorial on how to achieve the above.

Tks.

---

### Post by jdeca57 on 2019-03-06
Look at [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0]("https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0") to find some easy pointer how to install. In short: create a DVD / usb, boot from it, and install. I hope this helps.

---

### Post by mastablasta on 2019-03-06
> **tangara said:**
> I have downloaded Ubuntu Desktop version 18.0.42 but I am surprised that I can't install it, even after reading the instruction.



it would be good to know what you have done so far and also is the windows 10 install using secure boot? is it an UEFI system or older BIOS? is the "fastboot" function enabled?

---

### Post by yancek on 2019-03-06
The instructions and information at the Ubuntu site below should help.  What 'instructions' did you use?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-03-06
Windows historically has confused the definition of "drive". A d: drive in Window can be a second partition on one drive or a second physical drive.

In Linux there are partitions & drives. A drive is sda, sdb, etc and partitions are numbered within a drive like sda1, sda2 etc.

When installing you will create a new partition in unallocated space. The existing Windows partitions will already be sda1, sda2 etc for all existing partitions.
More info & many links in link in my signature for UEFI install, but yancek's link is one of the most important.

---

