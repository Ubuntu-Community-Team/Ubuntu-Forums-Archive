---
title: "cannot get gtk3+ and wxwidgets3 in 12.04 LTS"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by gschelotto on 2015-07-15
Hello,

I've tried to build & install both packages in Ubuntu 12.04 LTS. Build is okay but there is a lot of dependence issues during installation. Are you planed to provide them from the Software Center? I'd like to use some software that requires wxwidgets3 and gtk3+ and I'm not an experienced linux user.

thanks in advance,
gaston

---

### Post by steeldriver on 2015-07-15
Hello and welcome to the forums

The GTK+3 development headers and libraries should be available from the 12.04 repository as package **libgtk-3-dev**

There is at least one PPA offering a pre-built wxWidgets3 fro 12.04 (although I didn't try it myself) --> [https://launchpad.net/~wxformbuilder/+archive/ubuntu/wxwidgets](https://launchpad.net/~wxformbuilder/+archive/ubuntu/wxwidgets)

Otherwise, if you provide some more information about the specific dependency issues you are having we can try to help you resolve them

---

### Post by gschelotto on 2015-07-17
Thank you for replying. Here's my dependence issue:

[FONT=courier new]gaston@gaston-XPS13:~/Downloads$ sudo dpkg -i usbdm_4.11.1.60-1-amd64.deb
[sudo] password for gaston: 
Selecting previously unselected package usbdm.
(Reading database ... 1009725 files and directories currently installed.)
Unpacking usbdm (from usbdm_4.11.1.60-1-amd64.deb) ...
dpkg: dependency problems prevent configuration of usbdm:
 usbdm depends on libwxgtk3.0-0; however:
  Package libwxgtk3.0-0 is not installed.
 usbdm depends on libwxbase3.0-0; however:
  Package libwxbase3.0-0 is not installed.
 usbdm depends on libxerces-c3.1; however:
  Package libxerces-c3.1 is not installed.
 usbdm depends on libtcl8.5; however:
  Package libtcl8.5 is not installed.
dpkg: error processing usbdm (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 usbdm
[/FONT]
How can install the PPA you've suggested to solve this issue?

regards,
gaston

---

### Post by steeldriver on 2015-07-17
It should be as simple as

```

sudo add-apt-repository ppa:wxformbuilder/wxwidgets

sudo apt-get update

sudo apt-get install libwxgtk3.0-dev

```

Alternatively, you can add PPAs via the Software Center --> Edit --> Software Sources

---

### Post by gschelotto on 2015-07-20
Thank you for your help. 
This solve the issue.

regards,
gaston

---

