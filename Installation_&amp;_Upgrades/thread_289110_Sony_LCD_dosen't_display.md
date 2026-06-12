---
title: "Sony LCD dosen't display"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Orbital75 on 2006-10-30
I have tried to install Ubuntu versions 6.06.1 and 6.10 both will not work with my monitor.  I am running a Sony HS74P...... The CD runs durning boot and Ubuntu starts its loading.  After the Progress Bar has filled completely the monitor goes blank and my orange standby light apears on my monitor.  Now I can hear the startup sound as Ubuntu starts up, I just can't see anything.  I have tried safemode as well.  Any Ideas......

---

### Post by meng on 2006-10-30
I assume this has to do with the xserver trying to run a display at a higher refresh rate than your LCD monitor can support. My advice would be to ctrl-alt-backspace when the monitor goes black, as this should return you to a console mode. Then login and edit the /etc/X11/xorg.conf and change the screen refresh rate and/or resolution to numbers suitable for your monitor.

---

### Post by Kateikyoushi on 2006-10-30
You could try this to reconfigure X, might be easier than editing the config file.

```
sudo dpkg-reconfigure xserver-xorg
```

---

