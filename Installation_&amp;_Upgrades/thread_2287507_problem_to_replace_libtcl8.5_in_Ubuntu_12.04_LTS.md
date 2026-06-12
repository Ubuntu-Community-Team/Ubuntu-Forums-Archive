---
title: "problem to replace libtcl8.5 in Ubuntu 12.04 LTS"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by gschelotto on 2015-07-20
Hello,

I was able to get the libtcl8.5 package at [http://packages.ubuntu.com/precise/tcl8.5](http://packages.ubuntu.com/precise/tcl8.5)
but I cannot install it by using
[FONT=courier new]
sudo dpkg -i tcl8.5_8.5.11-1ubuntu1_amd64.deb
[/FONT]
Here's the console output:

[FONT=courier new]gaston@gaston-XPS13:~/Downloads$ sudo dpkg -i tcl8.5_8.5.11-1ubuntu1_amd64.deb
(Reading database ... 1012443 files and directories currently installed.)
Preparing to replace tcl8.5 8.5.11-1ubuntu1 (using tcl8.5_8.5.11-1ubuntu1_amd64.deb) ...
Unpacking replacement tcl8.5 ...
Setting up tcl8.5 (8.5.11-1ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/local/lib/libjlinkpic32.so.4.94.8 is not an ELF file - it has the wrong magic bytes at the start.
[/FONT]
Any hints about the magic bytes? I don't know what does it means.

regards,
gaston

---

### Post by steeldriver on 2015-07-20
That's likely nothing to do with libtcl8.5, it just manifests itself because ldconfig gets run as part of the process - are you sure that the dpkg command didn't succeed regardless?

The actual error seems to be related to software called mplab: [http://mplab25.rssing.com/chan-26031674/all_p129.html](http://mplab25.rssing.com/chan-26031674/all_p129.html)

---

### Post by gschelotto on 2015-07-28
> are you sure that the dpkg command didn't succeed regardless?

It seems that dpkg didn't succeed. Here's the output when I try to install a software called USBDM.

[FONT=courier new]gaston@gaston-XPS13:~/Downloads$ sudo dpkg -i usbdm_4.11.1.60-1-amd64.deb
[sudo] password for gaston: 
Selecting previously unselected package usbdm.
(Reading database ... 1069788 files and directories currently installed.)
Unpacking usbdm (from usbdm_4.11.1.60-1-amd64.deb) ...
dpkg: dependency problems prevent configuration of usbdm:
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
I have already installed the MPLAB software but I don't understand how it can be related.
Any suggestion?

---

### Post by steeldriver on 2015-07-28
Probably what you're bumping up against is that the packaging of TCL components seems to have changed between 12.04 and 14.04: in 12.04 it appears that a single package 'tcl8.5' contains the tcl shell AND runtime library files, whereas in later releases there is a separate 'libtcl8.5' package:

```

$ apt-cache search tcl8.5      **# Precise**
[B]tcl8.5 - Tcl (the Tool Command Language) v8.5 - run-time files
[/B]tcl8.5-dev - Tcl (the Tool Command Language) v8.5 - development files
tcl8.5-doc - Tcl (the Tool Command Language) v8.5 - manual pages
tcl8.5-kwwidgets - Cross-Platform GUI Toolkit - TCL/TK

```

```

$ apt-cache search tcl8.5      **# Trusty**
**libtcl8.5 - Tcl (the Tool Command Language) v8.5 - run-time [COLOR=#ff0000]library [/COLOR]files**
libtcl8.5-dbg - Symbol files for libtcl8.5
**tcl8.5 - Tcl (the Tool Command Language) v8.5 - shell**
tcl8.5-dev - Tcl (the Tool Command Language) v8.5 - development files
tcl8.5-doc - Tcl (the Tool Command Language) v8.5 - manual pages
tcl8.5-kwwidgets - Cross-Platform GUI Toolkit - TCL/TK

```

You have installed tcl8.5 but the usbm deb is expecting to find **lib**tcl8.5 - I don't know a way around that aside from using a usbm deb that is appropriate for your system.

---

