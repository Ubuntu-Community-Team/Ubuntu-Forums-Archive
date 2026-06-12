---
title: "Unity3d crash after updating system"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by dahakka on 2012-04-27
Hello to everyone.

Yesterday i have installed new great system ubuntu 12.04, but I have encountered errors. I install system, install some other programs and customize user interface and then restart system. Everything goes fine till now. Then i check if there is some other updates avalible to me. After scanning for new updates system found some updates and also there was kernel update to version 3.2.0-24-generc. I did update all updates and then restart system. But after this updating system i can't run anymore unity3d :( I am certaing, that my computer can run unity 3d, but for some reason it fails. Well unity run, but not in 3d mode. I don't like unity 2d, and I would like to install unity 3d.

I did some tests and one from them were this: /usr/lib/nux/unity_support_test -p and this shows me this message: 

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

I will be very happy if someone could help me solve this problem. I did already customize ubuntu and would not like to uninstall or reinstall it again.

Thanks in advance!

---

### Post by GnuSense on 2012-04-30
I've read that the shipping Nvidia driver is not compatible with Unity 3D & Gnome in some hardware.  I'd just be patient and use 2D or some other desktop and wait a couple of weeks, I suspect a new driver will ship.

---

