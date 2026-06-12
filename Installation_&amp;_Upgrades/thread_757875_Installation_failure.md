---
title: "Installation failure"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by dxtremeb on 2008-04-17
I have an installation failure when trying to install Debain 4.0. I know this is about ubuntu, but I figure that since it's based off Debian I'd post it here (much better community here anyway).

Okay, I get an installation failure when it's setting up the packages and whatnot. I looked in the syslog, and found this (it's the last line before DHCP renewals start):


```
Apr 16 13:07:58 in-target: Setting up gnome-cups-manager (0.31-3) ...
Apr 16 13:07:58 in-target: 
Apr 16 13:07:58 in-target: Setting up alacarte (0.8-5) ...
Apr 16 13:07:58 in-target: 
Apr 16 13:07:58 in-target: Setting up deskbar-applet (2.14.2-4.2) ...
Apr 16 13:08:00 in-target: 
Apr 16 13:08:00 in-target: Setting up gnome-btdownload (0.0.25-1) ...
Apr 16 13:08:00 in-target: 
Apr 16 13:08:01 in-target: tasksel: aptitude failed (255)
Apr 16 13:08:02 main-menu[1144]: WARNING **: Configuring 'pkgsel' failed with error code 1 
Apr 16 13:08:02 main-menu[1144]: WARNING **: Menu item 'pkgsel' failed. 
Apr 16 13:11:26 dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Apr 16 13:11:26 dhclient: DHCPACK from 192.168.1.1
Apr 16 13:11:26 dhclient: bound to 192.168.1.203 -- renewal in 300 seconds.
Apr 16 13:16:26 dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Apr 16 13:16:26 dhclient: DHCPACK from 192.168.1.1
Apr 16 13:16:26 dhclient: bound to 192.168.1.203 -- renewal in 300 seconds.
```


It's the warnings that I'm worried about. After that, it's just DHCP requests until today when I was able to get back to the computer and 'finish' installation (school computer, can't stay all day).

What can I do to fic this? By the way, this is a Dell Optiplex GX150 with the install options acpi=force

I can supply entire log if need be.

---

### Post by dstew on 2008-04-17
My guess is that your internet connection failed when apt was installing the package tasksel. It probably installed it fine after you reconnected. If your system works, no worries.

---

### Post by dxtremeb on 2008-04-17
> **dstew said:**
> My guess is that your internet connection failed when apt was installing the package tasksel. It probably installed it fine after you reconnected. If your system works, no worries.

Doubt it. I've tried it three times (third time is the only time I saved the log, though) with the same results. I dunno if it would have worked though, since I've aborted after every failure and didn't go any further; I can't see how it could have worked, seeing as it doesn't seem to have installed any other packages after tasksel, leaving a crippled system.

I guess I could install it without the network mirror, and then update it once it installs; i'll have to try that tomorrow. But any more recommendations or solutions are most welcome! =)

---

