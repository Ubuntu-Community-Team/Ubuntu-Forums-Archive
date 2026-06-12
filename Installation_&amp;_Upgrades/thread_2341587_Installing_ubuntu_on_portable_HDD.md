---
title: "Installing ubuntu on portable HDD"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by avagantamo on 2016-10-29
I have a 1TB WD hard drive with 2 partitions, and I want to install Ubuntu on one. Im a beginner, so I have no idea how to install properly. An additional piece of information I can provide is that I was trying to run Kali linux on this system but it would not boot (from a pen drive) but I inserted the drive in another pc and it worked fine. The BIOS is set to both auto legacy/UEFI, but my Windows runs only on legacy. How can I install Ubuntu on a partition and make it work properly?

Note: Rufus does not support partitioned HDD's

---

### Post by yancek on 2016-10-29
How did you create the two partitions?  Generally, if you have windows installed you are better off shrinking the windows partition to make room for Ubuntu by leaving unallocated space.  You need to format the partition for Ubuntu druing the install because windows can't do that.

As a beginner, it isn't a good idea to use something like Kali Linux.  It is designed specifically for computer forensics only and you need a lot of experience to be able to use it.  It is a poor choice for a Desktop operating system and they even state that on their home page.

Also, if you want to have Ubuntu installed to use on multiple computers, you will need to install it's bootloader to the MBR of the external drive.

If you actually are using windows in Legacy, the tutorial at the link below is very detailed.  Make sure you do not boot or install Ubuntu EFI.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

