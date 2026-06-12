---
title: "[SOLVED] Trouble installing Virtualbox"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by jimmysheldon on 2008-09-03
a few weeks ago i installed virtualbox-ose and, with a bit of trouble, got a virtual windows xp machine running. the drivers to plug my phone into a computer don't work with ubuntu, so i installed them on my virtual windows machine and when i came to plug my phone in, via usb, nothing happened and the computer just didnt detect the phone at all.

after a little reading i saw that virtualbox-ose doesn't support usb, so i uninstalled it and tried to install the 'closed source' or 'full version' it got called a few different things, i'm not sure if there different or both talking about the same thing. but either way, i tried to install virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb and got the following error:

(Reading database ... 166867 files and directories currently installed.)
Unpacking virtualbox (from .../virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb)
dpkg: error processing /tmp/virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb (--install):
trying to overwrite '/lib/modules/2.6.24-19-generic/misc/vboxdrv.ko', which also in package virtualbox-ose-modules-2.6.24-19-generic
dpkg-deb: subprocess killed by signal (Broken pipe)

can anyone help me out here. i'm not sure if i need to delete these files first, and im a little hesitant to start deleting module files before i'm given a little advice.

thanks, jimmy

---

### Post by Elfy on 2008-09-03
Uninstall the -ose versions from synaptic, search for -ose - all I find with that are virtualbox.

Once that is done try to install the puel version.

---

### Post by jimmysheldon on 2008-09-06
that worked great thanks.

---

