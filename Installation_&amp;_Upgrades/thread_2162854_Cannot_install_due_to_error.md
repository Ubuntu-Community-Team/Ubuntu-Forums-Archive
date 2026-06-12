---
title: "Cannot install due to error"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by grman401 on 2013-07-16
im trying to install ubuntu 10.04 on my gateway 6020GZ and i get the following code 

b43/ucode5.fw not found...i have no clue what is going on here!

---

### Post by claracc on 2013-07-16
Here, [http://ubuntuforums.org/showthread.php?t=1966655](http://ubuntuforums.org/showthread.php?t=1966655), there is a thread explaining the same problem and giving various approaches to solve the problem.

I recommend you to install an ubuntu supported release as 12.04, 12.10 or 13.04, since ubuntu 10.04 has reached its end of life support and you are not going to receive any security update, also you are going to find difficult to install any software.

---

### Post by grman401 on 2013-07-16
i only have the 10.04 disc and cannot boot from usb on this laptop

---

### Post by claracc on 2013-07-16
I provided you with the link in order you see is a known problem and that there are various workarounds you can try. It doesn't matter if you try to install from usb or from CD. 

Read carefully all the thread, it points you to launchpad page, where the bug is reported: [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/909871](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/909871)

As the problem seem to be to install the b43 driver, this link: [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)  (also referenced in the one provided) can help you, also, see the related ubuntu documentation: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

---

### Post by Bucky Ball on 2013-07-16
Forget 10.04 LTS. It is dead. Your only hope is the server edition which has five years support, until 2015, but I really don't see the point. Download the 12.04 LTS ISO and make an install disk/USB. Supported for five years, til 2017.

---

