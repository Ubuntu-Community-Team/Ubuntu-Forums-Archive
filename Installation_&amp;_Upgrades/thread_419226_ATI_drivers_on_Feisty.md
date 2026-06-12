---
title: "ATI drivers on Feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by holytoledo333 on 2007-04-22
Hi. I need help I can not get my ATI X800 drivers to work. I downloaded it a ran it. I am running Feisty and Feisty has xorg 7.2 and the driver goes up to 7.1 as its requirements. I think it has something to do with that.

[B][SIZE="4"]This is what happened when I ran it.
[/SIZE][/B]

user@user-desktop:~$ '/home/user/Help/ati-driver-installer-8.36.5-x86.x86_64.run' 
Created directory fglrx-install.d24190
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.36.5...............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.d24190
user@user-desktop:~$

---

### Post by pepsi_max2k on 2007-04-22
>> I am running Feisty and Feisty has xorg 7.2 and the driver goes up to 7.1 as its requirements. I think it has 
>> something to do with that.

that'll prolly be it. it def. won't work on 7.2 if it's only meant for 7.1.

---

### Post by Toadmund on 2007-04-22
I have the same problem.
I am waiting (im)patiently.

---

### Post by jdong on 2007-04-22
Please use ATI drivers from the repositories:


Either open up the Restricted Driver Manager in Administration then check ATI drivers, or:
```

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

---

### Post by Inspire1997 on 2007-04-22
I tried selecting the drivers from the restricted area, rebooted and got a blank screen. Now i'll try recovery mode and reinstall xserver

---

### Post by Toadmund on 2007-04-23
OK, Am I supposed to select 'Gnome with xgl' in 'Options' in the log-in screen?

When I do that all my icons are scrambled, but the desktop pic is OK.

---

