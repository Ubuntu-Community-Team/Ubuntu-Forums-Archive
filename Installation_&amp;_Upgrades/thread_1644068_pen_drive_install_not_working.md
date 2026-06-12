---
title: "pen drive install not working"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by voxangelus on 2010-12-12
Hi everybody. 

I followed the instructions to boot from USB to install the netbook remix, used the USB installer program listed on the Ubuntu netbook download page, followed all those directions. 

When I set my netbook (Acer Aspire One AOA 150 running H2Bios) to boot from USB, I get a screen that has one line of text reading SYSLINUX... (don't recall exactly, it looks like credits) and then a blinking cursor. 

Obviously it's acknowledging and trying to boot from the USB stick, but it doesn't continue to install or anything. I left it alone for an hour or so, and the cursor was still there, blinking. (o how it mocks me)

Any suggestions?

---

### Post by C.S.Cameron on 2010-12-12
Check the MD5SUM of your downloaded iso.
A small download error can make it not work.
If OK
Try installing to USB using UNetbootin.

---

### Post by voxangelus on 2010-12-12
Sorry, I am a total noob. 

What exactly am I looking for in the MD5SUM?

---

### Post by oldfred on 2010-12-13
The md5sum verifies that you have downloaded it correctly.
[https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/burning-cds.html](https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/burning-cds.html)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

There are a couple of issues depending on how you installed it.
syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by voxangelus on 2010-12-13
Using UNetbootin worked great - using Ubuntu now and couldn't be happier with it. Thanks for the help!

---

