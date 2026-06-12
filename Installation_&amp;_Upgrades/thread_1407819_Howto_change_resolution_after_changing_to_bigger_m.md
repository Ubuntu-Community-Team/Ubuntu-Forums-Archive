---
title: "Howto change resolution after changing to bigger monitor? can't access menu:("
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by breadbin on 2010-02-15
basically how to change the resolution in gnome when i can't access the menu cos i can't see it. the ctrl alt + or - doesn't work for some reason.

the new monitor is a 24" samsung lcd and the old one was a 17" sony trinitron. think the old resolution was 1024x768. the new resolution must be 640x480 or something cos its huge on the screen. any help will be much appreciated:)

---

### Post by josepaul on 2010-02-15
can you see the rest of your desktop? if so then you can move it down using the controls on the monitor, if you can't do that, post back

---

### Post by johnson.d on 2010-02-16
The display preferences can be changed without accessing the Gnome menu through the mouse pointer by using following steps:

You can access the GNOME menu by using the key combination Alt + F1.
Then you can access the display configuration by
GNOME menu (Alt + F1) -> System -> Preferences -> Display

You can also use Alt + F2 in the desktop which shows 'Run Application' where you can enter 
gnome-display-properties.

---

### Post by breadbin on 2010-02-16
thanks ill try that:)

---

### Post by dE_logics on 2010-02-16
You need to reconfigure X server.

Press alt+cntrl+F2

Login with your username and passwd (you will not see the password being typed).

Run - 

```
sudo /etc/init.d/gdm stop
```

Then run - 

```
sudo Xorg -configure
```

```
cp /home/<your user name>/xorg.conf.new /etc/X11/xorg.conf
```

```
/etc/init.d/gdm start
```

---

