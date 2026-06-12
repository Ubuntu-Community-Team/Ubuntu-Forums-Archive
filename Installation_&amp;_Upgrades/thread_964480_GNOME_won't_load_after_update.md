---
title: "GNOME won't load after update"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by brotherajnin on 2008-10-30
Today I updated from 8.04 and after I provide my login and password, the (brown) screen stays blank (i.e. the panels, desktop, etc. never load).  I can move around my mouse, but that's it. 

I can login fine using KDE... any idea on how I go about isolating the Gnome problem?

Thanks a lot.

---

### Post by martrn on 2008-10-31
You can load KDE perfectly ?

Try logging in to a terminal (or booting up in rescue mode) and type:

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

See if there is anything starting up that will cause a problem
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```
and remove any unecessary services.

If you think you might have some problems with X11 try:
```
dpkg-reconfigure x-server x-org
```

Check you /etc/rc2.d directory for run-level scripts.  I don't know but try deleteing gnome directory in your /home/yourname folder.

---

### Post by brotherajnin on 2008-10-31
Thanks for the quick reply.  I tried uninstalling compiz, to no avail.  As far as the last two options, I'm not sure what exactly I'm looking for.  Any suggestions?  Thanks for your patience.

---

### Post by martrn on 2008-10-31
> **brotherajnin said:**
> Thanks for the quick reply.  I tried uninstalling compiz, to no avail.  As far as the last two options, I'm not sure what exactly I'm looking for.  Any suggestions?  Thanks for your patience.

If you look here it will give you more info regarding the things loaded using the runlevel sysv scripts : [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

See if there is anything starting up that will cause a problem
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

Try to switch off things bluetoothy/power-on-off-sleep/HALinitialisation (failure)problems/etc.  If you can load KDE something here might cause a problem.

Check you have deleted all your .gnome directories from your /home/yourname  folder.

If you wish to reinstall gnome try :-
```
sudo apt-get remove --purge gnome
sudo apt-get install gnome
```

---

