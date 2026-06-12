---
title: "Very slow install on core2 quad, msi p6n sli platinum"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by pixel34 on 2007-06-13
My install process is taking more than 6 hours on my machines, and has not finished. This does not seem right.

I am trying to install either xubuntu, ubuntu, or debian on 6 brand new machines:

processor: intel core2 quad
motherboard: MSI P6N Platinum
4 gigs ram
2 250g WD harddrives
biostar geforce 6200 video card 128 ram

I have tried the ubuntu and xubuntu text install from disk, and by extracting the files to the hard drive (used another computer to put the files on the hard drive) then set up grub to boot the disk.

I have tried turning off USB, firewire, onboard lan, onboard audio. I have tried with another videocard from a machine that I have running kubuntu.

I can not figure out why it is taking so extremely long to install the file system.

one method:
Partition HD into three parts. Install mbr and grub on 1st. Copy over the initrd.gz and vmlinuz, set it to boot the image on the second partition. When it gets to the install dialog it is moving very fast. However It fails to find the iso. I go to command line and do the following,
mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0
OK. now I can find the iso. However in the next step it tries to find the packages on the CD drive. It fails to find the drive. I can not continue.

another method:
boot from CD. takes 3 hours to install first set of packages. I can't wait three days for the second set to install.

What might I need to do to increase the speed of this install? Machines this fast should be able to install in 30 minutes. Has anyone else used this MB? Is this chipset a problem?

---

### Post by pixel34 on 2007-06-13
I should have mentioned I am trying to install the amd-64 version of feisty fawn 7.04

---

### Post by pixel34 on 2007-06-14
I tried the 32 bit version and the installation flew! This may be some kernel problem with the quad core 2?

---

### Post by xpavement on 2007-06-14
What's your BIOS? I know updated BIOS's have better performance than others with 4gb with that mobo.

---

### Post by pixel34 on 2007-06-15
> **xpavement said:**
> What's your BIOS? I know updated BIOS's have better performance than others with 4gb with that mobo.

How am I able to update the bios? I thought the only tool for doing that was windows based? The bios version I have shipped with it. I think it is 2.61. I will double check and post if that is not right.

---

### Post by xpavement on 2007-06-15
You might want to check out this thread on the MSI forums:

[http://forum.msi.com.tw/index.php?topic=106608.0](http://forum.msi.com.tw/index.php?topic=106608.0)

I have the same mobo with a quad core, but it is running windows. I did update my BIOS before I upgraded to 4gb and there are no slow downs. I think BIOS 1.22 or higher will help (1.34 is the lastest beta I think) , and I loaded mine manually by booting from a USB key. (The Plat BIOS's are numbered 1.x, while the non plat are numbered 2.x)

---

### Post by pixel34 on 2007-06-18
I did install new bios and this solved my problem. It was certainly the issue.

Thanks!

---

