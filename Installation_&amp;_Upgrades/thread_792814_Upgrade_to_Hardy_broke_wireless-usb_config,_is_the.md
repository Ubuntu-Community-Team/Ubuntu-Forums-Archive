---
title: "Upgrade to Hardy broke wireless-usb config, is there a cure?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by terry-s on 2008-05-13
[upgrade to Hardy broke wireless-usb config, is there a cure?]

The original install was Gutsy/7 from CD. Getting the wireless USB internet connection working was painful: it involved using a temporary hardwired internet link (no longer available), and a whole lot besides. Software updates have worked well since then. 

But the most recent update confronted me with an invitation to upgrade to Hardy/8, and I agreed to do that. There was no warning that the hardware configuration might get broken by the upgrade, but that's what has happened. The wlan0 device no longer exists.

Is there a route to fix this? If it involves installing any fresh packages, is there a howto for downloading these on to a non-ubuntu machine and then installing them from CD on to the upgraded ubuntu machine which no longer has an internet connection?

Thanks in advance//terry

---

### Post by dstew on 2008-05-13
You will probably have to do the same things you did to get it working in Gutsy. Probably, you installed software by hand that is not available in the standard Hardy system. Check the Hardware Drivers window in System --> Administration first. If you don't find a driver for your wireless card, you will have to do whatever it was you did before.

If you don't have an internet connection, and you want to download Debian packages from the Ubuntu repositories, you can use the [nonetdebs service]("http://nonetdebs.homeip.net/"). You upload to them a text file of your system status, and they give you a bunch of links to the packages you need to install. You copy the packages to a CD, then put them on your no-internet computer and install them using dpkg.

---

