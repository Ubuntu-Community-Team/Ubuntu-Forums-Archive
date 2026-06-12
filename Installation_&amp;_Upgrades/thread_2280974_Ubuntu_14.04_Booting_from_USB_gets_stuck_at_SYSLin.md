---
title: "Ubuntu 14.04 Booting from USB gets stuck at SYSLinux line"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by eMshsWE on 2015-06-03
Hello,

I have a HP Pavillion dm4 1050 Laptop initially dual booted with Windows 7 and Fedora 14, but the OS has crashed. So I am trying to run Ubuntu on it to try and back up the data.

I downloaded Ubuntu 14.04 and burnt the ISO to a Transcend 4 GB Pendrive using UnetBootin. Now when I select the option to boot it shows this message and gets stuck :

SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H.Peter Anvin et al.


and does nt move beyond this stage .. :(

I tried this USB on another Dell Vostro Laptop and it works perfectly fine there. 

I am stuck with a computer that has no OS and I need to recover my data, Could someone please help me out? ?

---

### Post by Innuend0 on 2015-06-05
Hi,

I don't know if it can help but I had a similar problem with one of my laptop. I tried to install Ubuntu 14.04 and 14.04.2 but it stayed stuck.

Some colleagues advised me to try with the 14.04.1 (downloaded using p2p). I didn't really believe that it would fix the problem but tried anyway. Worked at first try.

Apparently there are problems with some drivers.

Don't know if it can apply to your case but can be worth a try.

---

### Post by yancek on 2015-06-05
Did you do an md5 checksum on the downloaded iso file prior to using unetbootin.  Might be a bad download.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by oldfred on 2015-06-05
These are now all older errors that I thought they fixed.

 syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
[http://ubuntuforums.org/showthread.php?t=2078599](http://ubuntuforums.org/showthread.php?t=2078599)
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

