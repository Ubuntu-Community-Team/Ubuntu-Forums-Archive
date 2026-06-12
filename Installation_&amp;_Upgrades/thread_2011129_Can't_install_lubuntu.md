---
title: "Can't install lubuntu"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by Oli999 on 2012-06-26
Hi there. I'm trying to install lubuntu onto my laptop. Have created a usb drive using universal usb installer. When plugged in to the laptop as soon as it is switched on it immediately freezes. 

black screen with message at the top.
SYSLINUX 4.06 EDD 4.06-pre1 Copyright (c) 1994-2011 H. Peter Anvin et al

I was thinking about installing an earlier version than 12.4 then 
upgrading to get around this but can't find anywhere to download 
a 64-bit file from.

Please can anyone advise on what to do here.

---

### Post by marinara on 2012-06-26
does booting from cd work?

---

### Post by Oli999 on 2012-06-29
> **marinara said:**
> does booting from cd work?

My laptop hasn't got a cd drive so can't try that.

---

### Post by Rex Bouwense on 2012-06-29
There could be many reasons why your flash drive will not install.  First, your download could be corrupt.  Did you check the md5sum of the download?
Second, it is possible that when you burned the image to the flash drive, you did not get a good burn.  Third, it is possible that you have a bad flash drive.  If you have another handy (1 Gb or larger) try using it.

---

### Post by Oli999 on 2012-06-29
How do I do a MD5sum check?

---

### Post by MG&amp;TL on 2012-06-29
[https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

:)

Although it's interesting that it doesn't get past the bootloader.

---

### Post by wis5.2 on 2012-06-29
me 2 have problem installing lubuntu. i burn cd from lubuntu.net 2 time to make sure put cd in machine then press start then press f6 got boot from hard or cd choose cd then machine after a walde eject the cd. machine is a p3 running at 700 with 258 mhk

---

### Post by southerngeek on 2012-06-29
> **Oli999 said:**
> Hi there. I'm trying to install lubuntu onto my laptop. Have created a usb drive using universal usb installer. When plugged in to the laptop as soon as it is switched on it immediately freezes. 

black screen with message at the top.
SYSLINUX 4.06 EDD 4.06-pre1 Copyright (c) 1994-2011 H. Peter Anvin et al

I had some issues with the recommended USB image writer program, I wound up using the LinuxLive usb creator instead. you might want to give that a whirl.

> I was thinking about installing an earlier version than 12.4 then 
upgrading to get around this but can't find anywhere to download 
a 64-bit file from.

 Also, you can pick up other versions and iso's from [http://releases.ubuntu.com/](http://releases.ubuntu.com/), if you still want to try that route.

---

### Post by ImperialHwy on 2012-06-29
I have exactly the same problem as reported in the first post here. I rebooted my laptop with the USB stick inserted and "Boot from USB" selected in my BIOS. When the computer boots it prints out "[COLOR=royalblue]SYSLINUX 4.06 EDD 4.06-pre1 Copyright (c) 1994-2011 H. Peter Anvin et al[/COLOR]" and goes no further. I did an MD5sum check on the iso download and that was valid. I also did a chkdsk on the USB flash drive and it came out clean. I am using a Gateway laptop running 64 bit W7. I built the USB image from "[COLOR=royalblue]ubuntu-12.04-desktop-i386.iso[/COLOR]"
 
Any other ideas would be greatly appreciated.  Thanx.

---

### Post by sudodus on 2012-06-29
Make sure your USB drive has a partition with good FAT32 file system. Set the boot and lba flags.

Then try Unetbootin (there are versions for linux as well as Windows). I have good experiences making boot USB drives with Unetbootin.

But there are other methods too. See the following links

[[COLOR="Red"]_https://help.ubuntu.com/community/Installation/FromUSBStick/_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick/")

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

[[COLOR="red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

---

### Post by sudodus on 2012-06-29
Sometimes there are hardware problems (or should I say cooperation between some hardware and the operating system). Then you can try some boot options, for example ***nomodeset***. See this link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

