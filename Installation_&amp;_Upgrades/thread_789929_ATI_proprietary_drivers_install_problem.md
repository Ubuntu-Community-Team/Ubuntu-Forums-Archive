---
title: "ATI proprietary drivers install problem"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by mboisson on 2008-05-11
Hello,
I have a Gigabyte GA-MA78GM-S2H motherboard with the 780G chipset and the HD 3200 ATI IGP. I installed the server amd64 version of hardy and apt-got ubuntu-desktop.

I also installed MythTV, and now, I wanted to get my PC to work with HDMI on my TV. I plug it and there is an image. However, I can't get it in the proper resolution (only basic resolutions like 800x600, 1024x768, etc. are available). So, I figure I don't have the right drivers.

After looking around for instructions, I get to this how-to :
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The first option they mention is "go in the Restricted Drivers Manager" and enable the "ATI accelerated graphics driver". Problem #1 : I don't have anything like "Restricted Drivers Manager" in System > Administration. The closest thing to this is "Hardware Driver", but it does not contain the ATI driver.

The second option is Method 1. I execute this command :
mboisson@HTPC:~$ sudo apt-get install restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.3.3-0ubuntu8
You should explicitly select one to install.
E: Package restricted-manager has no installation candidate

They say that this command may not be required, so I continue, everything goes fine until after rebooting, I type
fglrxinfo

and get this : Error: unable to open display (null)

Moreover, the login screen in HDMI looks fine, it is widescreen and is pretty. However, when I log in, I see the desktop background for a few seconds and everything goes white. X doesn't seems to load properly.


I also tried Method 2, but I can't get to compile the drivers.

---

