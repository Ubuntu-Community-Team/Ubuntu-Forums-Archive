---
title: "Minimal GUI installation"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by taxidimu on 2010-11-23
How can I install a minimal GUI interface, on a Ubuntu server?
And more: Suse has a RUNLEVEL tool, to select application to be launched. What in Ubuntu?

I need a GUI interface ONLY to use some useful administration tools, no other application, and need to charge the system as less as possible.

Thanks.

---

### Post by pawhtiobo on 2010-11-23
Hi :)

In my case i run my server with no GUI and installed Webmin to have some GUI interface for the tools, and it rocks :).
If you really want a light GUI in the server you shouldn't use Gnome (ubuntu-desktop), use LXDE, XFCE, Enlightment (more funcionality) or busybox, openbox, fluxbox (more simple).

Take a look at this for more infoemation:

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

About runlevels:

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)


See ya...

---

### Post by wet-willy on 2010-11-23
In my opinion, the best route to take when looking for a lean Debian based system is to install a base minimal Debian and start adding what you want, like Xfce for a lean/no frills nice desktop.
If you are set on Ubuntu, you'll have to un-install Gnome if you feel it's too heavy, and add a different desktop, but one could expect some broken apps running down this trail. You could look at Xubuntu which is Ubuntu with Xfce as the default window manager.
Personally, being a long time lean Debian user, I find Ubuntu is nicely put together for a CD sized desktop OS. And being that small, it might give one the impression it's not bloated "as is".

---

### Post by taxidimu on 2011-01-27
How can I customize a minimal gnome installation?
It seems to me that no option is available at installation.
Thanks

---

### Post by Zlatan on 2011-01-27
> **taxidimu said:**
> How can I customize a minimal gnome installation?
It seems to me that no option is available at installation.
Thanks

you could try
```
sudo apt-get install gnome-core gdm
```
check with the packages if this is what you want

---

