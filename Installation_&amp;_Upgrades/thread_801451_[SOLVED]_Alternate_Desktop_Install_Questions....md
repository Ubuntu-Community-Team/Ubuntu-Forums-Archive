---
title: "[SOLVED] Alternate Desktop Install Questions..."
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by lil0tik on 2008-05-20
Hi folks -

I've been running Gutsy on my Dell Inspiron 1501 laptop, dual-booting with Vista (rarely used).  Now, I want to do a clean install of 8.04 and XP.  After using Linux for a while, I've decided I'd like to set up a *mostly* cli-based system, and have been considering the Ubuntu Alternate Desktop install.

My questions:

1) Will the alternate install likely detect my hardware as nicely as the normal x86 install?  (Gutsy Desktop Ed. installed with next-to-no problems).

2) How much of a pain is it to set up Gnome after the fact?  I do want a desktop environment, I'd just like to avoid the bloat of a full, standard install.

Any tips appreciated.
[lil0tik].

---

### Post by lil0tik on 2008-05-20
Sorry, been researching & am going to try my luck / skill with the Server Edition & Flexbox.

---

### Post by atomkarinca on 2008-05-20
You can build your system on a minimal install. If you install your graphics driver there shouldn't be any problem. Just a quick guide for you:

Download a [minimal cd iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and burn it to a blank cd, when you boot up type "cli" (without the quotes) to install a base system. After you answer a few questions the system will restart. First uncomment the universe repositories:

```
sudo nano /etc/apt/sources.list
```

Then update and install needed packages:

```
sudo apt-get update
sudo apt-get install x-window-system-core xorg xserver-xorg xserver-xorg-video-vesa
```

At last install a WM to your liking (I suggest Fluxbox):

```
sudo apt-get install fluxbox
```

If you have an nVidia or an ATI card you can easily install your drivers with EnvyNG:

```
sudo apt-get install envyng-gtk
envyng -g
```

---

