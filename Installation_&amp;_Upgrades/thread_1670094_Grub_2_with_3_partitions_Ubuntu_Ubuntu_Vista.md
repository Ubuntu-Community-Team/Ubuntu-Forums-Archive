---
title: "Grub 2 with 3 partitions Ubuntu Ubuntu Vista"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by mr_sausage on 2011-01-18
Hello.
Please help.

I am up the creek a bit.

I was using Ubuntu 10.10 on an old PC with an old ASUS K8u-x motherboard, a sempron CPU and a couple of GB RAM.

Everything was working OK. However, due to audio driver problems and  because I needed to use a couple of applications in Vista, I decided to  install VIsta as well.

However, I had some problems with installing VIsta off an original  WIndows DVD-Rom using an external DVD drive and an internal DVD drive.

I think this is probably due to the PC being based around an old motherboard which has probably seen better days.

I also tried installing off a USB Flash Drive. I looked into the BIOS  and adjusted the settings, however, I still had some problems.

So, I took the Hard Drive and plugged it into a different Motherboard.
which allowed me to install VIsta and an additional Ubuntu installation  on the hard drive using 3 separate Partitions on the same Hard Drive.

All 3 partitions working well. Ubuntu / Ubuntu / Vista - all working well, booting from Grub 2 and from EasyBCD from Vista.

I then brought the hard drive back and installed the hard drive back into its original home, the K8ux and Sempron.

Now, when I boot up, the PC does enter into Grub2 and gives me the usual choice of:

Ubuntu
Ubuntu recovery
Memtest86+
Memtest86+ diagnostic
Vista

Now, if I choose to boot into Ubuntu. It boots into the last clean installation of Ubuntu and works fine.
If I boot into Vista, it then boots up another Bootloader, offering me two options, Vista or Ubuntu.

Now, if I choose Vista. I am then given the option of the various Vista boots, i.e. Safe Mode, last known config etc.
Now, if I choose any of the options, the PC starts to boot but then just  restarts and goes back to the BIOS / POST etc. And then back to the  original Grub2 Boot Menu.

The same happens if I choose the alternative Ubuntu (original) installation, it also just reboots.

Now, I have been trying to figure out how to fix the bootloader so that I  can simply choose one of the 3 installations installed on the 3  separate partitions on the single drive.

I know this is possible by making adjustments in GRUB 2, however, I am pretty new to Linux / Ubuntu and am not used to coding.

Please can some one help.
Cheers
:razz:

---

