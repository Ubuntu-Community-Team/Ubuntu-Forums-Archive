---
title: "Looking up list of active drivers"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by Elssha on 2008-08-27
Hi, 
  hopefully, this is a real simple question, but I can't seem to find anywhere that will list what drivers are active on my system and where they are located. Is there a place (I looked all over the admin and pref menus) or a command I can type into terminal that will give me this information? 
  I ask because I am thinking of doing a clean install of Ubuntu now that I know more about which programs I use and what works. However, I am running ubuntu on a laptop, and had to hunt for drivers for a long time to get everything running right (the bad versions of which making up some of the clutter i want to delete from the sys). Thanks, 
El

---

### Post by roaldz on 2008-08-27
> **Elssha said:**
> Hi, 
  hopefully, this is a real simple question, but I can't seem to find anywhere that will list what drivers are active on my system and where they are located. Is there a place (I looked all over the admin and pref menus) or a command I can type into terminal that will give me this information? 
  I ask because I am thinking of doing a clean install of Ubuntu now that I know more about which programs I use and what works. However, I am running ubuntu on a laptop, and had to hunt for drivers for a long time to get everything running right (the bad versions of which making up some of the clutter i want to delete from the sys). Thanks, 
El

Drivers are modules, which you can view with:

lsmod

---

### Post by iaculallad on 2008-08-27
Usually, Ubuntu auto-detect and auto-install drivers for hardwares that it can support. You could always use the "Restricted Drivers Manager" to install proprietary drivers for your un/supported hardware.

---

### Post by Elssha on 2008-08-27
is ismod a program i need to install? It doesn't seem to work in commandline
 
I remember not being able to use the restricted drivers manager when we first installed Hardy (I had help from a friend with far more experience), and the drivers we did find were a hit n' miss... grrr, stupid sony >_<

---

### Post by iaculallad on 2008-08-27
> **Elssha said:**
> is ismod a program i need to install? It doesn't seem to work in commandline
 
I remember not being able to use the restricted drivers manager when we first installed Hardy (I had help from a friend with far more experience), and the drivers we did find were a hit n' miss... grrr, stupid sony >_<

It's lsmod and not ismod.

```
lsmod
```

To know more about lsmod, do **man lsmod** on your terminal.

---

### Post by Elssha on 2008-08-27
>_< thanks...

---

