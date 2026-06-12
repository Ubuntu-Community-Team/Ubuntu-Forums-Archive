---
title: "ATI driver causing boot problems"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by sirthomas711 on 2010-11-03
okay, so, I'll try to be as detailed as possible.  I just recently installed Kubuntu 10.04 LTS on my Sony Vaio E series.  It's the 64-bit version.  no problems aside from the fact that the mouse tracker doesn't work, and the fact that I'm a kind of a noob.  I just installed the proprietary ATI driver for the HD Radeon 4200 and when I went to restart it loaded the Kubuntu load screen(not the splash screen) for a brief second and then the screen just goes black and does nothing.  any ideas?  I can run recover mode but I'm not familiar enough with unix/linux OS's to run it and recover it from a command line format.  any ideas?

---

### Post by coffeecat on 2010-11-04
The open source ati driver works better than the proprietary driver for that card. In fact the open source driver in 10.04 should give you enough 3d acceleration for compiz. It works very well on my Acer laptop with the Mobility Radeon HD4200. I presume yours is the mobility version seeing as it's a laptop.

Anyway, the best (only) option is to uninstall the proprietary driver. I can't 100% guarantee the following will work because it's some time since I did this (since I made the same mistake with 9.10/Karmic), but give this a try.

Boot into the recovery mode. Choose 'drop to root shell' with or without networking. Networking will only work with an ethernet cable attached and you shouldn't need internet for this. When you get the # prompt you have full root powers, so double-check everything you type in. A single typo has the potential for disaster. To uninstall the fglrx proprietary driver and misc gubbins, do:

```
apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```Let that complete. You now have to disable the xorg.conf configuration file created when  the proprietary driver was installed. One way is simply to rename it:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Check you've got case correct - Linux is case-sensitive unlike Windows. X11 = CAPITAL-X, eleven.

Now:

```
reboot
```And see if you get a GUI this time. You don't have to reinstall the open source ATI driver because it won't have been uninstalled. Or, it shouldn't have been. If you get any problems, post back.

---

