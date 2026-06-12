---
title: "Lubuntu can’t see PATA SSD during installation"
date: 2018-03-04
forum: Installation &amp; Upgrades
---

### Post by mukesh11 on 2018-03-04
Lubuntu can not see hard drive of an old laptop
I am trying to install Lubuntu Version 16.10 (32 bit) on an ancient laptop Compaq Presario V2000 
but not being successful.It has regular BIOS and not UEFI. The laptop specs are:

************************************************** **************************
Compaq Presario V2000
Processor: AMD Turion 64 ML-34 (Lancaster, AMD Turion 64 Mobile Technology ML-34)

Memory: 2 chips of 1GB each of DDR 300 (PC2700) SODIMM, Single Channel

Hard Drive: PATA (115GB SSD)
************************************************** **************************

The laptop originally had a PATA hard drive which was replaced with the following PATA/SSD to increase speed.

[http://www.ebay.com/itm/2-5-PATA-IDE...AAAOSwu4BVmP~y](http://www.ebay.com/itm/2-5-PATA-IDE...AAAOSwu4BVmP~y)

The laptop has Windows 7 (32bit) installed and it runs fine. I want to make it dual boot and install Lubnutu. The BIOS sees the hard drive, but when I put Lubuntu install disk it gives error.

The error I am getting is:

ata1: SRST failed (errno=-16)

This probably points to the fact that Lubuntu can't see my hard drive. I tried all combinations of the 4-pin jumper settings of SSD but it didn't help. I tried running the following command from live Lubuntu DVD:

dmesg | grep sd

The command doesn't show sda or sdb either. FYI, this laptop has only one hard drive.

I can install Linux on USB stick when using the laptop but it refuses to install on hard drive.

Please post if you can help me install Lubuntu on this laptop.

---

### Post by wildmanne39 on 2018-03-04
Hello and welcome to the forum! lubuntu 16.10 is no longer supported so you will not receive any updates, I recommend installing 16.04 then if you want you can upgrade directly to 18.04 when it comes out at the end of April.

---

