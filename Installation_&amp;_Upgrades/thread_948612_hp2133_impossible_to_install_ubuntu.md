---
title: "hp2133 impossible to install ubuntu?"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by lepire on 2008-10-15
Hi,

I'm trying to install ubuntu on my mini note hp2133 (1,6 ghz via, 2go ram, 160 gb hard disk) shipped with Vista.

I've tries, 8.10 beta, xbuntu, 8.04, netinstall, live cd via usb key like in all the tutorial on line... and NADA.. Nothing! Impossible.

I see the ubuntu logo at start and then the screen freeze and that's it! Always the same problem.

I've just tried to add "xforcevesa" in syslinux... but it doen't change anything.

Any idea? or help hint?

---

### Post by mssever on 2008-10-16
> **lepire said:**
> Hi,

I'm trying to install ubuntu on my mini note hp2133 (1,6 ghz via, 2go ram, 160 gb hard disk) shipped with Vista.

I've tries, 8.10 beta, xbuntu, 8.04, netinstall, live cd via usb key like in all the tutorial on line... and NADA.. Nothing! Impossible.

I see the ubuntu logo at start and then the screen freeze and that's it! Always the same problem.

I've just tried to add "xforcevesa" in syslinux... but it doen't change anything.

Any idea? or help hint?
If you've tried the alternate install CD and it still doesn't work, you might have to try another distro. Ubuntu works well with a lot of hardware, but every once in a while there's hardware that works better on some other distro.

---

### Post by michealk on 2008-10-30
> **lepire said:**
> Hi,

I'm trying to install ubuntu on my mini note hp2133 (1,6 ghz via, 2go ram, 160 gb hard disk) shipped with Vista.

I've tries, 8.10 beta, xbuntu, 8.04, netinstall, live cd via usb key like in all the tutorial on line... and NADA.. Nothing! Impossible.


Nope, not impossible! I'm happily running 8.04 on my HP 2133. Installed via Live CD from a USB external DVD drive. I've also installed it via a live CD usb key.

I followed the instructions here: [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

If those don't work for you, I'm not sure what the problem could be...

---

### Post by reidy90 on 2008-10-31
I followed the instructions at [ pendrive linux ]("http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/") to to a clean install of ubuntu 8.10 on my hp 2133.

At the pre-boot menu you must select the help option, and then type 
```
live xforcevesa
```
This will fix the graphics problem some people have been having.

---

### Post by nickdngr on 2008-11-02
I didn't have any problems installing 8.04 on it back in August. Right now it's at home downloading 8.10, which hopefully won't be a nightmare. The wiki is dead on for a clean install.

---

### Post by lepire on 2008-11-03
reidy90 which hp2133 do you have? The 1.6ghz 2go ram with vista preinstalled?

---

### Post by luvit on 2008-11-23
i had that exact same problem.  the solution you're looking for is detailed in [[COLOR="Blue"]_**this thread**_[/COLOR]]("http://www.hp2133guide.com/forums/viewtopic.php?p=7176#7176")
.

---

### Post by windowsseven on 2008-12-16
or go 2 [http://www.ubuntu2133.blogspot.com/]("http://www.ubuntu2133.blogspot.com/")

Guides for hp 2133 on ubuntu.:guitar:

---

