---
title: "how to change xubuntu to ubuntu ?"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by charleshdw on 2008-08-15
how to change the xubuntu 6.06 to ubuntu 7.10?
thanks for your help.

---

### Post by meindian523 on 2008-08-15
More details please.Why not 8.04?

---

### Post by MaxIBoy on 2008-08-15
Assuming you wanted to upgrade to Ubuntu 8.04 instead of 7.10, type 
```
sudo dist-upgrade
```
into the console. The download should take a while. Then find GNOME in the Synaptic Package Manager and install that.


The boot screen will still say "Xubuntu," but the only difference between Xubuntu and Ubuntu is that Xubuntu uses Xfce and Ubuntu uses GNOME.

---

### Post by meindian523 on 2008-08-15
MaxIBoy:
I believe you meant to install ubuntu-desktop?OP will still have Xubuntu,only with the ability to choose between Xfce/GNOME at login.I believe OP wants to switch to Ubuntu completely.

---

### Post by SkonesMickLoud on 2008-08-15
> **meindian523 said:**
> MaxIBoy:
I believe you meant to install ubuntu-desktop?OP will still have Xubuntu,only with the ability to choose between Xfce/GNOME at login.I believe OP wants to switch to Ubuntu completely.

It's better to upgrade in an Xfce only environ, as GNOME is much larger, and installing gnome before upgrading will take much much longer.

A clean install is a much faster option.

---

### Post by meindian523 on 2008-08-15
> **SkonesMickLoud said:**
> It's better to upgrade in an Xfce only environ, as GNOME is much larger, and installing gnome before upgrading will take much much longer.

A clean install is a much faster option.
Exactly what I was going to recommend.And I meant installing ubuntu-desktop AFTER dist-upgrade,not before.

---

