---
title: "No X after kernel upgrade"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by thoughts on 2006-12-28
Hello,

I'm running Edgy with the stock 2.6.17-10-generic kernel.  I just installed the 2.6.19.1 kernel from kernel.org, built it starting from the old config file (/boot/config-2.6.17-10-generic), and rebooted.  The new kernel boots fine and the system seems mostly fine, until I log in.

At the GDM (graphical) login screen I enter my username and password.  It logs me in, but then almost immediately displays the "your session lasted less than 10 seconds..." message with these errors:

```
/etc/gdm/Xsession: Beginning session setup...
Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

/usr/bin/xmodmap: unable to open display ":0"
Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified
```

At this point all I can do is hit the OK button, which drops me back at the login screen again.

If I press Ctrl-Alt-F2 to switch to a text console, and then login, and run these commands:

```
sudo killall gdm gdmgreeter X
startx
```

...then X (and Gnome) actually starts properly and I have my normal desktop (but with some other problems, for example when I click Quit -> Logout, nothing happens).

And if I reboot and choose the old 2.6.17 kernel from the grub menu, everything works fine, including X and Gnome.

Any ideas what's going wrong or how to fix it?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

