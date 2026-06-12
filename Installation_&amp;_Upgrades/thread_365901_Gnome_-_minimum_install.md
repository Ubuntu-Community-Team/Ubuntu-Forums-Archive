---
title: "Gnome - minimum install"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Doomsword on 2007-02-20
Hi everybody, I've downloaded and installed the alternate ubuntu version and installed a minimum system (only terminal). I'd like to install Gnome without all the apps preconfigured in "ubuntu-desktop" package. There's a way to do that with "ALTERNATIVE CD" ? I've no way to access to internet and a must do everything from the cd.
I've tryied installing gnome packages and x packages but after starting GDM and doing login a small console appears on the upper left side and no gnome desktop appear :-/
Thanks in advance to everyone :-)

---

### Post by Kateikyoushi on 2007-02-20
Why don't you install ubuntu-desktop or just gnome itself and then remove the packages you do not need ? I think much easier and faster than adding packages one by one to your system.

---

### Post by Doomsword on 2007-02-20
> **Kateikyoushi said:**
> Why don't you install ubuntu-desktop or just gnome itself and then remove the packages you do not need ? I think much easier and faster than adding packages one by one to your system.

I dont think it's the right way to have a CLEAN system install ... why I have to install 1.5GB instead of a clean gnome install? I don't need openoffice, evolution and other application installed with ubuntu-desktop.

---

### Post by Kateikyoushi on 2007-02-20
As I wrote you could also try the gnome package, ehat does that pull in ? I guess that is less but I never tried it myself so can't tell.

---

### Post by njparton on 2008-04-10
Was this ever resolved? I'd like to do this on top of a hardy server install in a couple of months.

---

### Post by njparton on 2008-04-10
Would the following be sufficient to get a working minimal gnome desktop?
 
```
sudo apt-get install xorg gdm gnome-core
```

---

