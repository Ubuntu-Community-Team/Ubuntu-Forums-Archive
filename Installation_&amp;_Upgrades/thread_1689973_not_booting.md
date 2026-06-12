---
title: "not booting"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by Taexali on 2011-02-17
I'm going to be building a new PC so have downloaded ubuntu in preparation for the new PC.  I have tried to boot the CD on my laptop and get the following message:

BusyBox V1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


Does anyone have any advice on what I need to do?

Regards

Taex.

---

### Post by sikander3786 on 2011-02-17
Welcome to the forums :-)

Run an MD5SUM test on the downloaded image and make sure it is not corrupt.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, burn a new disc and this time, at the lowest possible speed. I burn at 4x.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Or if your Bios supports, you can use a USB drive.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html?showComment=1297175951702#c3100135703895167905](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html?showComment=1297175951702#c3100135703895167905)

The error you quoted above, most probably appears due to a bad burn.

---

### Post by Taexali on 2011-02-17
Thanks sikander3786

The ISO file was corrupt.  Downloaded again, burnt a new CD and all is well in the world of ubuntu!!!!

Taex.

---

