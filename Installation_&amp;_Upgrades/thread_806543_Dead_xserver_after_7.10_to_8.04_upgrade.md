---
title: "Dead xserver after 7.10 to 8.04 upgrade?"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Cleric. on 2008-05-25
A friend of mine has had some problems with Kubuntu every time he goes to upgrade from one version to another.
He has a 7.10 CD and upgrades to 8.04.
If I understand correctly, every time he upgrades, the first time his computer restarts everything is fine, but after he goes to restart X or the computer after that first time after upgrading, X completely dies on him.

His computer is an HP a800n and he's using integrated graphics with the VESA driver.

I've tried running him through ```
dpkg-reconfigure xserver-xorg
``` but to no avail; nothing changed.

Nothing at all happens when running ```
kdm restart
``` either.

Is there anything else I can do to try to remedy this situation?
Would reinstalling all the xorg related packages possibly help at all? And if that would help, what are the names of the packages I'd need to have him reinstall?

---

### Post by Cleric. on 2008-05-25
Bump? :(

---

### Post by dstew on 2008-05-25
For Hardy, dpkg-reconfigure does not work for the display. You need to first boot in Recovery Mode, and chose **xfix**. That should get you a vesa-driven desktop. Then, look for a restricted driver in System --> Administration --> Hardware Drivers. If one is available, activate it. You might have to re-start. At restart, your display should return, but the resolution might be bad. If so, press alt-F2, and enter ```
gksudo displayconfig-gtk
```This configuration front-end will let you pick your monitor type and resolution. You can also change the video display driver also, if you want.

---

