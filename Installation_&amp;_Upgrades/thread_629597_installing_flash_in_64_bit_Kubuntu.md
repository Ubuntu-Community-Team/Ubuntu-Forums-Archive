---
title: "installing flash in 64 bit Kubuntu"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-12-02
I found a script from here: [http://www.lockergnome.com/linux/2007/09/22/installing-flash-9-on-64-bit-ubuntu/](http://www.lockergnome.com/linux/2007/09/22/installing-flash-9-on-64-bit-ubuntu/) , and was anticipating that it would work in (K)ubuntu, even though it is for the Gnome version of ubuntu. You are supposed to right click on it and run it in terminal, in KDE, it does not present such an option. KDE only offers the immediate possibility of running it as root, and when I try that I get an error message saying "No such command". Any advice? Thanks.

---

### Post by siouzi on 2007-12-02
In 64-bit Ubuntu there's Adobe Flash Player plugin installer:
```

Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can use
 the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.

```
```

sudo apt-get install flashplugin-nonfree

```

---

### Post by popatopalous on 2008-02-02
> **siouzi said:**
> In 64-bit Ubuntu there's Adobe Flash Player plugin installer:
```

Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can use
 the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.

```
```

sudo apt-get install flashplugin-nonfree

```

Apparently that just installs the installer. I installed it and I don't have flash in Firefox. How do I get it to work? Where does it install the installer? Or does it actually install flashplugin without creating a path firefox can use?

---

### Post by popatopalous on 2008-02-02
This installed flashplugin for me in 7.10 x86_64. Don't know how well it works yet.

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

