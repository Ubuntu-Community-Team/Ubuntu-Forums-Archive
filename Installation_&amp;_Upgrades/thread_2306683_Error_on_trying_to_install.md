---
title: "Error on trying to install"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by DaedalusOS on 2015-12-17
So, I've spent about the past hour trying to get Ubuntu to install. (I'm pretty new to Ubuntu, main experience is with SSH on my server I used to own, so sorry if I'm a noob at this)

I've created both a USB and a DVD in order to attempt to get this installed, to no avail. I boot to the USB and whether I click "Try Ubuntu without installing" or "Install Ubuntu" I still get the same error.

Error I'm getting:

[https://screencloud.net/v/vlFy](https://screencloud.net/v/vlFy) (Sorry for potato quality)

Super long error reads:

[      31.959742] ata8: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B0B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch }

I've tried 3 different programs for the USB:
Universal USB Installer
Win32DiskImager
LinuxLive USB Creator

And for the DVD I just burned it to the disk by right clicking the ISO.

Any ideas guys? Ubuntu has always intrigued me so I want to dual boot with Windows.

---

### Post by deepakdeshp on 2015-12-17
Please check the correct download of the image by checking against md5 checksum
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

There is excellent installation guide on the ubuntu site

---

### Post by kansasnoob on 2015-12-18
If that's Wily (15.10) it may be this bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147)

I personally found Wily to be too buggy to even consider using it on a production machine so I'm still using 14.04 (Trusty).

---

