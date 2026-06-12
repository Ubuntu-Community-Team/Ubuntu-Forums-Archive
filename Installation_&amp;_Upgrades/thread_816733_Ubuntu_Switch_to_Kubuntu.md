---
title: "Ubuntu Switch to Kubuntu?"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Landscapeman on 2008-06-03
I have ubuntu on both of my computers and I am looking in to Kubuntu. I need some help on how to switch from ubuntu to kubuntu on a windows xp dual boot. Heres the kicker is there a way not to loose any info on the windows side(I run Quickbooks 08 pro for my bus.). I love ubuntu on my laptop but i figured I would give kubuntu a shot on the desktop. Thanks for the help.

---

### Post by iaculallad on 2008-06-03
You can install (k)Ubuntu by typing the code in your terminal:

```
sudo apt-get install kubuntu-desktop
```

After installation, you can change desktop by modifying the /etc/X11/default-display-manager file.

KDM = /usr/bin/kdm
GDM = /usr/bin/gdm

---

### Post by Landscapeman on 2008-06-03
I'll give it a shot. Thanks

---

### Post by aquavitae on 2008-06-03
> **iaculallad said:**
> You can install (k)Ubuntu by typing the code in your terminal:

```
sudo apt-get install kubuntu-desktop
```

After installation, you can change desktop by modifying the /etc/X11/default-display-manager file.

KDM = /usr/bin/kdm
GDM = /usr/bin/gdm
I don't think you have to manually switch to kdm - IIRC a question pops up when kdm is installed asking which you want to use.

The thing to remember its not a case of installing Kubuntu instead of Ubuntu, its just installing all the packages that come with Kubuntu and (presumably) removing the ones that came with Ubuntu.

---

### Post by kesman on 2008-06-03
Nah, It won't even remove anything. If you can find a package called kubuntu-default-settings, install it. Also search for "kubuntu" in synaptic or apt-cache search function to see if there's something else you'd like to install.

---

### Post by iaculallad on 2008-06-03
> **aquavitae said:**
> I don't think you have to manually switch to kdm - IIRC a question pops up when kdm is installed asking which you want to use.

The thing to remember its not a case of installing Kubuntu instead of Ubuntu, its just installing all the packages that come with Kubuntu and (presumably) removing the ones that came with Ubuntu.

You would be prompted of an option on what Desktop you want to use as default, but then again, if you want to use the other Desktop as default, you could always change it by by modifying the /etc/X11/default-display-manager file.

---

### Post by mde123 on 2008-06-03
oh, um and make sure that when you do what the the person said before me,

log out, and click sessions and click in KDE

---

### Post by kellemes on 2008-06-03
> **aquavitae said:**
> I don't think you have to manually switch to kdm - IIRC a question pops up when kdm is installed asking which you want to use.


Indeed, also you can issue the following command.
```
sudo dpkg-reconfigure gdm
```

---

### Post by aquavitae on 2008-06-03
> **kesman said:**
> Nah, It won't even remove anything. If you can find a package called kubuntu-default-settings, install it. Also search for "kubuntu" in synaptic or apt-cache search function to see if there's something else you'd like to install.
No, installing kubuntu won't uninstall anything, but the OP would probably want to remove most of the gnome stuff if its not being used. The point I was trying to make is that its not like installing a new operating system, its just a question of which packages you have.

---

