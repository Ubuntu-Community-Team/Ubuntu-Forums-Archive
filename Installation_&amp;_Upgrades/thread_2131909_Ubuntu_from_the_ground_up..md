---
title: "Ubuntu from the ground up."
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by Zestypanda on 2013-04-03
Is there a way I can install the bare minimal install of Ubuntu? Just gnome and basic standard Ubuntu tools. No third-party apps or anything.,

---

### Post by darkod on 2013-04-03
There is something called minimal CD that installs only the core. From there on you add what you want including the desktop environment (it comes without one).

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by mörgæs on 2013-04-03
This [script]("http://andyduffell.com/techblog/?p=689") comes in handy when you add the packages you want, after you have installed the minimal system.

Unfortunately it stops at Buntu 12.04.

---

### Post by ibjsb4 on 2013-04-03
Another way would be to do a terminal only install with the mini iso and then install ubuntu without the recommend packages.  This turns a 600+MB install into about 160MB.

The command for this type of install:

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

---

### Post by matt_symes on 2013-04-03
Hi

You could install the system using ```
debootstrap
```

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

Kind regards

---

### Post by Zestypanda on 2013-04-04
Thanks guys, thanks for the help I will check this all out

---

### Post by Zestypanda on 2013-04-04
O.0 catch 22, does the minimal base install (terminal) have wifi drivers?

---

### Post by matt_symes on 2013-04-04
Hi

> **Zestypanda said:**
> O.0 catch 22, does the minimal base install (terminal) have wifi drivers?

I'm unsure about this as last time i did a minimal install using the iso, i connected via ethernet.

If you go down the debootstrap route and install the minimal system from a desktop LiveCD/USB, you should be able to install all the drivers and everything else you need (such as grub).

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

It's a more complicated way to do it than a minimal install from one of the isos though. So this will depend on how well you know how to install an Ubuntu system.

As for whether the minimal iso contains wireless drivers, you could just download a minimal iso and try it.

Kind regards

---

### Post by mörgæs on 2013-04-05
> **Zestypanda said:**
> O.0 catch 22, does the minimal base install (terminal) have wifi drivers?

It's unlikely. As the name indicates it's minimal, some 20-30 MB. Also, many cards need closed-source drivers which for sure are not part of the package.

Even if they were available I would recommend installing with a wired connection. Only when that works well and all updates have been applied it's time to focus on the wirefree.

---

### Post by darkod on 2013-04-05
Yeah, you are making it complicated for yourself. Unless you are stealing that wi-fi from the neighbour, you have a router someplace at home and can connect the machine to it to install at least. :) Use a good old cable and don't create more headaches for yourself than you need to. :)

---

