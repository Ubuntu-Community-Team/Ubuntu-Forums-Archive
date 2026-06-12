---
title: "Installing ubuntu over kubuntu"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by MetalliMix03 on 2008-09-16
i have kubuntu, the latest version. I didn't like it too much, i think gnome will be better. so i've decided to install ubuntu over kubuntu. I have dual boot. XP and Kubuntu. i don't want to remove xp. i just want to remove kubuntu. should i uninstall kubuntu then install ubuntu? or install ubuntu on the same partition?

when i install kubuntu, i think it created many partition, if i'm not mistaken. so if anyone can help, that'll be cool

---

### Post by Pumalite on 2008-09-16
You can go Manual and install on top of Kubuntu. You can ignore /swap

---

### Post by manishtech on 2008-09-16
> i just want to remove kubuntu. should i uninstall kubuntu then install ubuntu? or install ubuntu on the same partition?
There is nothing called uninstalling an Operating System. Though it is possible only by Wubi.

Just reinstall ubuntu over kubuntu. For this start ubuntu installation, when asked for partitioning goto "Manual Partitioning". There select the kubuntu partition as / and then proceed with the installation. Its done. :)

---

### Post by zvacet on 2008-09-16
You don´t need to uninstall Kubuntu.You can install Ubuntu desktop and remove Kubuntu desktop.Instructions are [here.]("http://psychocats.s465.sureserver.com/ubuntu/puregnome") Read **Remove Kubuntu**.

---

### Post by manishtech on 2008-09-17
> **zvacet said:**
> You don´t need to uninstall Kubuntu.You can install Ubuntu desktop and remove Kubuntu desktop.Instructions are [here.]("http://psychocats.s465.sureserver.com/ubuntu/puregnome") Read **Remove Kubuntu**.
Would it be a good way? I have kubuntu-desktop installed in Ubuntu. But I had preferred that I installed kubuntu separately.
I always suggest a fresh reinstall, but its my personal opinion.

---

### Post by SkonesMickLoud on 2008-09-17
No need to reinstall anything!

Simply open up a terminal window and enter:

```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```You'll get a prompt asking if you want to keep KDM or switch to GDM.  It's your choice.  They both do the same thing, but if you are going to stick with GNOME, you should choose GDM.

Then, all you have to to is logout or restart X (Ctrl+Alt+Backspace) and select GNOME from the "Session" menu.  Log in as normal and there's GNOME.

If you want to remove KDE simply:

```
sudo aptitude remove kubuntu-desktop && sudo aptitude autoclean
```

---

### Post by robert shearer on 2008-09-17
> **SkonesMickLoud said:**
> No need to reinstall anything!

Simply open up a terminal window and enter:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```
You'll get a prompt asking if you want to keep KDM or switch to GDM.  It's your choice.  They both do the same thing, but if you are going to stick with GNOME, you should choose GDM.

Then, all you have to to is logout or restart X (Ctrl+Alt+Backspace) and select GNOME from the "Session" menu.  Log in as normal and there's GNOME.

If you want to remove KDE simply:

```
sudo aptitude remove kubuntu-desktop && sudo aptitude autoclean
```

Maybe this        sudo aptitude update && sudo aptitude install kubuntu-desktop

Should be this    sudo aptitude update && sudo aptitude install ubuntu-desktop

???

---

### Post by SkonesMickLoud on 2008-09-17
> **robert shearer said:**
> Maybe this        sudo aptitude update && sudo aptitude install kubuntu-desktop

Should be this    sudo aptitude update && sudo aptitude install ubuntu-desktop

???

Oops!  Sure should be.

---

