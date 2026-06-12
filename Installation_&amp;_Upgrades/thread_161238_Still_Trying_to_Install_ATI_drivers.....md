---
title: "Still Trying to Install ATI drivers...."
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by general_error on 2006-04-16
I'm still trying to install the native ATI drivers.  I have X850 XT graphics card.

I was running Breezy.  Someone suggested I upgrade to Dapper to get ATI driver support.

So I upgraded my distro to Dapper.

Now when I run the ATI driver installer it doesn't support my version of X.org version 7.0.
Detected configuration:

[I]Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x
Removing temporary directory: fglrx-install[/I]


So how do I downgrade back to X.org version 6.9 so I can install this driver?

---

### Post by Ensnared on 2006-04-16
You don't have to - it should work to just specify X.Org 6.9 when running the installer, that will also work with X.Org 7.0.

You'll find complete instructions on the [Unofficial ATI Linux Driver Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide).

---

