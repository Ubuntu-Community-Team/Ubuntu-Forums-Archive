---
title: "Remove Unity"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Nick Hopton on 2011-05-02
I've just upgraded to 11.04 and don't like Unity, so I'm using Classic (with no effects).

What I'd like to do now is to completely remove Unity from my system. Looking at the package manager, I have the following installed, that all appear to be associated in some way with Unity:

unity
unity-asset-pool
unity-place-applications
unity-place-files
unity-common
gir1.2-unity-3.0
firefox-globalmenu
libunity-misc0
libunity4

We it be safe to remove these packages? I'm only quite new to Ubuntu and still pretty apprehensive about making changes that I don't understand. If it's okay to remove the packages, should I 'completely remove' them?

Regards, Nick.

---

### Post by elliotcroft on 2011-05-02
They should be.
The firefox-globalmenu one doesn't seem to be linked to unity, though, so don't remove it at the moment.
Make sure that you remember their names, in case you need to reinstall them from command line mode.

---

### Post by collisionystm on 2011-05-02
let me know if this works

---

### Post by dino99 on 2011-05-02
well its new, not free bug yet, and need you to be used with it.

two cases:
- with unity installed (default), you can log in selecting "classic" then on next boot this previous choice will be your default, so no worry

- if you really want it off, with synaptic: remove/purge both unity & ubuntu-desktop, that it, no trouble. To get it back, simply reinstall ubuntu-desktop.

---

### Post by Nick Hopton on 2011-05-02
As always, thanks for the help. I did remove all of the Unity packages and everything appears to be working properly in 'Classic'.

Regards, Nick.

---

### Post by temporizer on 2011-12-21
> **dino99 said:**
> well its new, not free bug yet, and need you to be used with it.

two cases:
- with unity installed (default), you can log in selecting "classic" then on next boot this previous choice will be your default, so no worry

- if you really want it off, with synaptic: remove/purge both unity & ubuntu-desktop, that it, no trouble. To get it back, simply reinstall ubuntu-desktop.

upon removing ubuntu-desktop, will this break classic (with effects) or classic (without effects) using the gnome desktop environment?

---

