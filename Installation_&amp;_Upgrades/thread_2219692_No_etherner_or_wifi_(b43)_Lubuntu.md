---
title: "No etherner or wifi (b43?) Lubuntu"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by ferge-kolferol on 2014-04-25
Dear Ubuntu Forum users,

Yesterday I would have liked to change my previous working Lubuntu 13.10 for the new 14.04. I had a few problems, which were:


I tried to install the 14.04 with Wubi, the Windows part was okay, the installation was also without any error message, but at the first reboot it started to give me this error message, and the booting process stopped every time.


*"b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found*
*b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found" ...*


I removed the Wubi installation, and after he new partitioning, I installed from the live CD without any error also.
While booting, I got the same error message, but the Lubuntu started this time, but I didn't have any internet connection, neither ethernet, neither wifi.


I tried to install a few packages, like firmware-b43-installer, bcmwl-kernel-source, b43-fwcutter, but none of them worked. I read a few topics about this problem, and most users with this problem do have a working ethernet connection (by the way the Windows internet connection works).


And, the strange thing, I tried to reinstall the previously fully functional 13.10, and I got the same error message, without any internet.


What should I do? Try to blacklist b43? But I don't know, without ethernet it may not be my solution. I don't want to give up on Lubuntu :)

Csabi from Hungary

---

### Post by Rex Bouwense on 2014-04-25
Try looking here.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
Broadcom Wi-Fi drivers sometimes require a little more attention.

---

### Post by ferge-kolferol on 2014-05-07
I managed to install *bcwml-kernel-source* and all the dependencie (I downloaded them from another computer), and beside that, the *b43-fwcutter* also. The computer stopped giving the error message during the booting, but still, nothing happens if I plug my ethernet cable and my wireless still unseen. Which commands should I run in Terminal to have more help? Thank you.

---

