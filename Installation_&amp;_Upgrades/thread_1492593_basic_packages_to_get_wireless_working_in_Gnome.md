---
title: "basic packages to get wireless working in Gnome"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Arla on 2010-05-24
Let me preface, assuming your wireless card works with gnome, doing an install from scratch, what packages do you need to get wireless working?

So far I've installed gnome-core, menu, menu-xdg and gdm.

network-manager and network-manager-gnome are both now installed, I can setup stuff in network connections, but can't see the nm-applet in the notification area, and it never seems to try to connect to my wireless network, do I need any specific other packages (wireless works fine if I install the entire ubuntu 10.04 live CD).

---

### Post by rob-ward on 2010-05-25
I don't really understand what you are trying to do, have you done a minimal or commandline install and then trying to add gnome to it for your wifi manager? If so do you actually want gnome because using iwconfig you should be able to manage and connect to your wifi from the commandline.

If you are just wanting to install gnome in it's entirety then you need to install

```
sudo apt-get install ubuntu-desktop
```

---

### Post by kimberlite on 2010-05-25
> **Arla said:**
>  (...)

network-manager and network-manager-gnome are both now installed, I can setup stuff in network connections, but can't see the nm-applet in the notification area, and it never seems to try to connect to my wireless network, do I need any specific other packages (wireless works fine if I install the entire ubuntu 10.04 live CD).
I am not sure, but you may miss "nm-applet", "nm-connection-editor" and "nm-tools".

---

### Post by Arla on 2010-05-25
> **rob-ward said:**
> I don't really understand what you are trying to do, have you done a minimal or commandline install and then trying to add gnome to it for your wifi manager? If so do you actually want gnome because using iwconfig you should be able to manage and connect to your wifi from the commandline.

If you are just wanting to install gnome in it's entirety then you need to install

```
sudo apt-get install ubuntu-desktop
```

What I'm trying to do is get a somewhat more minimal gnome environment working, a lot of the default stuff that's installed I just never touch, and would rather not have it wasting space.

As much as anything it's an experiment to see what I can manage to get done (or not) I did a commandline install, then added the gnome-core package and a few others to get gnome working (somewhat), ubuntu desktop has the disadvantage of dragging a TON of stuff in with it (openoffice, evolution, xsane to name but a few that I didn't want to install at this point).

I'm thinking of trying to do it backwards, compare what my install has now against a clean default install, and try to figure out what I can get rid of, I'm just always skeptical of autoremoves ability to actually remove packages that aren't required.

---

### Post by Arla on 2010-05-25
> **kimberlite said:**
> I am not sure, but you may miss "nm-applet", "nm-connection-editor" and "nm-tools".

Will check into those thanks, nm-applet seemed to be installed (and in fact running) I didn't look for nm-connection-editor or nm-tools so will check those, installing wireless-tools seemed to not resolve anything, but will look further tonight.

---

