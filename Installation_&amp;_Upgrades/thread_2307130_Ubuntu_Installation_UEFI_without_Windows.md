---
title: "Ubuntu Installation UEFI without Windows"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by javiernisa on 2015-12-22
I'm going to buy a Dell 17 "Inspiron 17 5000 Series (Intel (R)) - 5759 will remove Windows but I have a big doubt that however much the review forum does not work out.


Obviously it comes with UEFI, and I will remove windows because not used it for years. How is to be installed ubuntu to work with UEFI installation and beyond?


Please, I think many of us have this doubt and it would not hurt to create a fixed post with this.


Thank you.

---

### Post by Oliver_Mead on 2015-12-22
On a UEFI BIOS you should be able to boot an Ubuntu Live USB or CD (I did have some trouble on my HP Pavilion laptop but it was still possible) without much hassle, if you remove Windows first then Ubuntu will be the only thing the computer can boot from and if you don't remove it first (removing it during installation) you should be able to do so by following some of [these]("http://www.penguintutor.com/news/hardware/ubuntu-windows8-dellinspiron") steps - of course omitting the parts about shrinking the Windows partition as Windows is going to be removed anyway. You can also chose the "Erase disk and install Ubuntu" option during installation to get rid of Windows for you.
Hope this helped

---

### Post by kc1di on 2015-12-22
I had no problems installing ubuntu on my uefi laptop without windows.  it installed and created the correct uefi boot. works great.

---

### Post by sudodus on 2015-12-22
Installing without Windows is much easier than installing a dual boot system with Windows and linux. Without Windows you can install both in UEFI mode and BIOS mode (also called CSM or legacy mode). Both should work, but if you want UEFI mode you must use the 64-bit versions of Ubuntu or an Ubuntu flavour.

Maybe it helps to look at the following links and links from them about UEFI.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

There is a good wiki page about [booting with UEFI](https://help.ubuntu.com/community/UEFI), and a good tutorial thread, [UEFI Installing - Tips](http://ubuntuforums.org/showthread.php?t=2147295).

---

### Post by oldfred on 2015-12-22
Is that with the older Haswell based or newer Skylake based Intel chips.

I bought a Dell SFF with Haswell & it just worked. But those newer systems with Skylake need newer kernels & Intel's support software. 

Make a backup of Windows as we have many users who totally erase Windows then find one application that only works or works well with Windows. I had that happen as I only run (ran) Ubuntu. But I shrank Windows to 40GB and installed Ubuntu. But to run Comcast to get HD video I could only run Windows. And all the Windows updates filled my 40GB, so I had to expand it back again.

       Xeon Skylake Users May Run Into Display Problems With Current Distributions Dec 2015
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)
Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

