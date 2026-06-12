---
title: "Unable to install with wireless keyboard and mouse"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by jasonabullard on 2015-11-15
Hello all.  Having some issues getting Ubuntu 15.10 Server 64-bit installed on my Intel NUC D3217IYE with a Logitech wireless keyboard and mouse.  I have done some research and noticed earlier versions of Ubuntu not having support for the Logitech Unifying Receiver but also noticed on LaunchPad that a patch was put in place

[SIZE=2]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/975198
[/SIZE]
I am using UEFI boot (Secure Boot disabled) and have ensured that legacy USB support is enabled.  The problem arises as soon as I am taken to the language selection screen the keyboard/mouse quit responding.  Just to ensure that there was not any problems with ports or devices I was able to install Debian 8.2 (netinst) using the same UEFI setup with no issues.

Anyone have ideas that might help me get this working?

---

### Post by tgalati4 on 2015-11-15
Use a powered USB hub.  It's possible the NUC doesn't have enough power to run the receiver.  You were able to install Debian (net install) because it wasn't using graphics which takes power away from the USB port.  Or, find a wired keyboard and mouse.  What power supply are you using with the NUC?

---

### Post by jasonabullard on 2015-11-15
I actually did use a powered usb hub last night while attempting various configurations.  I just found it weird that Debian saw the keyboard/mouse and not Ubuntu.  Normally, in my experience it has always been the other way around.  I ended up purchasing a wired keyboard just to install.  However, once Ubuntu Server was installed there were no issues with the wireless keyboard/mouse.  Seems to me that something is not being loaded for the server install iso.

I am going to mark this as solved since I was able to eventually install Ubuntu Server with a wired keyboard but I don't think that should be the ultimate solution.

---

