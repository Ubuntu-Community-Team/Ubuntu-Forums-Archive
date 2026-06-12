---
title: "Default install of 9.10 and the USB drive version of 9.10 behave differently?"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by DavidGeer1 on 2009-12-25
I have a machine which I have installed the 9.10 Netbook remix directly from the CD and I have also run the OS from a USB pen drive based on the installation instructions here: [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

What I find odd is I used the same ISO for both installs but it yielded very different results.

For the CD install:
1) Ethernet card not detected (lspci & lshw & isconfig didn't show the hardware)
2) I tried the install on another box and it did detect the ethernet card however, I had to manually edit the network/interfaces file to get things working
3) I could not get it to auto detect my nVidia card

Powered off and booted from USB key:
1) Ethernet card detected
2) Network automatically configured and DHCP worked on first boot.  No need to edit /network/interfaces
3) On the opening screen it asked me if I wanted to download nVidia drivers

Why are there such big differences between the two methods even though they come from the same ISO?  Are the changes to the USB key version documented somewhere?  If so, this would be helpful to find out what configuration changes were made in  order to get the CD install to work properly.

Thanks!

---

