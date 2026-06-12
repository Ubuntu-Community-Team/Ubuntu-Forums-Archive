---
title: "USB mouse not working after switching from Unity desktop to Xubuntu desktop"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by oldrunner55 on 2015-01-04
I just switched desktop systems because of slow performance on an older system. I have an HP220 desktop system with a Pentium 4 processor, 2GB ram, 160Gb HDD, and Nvidia graphics card. The installed version is Ubuntu 14.04 LTS with the Unity desktop environment. Everything worked fine before but the system was slow so I changed to the Xubuntu desktop environment because it is leaner for older systems. Now my USB wired mouse will not work and yes, my USB ports are working as I can plug in a flash drive and the system sees it just fine. Also I've noticed that Google Chrome no longer works. For some reason the only mouse that will work, is an older PS/2 mouse which was detected EVEN THOUGH THERE WAS NOT ONE PLUGGED IN !!! I have searched many forums and help websites with no luck. Everything I can find on modifying the config files is much older and doesn't apply to 14.04. HELP !

---

### Post by ibjsb4 on 2015-01-06
This is an odd problem that your having and I do not have any answer for it.

You were able to run Unity without this problem.  Unity is based on gnome3 and I wonder if you would be better off staying in the gnome environment.  Maybe worth a test drive:

[http://www.webupd8.org/2014/11/ubuntu-mate-1404-lts-available-for.html](http://www.webupd8.org/2014/11/ubuntu-mate-1404-lts-available-for.html)

---

### Post by MAFoElffen on 2015-01-07
There are two places that will should hints to this.

Please post your /var/log/Xorg.0.log

Input mouse was chaged a few years ago from xorg drivers to udev (PnP) HID sense. The xorg log should show what device it saw on it's start. 

If there was a problem before XServer, then the hints would be in the USB init tree recorded in the /var/log/syslog... Please post the results of 
```

dmesg | grep -i usb

```

---

