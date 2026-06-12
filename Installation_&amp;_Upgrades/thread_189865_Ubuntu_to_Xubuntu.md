---
title: "Ubuntu to Xubuntu"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by FoggyMtn on 2006-06-05
Hello

This is my first time upgrading releases.  I currently am running Breezy BAdger Ubuntu and want to upgrade to Dapper X-ubuntu.  Can I do an upgrade (either with the alternate cd or via the gui) or do I HAVE to do a clean install..

I couldn't find anything on how to upgrade from one flavor to another...

Thanks Ya'll

rob

---

### Post by Sgood1971 on 2006-06-05
[QUOTE=FoggyMtn]Hello

This is my first time upgrading releases.  I currently am running Breezy BAdger Ubuntu and want to upgrade to Dapper X-ubuntu.  Can I do an upgrade (either with the alternate cd or via the gui) or do I HAVE to do a clean install..

I couldn't find anything on how to upgrade from one flavor to another...

Thanks Ya'll

rob[/QUOTE]

It's not really an upgrade, just a different window manager.

Do

```
sudo apt-get install xubuntu-desktop
```

Then the next time you log in, choose XFCE from the session dialog.

---

### Post by FoggyMtn on 2006-06-05
OOohhh... could you see the lightbulb click on? :)  I already installed the window manager...  I thought xubuntu had a different core installation too, not just the window manager!  

So if I apt-get uninstall the gnome window manager, I in essence have the xubuntu version, right?  And I guess this means I can do the standard upgrade to Dapper?

Thanks!


Rob

---

### Post by John.Michael.Kane on 2006-06-05
FoggyMtn if you have xubuntu desktop installed already dist-upgrade while log into xubuntu.

---

### Post by FoggyMtn on 2006-06-05
[QUOTE=SD-Plissken]FoggyMtn if you have xubuntu desktop installed already dist-upgrade while log into xubuntu.[/QUOTE]
And please excuse my ignorance, when you say "xubuntu desktop installed", that's xfce, right?  And when you say logged into xubuntu, you just mean usung the xfce window manager?  I originally installed breezy ubuntu, but then tried the xfce to speed things up...

THanks abunch!!  
rob

---

### Post by John.Michael.Kane on 2006-06-05
xubuntu desktop=xfce. yes I mean using xfce window manager. just dist-upgrade from that, and you should be fine.

---

