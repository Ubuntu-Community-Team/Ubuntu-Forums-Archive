---
title: "Ubuntu Server GUI"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by ndicostanzo on 2007-08-22
Hey guys. I've loaded Ubuntu Server 7.04 and I'm trying to install a GUI. I've read several different posts and tried different command lines and it basically keeps telling me that it can't find the package.
I'll be honest and say that I'm new to this Linux thing, but I'm also very determined. Any help would be greatly appreciated. Not sure if this matters, but it's also not currently connected to the internet.

Thanks

---

### Post by Patrick793 on 2007-08-22
You need to be connected to the internet to get the GUI I think...

---

### Post by codejunkie on 2007-08-22
as **Patrick793** said you need to be connected to the internet then run ```
sudo apt-get install ubuntu-desktop
```for the gnome desktop run ```
sudo apt-get install kubuntu-desktop
``` for the kde desktop or ```
sudo apt-get install xubuntu-desktop
``` for the xfce desktop, if you can't get internet on that computer you can also add cd-rom's as repositories and should be able

to get the desktop installed that way by placing the cdrom in the drive and running ```
sudo apt-cdrom add
```

---

### Post by vikasiz on 2008-04-22
> **codejunkie said:**
> as **Patrick793** said you need to be connected to the internet then run ```
sudo apt-get install ubuntu-desktop
```for the gnome desktop run ```
sudo apt-get install kubuntu-desktop
``` for the kde desktop or ```
sudo apt-get install xubuntu-desktop
``` for the xfce desktop, if you can't get internet on that computer you can also add cd-rom's as repositories and should be able

to get the desktop installed that way by placing the cdrom in the drive and running ```
sudo apt-cdrom add
```

How does one get the desktop in cd - is it just the desktop version of ubuntu [the iso file] ??
I have installed the server edition and for some reason net is not working from there

Help will be highly appreciated
Thanks

---

