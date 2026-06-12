---
title: "Dual Encrypted Installation of 12.04 Fails on"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by shkkmo on 2012-08-15
I'm trying to do a secure Dual install with Windows 7 on a Gateway running the A8 APU from AMD.

I'm running the install off a live usb I created with from the ubuntu-12.04-alternate-amd64 image.

I can create all my partitions just fine (a 500mb ext4 logical for /boot, a 200GB logical partition that is AES encrypted and contains an LVM group containing a logical 8GB swap partition and a logical ext4 partition for the main installation)

The installation proceeds through the core setup and everything fine until it gets the 'Select and Install Software' step. It seems to load aptitude fine, and then fails.

I noticed a couple of similar bug reports from back in June, but I thought they had been fixed.

I've tried formating, re-partitioning, and re-installing a couple of times. I've also remade the live usb as well as tried to recover the installation. This last had the most success as I was actually able to get into aptitude and select packages. Things seemed to install correctly, but upon rebooting the installation would not lode

I'm still rather new to Linux, this is my second installation (I installed 10.04 a couple years ago and used it as my daily for a while) I'm not really sure where to go from here to troubleshoot.

Should I download a daily and try that? Should I try manually installing the packages (I think this might be over my head.) Are there any other options besides the alternate install for created a secure encrypted system that dual boots? Am I simply doing it wrong?

Thanks

---

