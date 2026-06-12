---
title: "Error when trying to install Ubuntu with thumb drive alongside Win10"
date: 2017-10-11
forum: Installation &amp; Upgrades
---

### Post by jabberwookiee1974 on 2017-10-11
Hi. I made a thumbdrive for Ubuntu 17.04 with Universal USB Installer (v. 1.9.7.9) for a dual boot with Win 10. I try to boot with it (after disabling Secure Boot and Fast Boot) and I keep getting this error:

> (intramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I should note that all this worked before. I used the same ISO file as before and had a successful dual-boot system. Earlier today I tried to do a dist-upgrade to 17.10 and it didn't work. So I figured I'd start again. I deleted my linux partition in Windows Disk Management (successfully) and tried to remove the Ubuntu boot option from my BIOS (unsuccessfully). I've tried so many things and am at my wits end.

Can anyone offer some advice?
Thanks.

---

### Post by ubfan1 on 2017-10-11
I'd still run a hashcheck (md5sums,...) on the ISO, but then run the media-check option on the USB menu instead of the install.

---

### Post by jabberwookiee1974 on 2017-10-11
Hi. Thank you for responding.

I did do the hashcheck with winMD5sum. And I did try the media check option on the usb boot menu. Still received the above error.

All this worked the first time I did this in September. Makes it really frustrating. Don't know what's different this time around :)

---

### Post by ubfan1 on 2017-10-12
Take a look at [https://ubuntuforums.org/showthread.php?t=2300910](https://ubuntuforums.org/showthread.php?t=2300910)

---

### Post by jabberwookiee1974 on 2017-10-12
Back again.

I tried a different app, UNetbootin, to make my live usb drive. Everything is fine now. Turns out I had to specifically erase and format my thumbdrive for FAT32 beforehand ... even though it was already formatted correctly (shrugs).

Many thanks.

---

