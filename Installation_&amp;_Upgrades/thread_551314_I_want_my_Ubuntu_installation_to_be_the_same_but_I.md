---
title: "I want my Ubuntu installation to be the same but I want to add option of Xfce"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by s3a on 2007-09-15
I want my Ubuntu installation to be the same but I want to add option of the Xfce environment in the login window. Is there a way to do this without having an optical drive on the computer or the Xubuntu CD? If not, then it should be possible to achieve this through an external optical drive with the Xubuntu CD or would I need boot privileges?

*I only want to install the Xfce environment NOT all the other applications included with Xubuntu such as Abiword, etc.*

Thanks in advance!

---

### Post by edd07 on 2007-09-15
You can use Synaptic or 
```
sudo apt-get install xubuntu-desktop
```
to install the xfce environment, however, that will install all the xubuntu applications as well. You could try removing them :P, or search for a xfce-only package.

---

### Post by Warren Watts on 2007-09-15
You can try this:

```
sudo apt-get install xfce4 xfce4-appfinder xfce4-artwork xfce4-goodies
```

This will only install pretty much the bare minimum you need to start a Xfce session.  But you will have to build all of your Xfce panels from scratch.

---

### Post by s3a on 2007-09-15
> **Warren Watts said:**
> You can try this:

```
sudo apt-get install xfce4 xfce4-appfinder xfce4-artwork xfce4-goodies
```

This will only install pretty much the bare minimum you need to start a Xfce session.  But you will have to build all of your Xfce panels from scratch.
Doesn't the Xfce understand both Gnome and KDE applications? So if I only have Xfce, I can use my Ubuntu programs, right? I want to do this on my laptop which has no functional internet at the moment but I do have a desktop PC with internet running Ubuntu Feisty so...is there a command that will download what I need only without installing it so that I can just bring it to laptop and type in another command to install it?

Thanks!

---

### Post by aysiu on 2007-09-15
Yes, you can install only *xfce4* and then use Gnome and KDE applications.

---

