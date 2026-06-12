---
title: "Oh wow, why does Flash work perfectly in Kubuntu AMD 64 9.04, and so poorly in Ubuntu"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hotweiss on 2009-04-11
Flash is working perfectly in Kubuntu AMD 64 9.04, and terribly in Ubuntu AMD 64 9.04. Can't the Ubuntu team borrow the code from the Kubuntu team? This is an open source project after al. It would be nice to be able to watch full screen Flash HD videos.

---

### Post by zika on 2009-04-11
flash works great in JJ Gnome. (10.0 r22, 64-bit) ...

---

### Post by hotweiss on 2009-04-11
Do you have a Nvidia video card? Is your resolution 1920x1200? Did you try full screen HD Youtube videos?

---

### Post by taavikko on 2009-04-11
> **hotweiss said:**
> Flash is working perfectly in Kubuntu AMD 64 9.04, and terribly in Ubuntu AMD 64 9.04. Can't the Ubuntu team borrow the code from the Kubuntu team? This is an open source project after al. It would be nice to be able to watch full screen Flash HD videos.

Only difference in these two are the desktop enviroments in use.
Everything is the same under the hood.

What version of flash are you using?
Are these on separate partitions or what is the setup?

---

### Post by zika on 2009-04-11
> **hotweiss said:**
> Do you have a Nvidia video card? Is your resolution 1920x1200? Did you try full screen HD Youtube videos?
No. No. Yes. ???????

---

### Post by Zorael on 2009-04-11
The only things that differ between a Kubuntu and an Ubuntu installation of the same release (9.04b) are the packages installed per default. Mainly, Kubuntu runs KDE and Ubuntu runs GNOME. It's still the same linux underneath, the same drivers, the same openoffice, the same firefox, and the same flash. They use the same repositories, so the same range of software is available to both.

In practise, you could install Kubuntu, then remove all desktop packages and end up with a terminal-only installation, then install GNOME and presto; you have an Ubuntu installation. Or take your Kubuntu installation and install GNOME alongside KDE, then you have a Kubuntu+Ubuntu system. Only the very outer layers differ.

Whether it's Ubuntu or Kubuntu is irrelevant for Flash. If fullscreen flash works in one instance and not in another on the same machine, that suggests differences in the videocard driver setup to me.

---

### Post by hotweiss on 2009-04-11
I know that Ubuntu and Kubuntu share the same platform, but Flash videos play perfectly in Kubuntu and stutter in Ubuntu. That is the reason for my post! Why the difference when the platforms are identical?

---

### Post by krazyd on 2009-04-11
There is a difference between Kubuntu and Ubuntu: KDE has its own compositing built into the window manager kwin, while gnome uses Compiz.

Does flash work without Compiz?

---

### Post by Nullack on 2009-04-11
In my gnome 64 bit install I turn compiz off and I run the 64bit flash version from adobe. Works ok.

---

### Post by hotweiss on 2009-04-12
> **Nullack said:**
> In my gnome 64 bit install I turn compiz off and I run the 64bit flash version from adobe. Works ok.

I tried turning Compiz off, but it makes little difference.

---

### Post by hotweiss on 2009-04-18
After some more experimenting it seems that the culprit is compiz. The only problem is that if I turn off compiz, I get tearing.

---

### Post by hotweiss on 2009-04-18
OK, I have found a solution that works in the AMD64 version of Ubuntu.

1. sudo mkdir /etc/adobe

2. sudo nano /etc/adobe/mms.cfg

3. Paste "OverrideGPUValidation=true"

4. Restart Firefox.

---

