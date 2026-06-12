---
title: "apt-get udate some?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by rodmacpherson on 2009-12-22
Does anyone know of a way to script apt-get to upgrade all but a predefined list of packages? I'd like to be able to hold back certain packages for compatibility reasons, but automatically update anything else. 

Namely, I want to NOT auto upgrade the kernel as that will break compatibility with VMWare Server until the kernel components of VMWare are recompiled (somthing i"d like to be in front of the machine to do) but I'd like all of the rest of the packages to upgrade as they are released.

---

### Post by starcraft.man on 2009-12-22
> **rodmacpherson said:**
> Does anyone know of a way to script apt-get to upgrade all but a predefined list of packages? I'd like to be able to hold back certain packages for compatibility reasons, but automatically update anything else. 

Namely, I want to NOT auto upgrade the kernel as that will break compatibility with VMWare Server until the kernel components of VMWare are recompiled (somthing i"d like to be in front of the machine to do) but I'd like all of the rest of the packages to upgrade as they are released.

Easy enough, either use Synaptic manager or Aptitudes commands/curses interface to put a hold on the appropriate packages. There's no need for a script. In Synaptic you for instance select the designated package (check in main window) and go Package Menu > Lock version. Same as a hold.

---

### Post by snowpine on 2009-12-22
You can also do it from the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

will not upgrade your kernel.

---

