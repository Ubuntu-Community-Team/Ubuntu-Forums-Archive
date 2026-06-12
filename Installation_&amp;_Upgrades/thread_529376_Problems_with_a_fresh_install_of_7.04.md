---
title: "Problems with a fresh install of 7.04"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by revlucio on 2007-08-19
Hi all,

After getting sick of Vista I'm trying to jump to linux. I'm not completly new to it, having run Ubuntu 6.06 on a laptop and I've done a bit of programming on Red Hat at university.

However, trying to get K/Ubuntu 7.04 running on my desktop has been a nightmare. After a bit of difficulty with installation, it boots up, but I'm having some problems. The two major ones are:

1) The updater freezes while downloading packages. This occurs in both Unbuntu and Kubuntu. I'll go to update, and somewhere through the updating process the desktop will freeze. Mouse, keyboard, it all stops responding. I end up rebooting just to get it working.

2) Internet connectivity drops out. Whenever I start up my internet connection is fine, but it can drop out randomly. Other windows computers on the network are unaffected, so it may be a setting in Ubuntu somewhere. I don't think this is the cause of problem 1 either, as sometimes the net cuts out while downloading packages, and they just stop downloading, it doesn't freeze.

The freezing problem has happened a few other times as well. I'm not sure what to do, after having re-installed both versions of Ubuntu about 3 times and searching around these forums and google for the past few hours.

I hope someone can give me a hand.

---

### Post by s0me0ne on 2007-08-19
Probably a bug, I've been trying to get Xubuntu, Ubuntu to install and it just doesnt like some older computers, make sure your BIOS is as up to date as you can get it

[https://bugs.launchpad.net/ubuntu/+source/pkgsel/+bug/104713](https://bugs.launchpad.net/ubuntu/+source/pkgsel/+bug/104713)
[https://bugs.launchpad.net/ubuntu/+bug/110400](https://bugs.launchpad.net/ubuntu/+bug/110400)

Do a search through the bugs, I gave up on *buntu

---

### Post by Gremlinzzz on 2007-08-19
After a bit of difficulty with installation could be the problem but i think im no expert that the kernel feisty is using is a bit buggy. i bye past the update kernel and installed  2.6.22-9-generic.
my computer works allot better with this kernel.If ya want to give it a try at your own risk.
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by revlucio on 2007-08-19
After poking around the forums it seems a lot of people were having freezing problems when using Core 2 Duo processors, and it has something to do with SMP. Upgrading kernel is what I'd like to try next, and if that doesn't work then disabling SMP in the kernel.

The problem is Ubuntu freezes within 10-15 minutes of booting, which in this case was halfway through downloading the new kernel. _Is there a way I can download the kernel using a Windows XP machine (what I'm on) and copying it over with a USB drive and installing it then?_

The other option I suppose would be to install it via the command line. _How do I boot without turning on the GUI? Or can I easily turn off the GUI once I'm in the OS?_

Also, for those who are interested here are my hardware specs:

**Processor:** Intel Core 2 Duo E6400
**Motherboard:** Gigabyte P965-DS3P
**RAM:** 2GB Kingmax 667Mhz
**Video Card:** Gigabyte Nvidia GeForce 7950GT 512MB
**HDD: **120GB Seagate SATA
**DVD Drive:** Some generic brand, IDE

---

