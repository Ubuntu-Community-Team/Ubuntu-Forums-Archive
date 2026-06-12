---
title: "Why are modules bundled in the restricted-modules package"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by whitebrianc on 2006-05-26
I've recently purchased an Alienware Area 51 7700 laptop.  We run Debian on all of our other boxes but it couldn't see the disk controller at boot.  Sort of a problem.  Anyway, I found Ubuntu and it loaded like a champ and I'm very happy with the OS.

My problem is that this box is running an Nvidia chipset and the Atheros chipset for wireless meaning all I should have to do is load the restricted-modules package for my kdernel and be good to go.  Unfortunately, it looks like I need a newer version of the madwifi driver.  The other complication is that the video card is the Nvidia go7800gt which doesn't seem to work correctly with the latest drivers from Nvidia.  There is a How-to about loading the new driver after installing the restricted-modules but that doesn't seem to work for me after reboot.  What I'd really like is the ability to only uninstall the madwifi module.

Is there a good reason why these 5 modules are bundled together?  Is it possible they could be broken apart?  If someone wants more detail concerning my problem just let me know.

Thanks.

---

### Post by az on 2006-05-26
[QUOTE=whitebrianc]
Is there a good reason why these 5 modules are bundled together?  Is it possible they could be broken apart?  [/QUOTE]

They are not free-libre open-source software.  Everything else that you get on the install cd is.  They are packages like that to be easily removed if you object to that kind of software.

The manufacturers of those bits of hardware don't care about your rights to run software that is your own property on your computer.  If they cooperated properly with the FLOSS community, you wouldn't have to fart around to get their stuff working.

---

### Post by Sutekh on 2006-05-26
[quote=whitebrianc] Is there a good reason why these 5 modules are bundled together?[/quote]Azz speaks true on this.  Plus it must be easier for Ubuntu to bundle them together than offer, 5 different restricted-module packages.

[quote=whitebrianc]Is it possible they could be broken apart?[/quote] They could be installed separately as their own kernel modules, rather than downloading them all together in the restricted-modules package.

For example the NVIDIA drivers from NVIDIA's website, don't need the restricted-modules package just the kernel headers.  Their installer creates a kernel module and inserts it into the kernel.


Try this thread to help you install the drivers (method 2)

[Ubuntu Forums - Latest NVIDIA Drivers]("http://ubuntuforums.org/showthread.php?t=75074")


This link might help you with determining support for your particular card

[Ubuntu Wiki - Supported Wireless Network Cards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")

And this link for installing the wifi module separately (without restricted-modules)

[Ubuntu Wiki - MadWifi]("https://wiki.ubuntu.com/WifiDocs/Driver/Madwifi")

---

