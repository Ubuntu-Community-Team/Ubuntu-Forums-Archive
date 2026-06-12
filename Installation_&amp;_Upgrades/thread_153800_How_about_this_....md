---
title: "How about this? ..."
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by vr04 on 2006-04-01
Is the following possible?

When installing Ubuntu, just do a server install, then do sudo apt-get install gnome (and gdm). Would that give me a system with just gnome installed without all the other stuff? Would I have a GUI?

Another question: I searched in Synaptic, and noticed that a package called "gnome" is not even installed. What's that about?

---

### Post by Sef on 2006-04-01
Gnome is the default install, so it would not be listed in synaptic.

> When installing Ubuntu, just do a server install, then do sudo apt-get install gnome (and gdm). Would that give me a system with just gnome installed without all the other stuff? Would I have a GUI?

What other stuff are you talking about?  If Gnome is installed, everything with it is installed. And yes you would have a gui.

---

### Post by xmastree on 2006-04-01
Gnome is listed as **gdm** in synaptic. GDM = Gnome Desktop Manager.

And yes, it is possible to do a server insall and then apt-get install gdm

---

### Post by vr04 on 2006-04-01
[QUOTE=Sef]What other stuff are you talking about?  If Gnome is installed, everything with it is installed. And yes you would have a gui.[/QUOTE]
I'm talking about stuff like OpenOffice, Firefox, Gaim, etc.

---

### Post by aysiu on 2006-04-01
The *gnome* package is not Gnome, believe it or not. It's a metapackage with the full description: > **The GNOME Desktop Environment, with extra components**
This is the GNOME Desktop environment, a graphical interface to use on your Debian system. It includes a wide range of applications, including programs for email, messaging, word processing, financial accounting and more. If you use Ubuntu's Gnome, *this* Gnome package will *not* be installed.

GDM is not Gnome either. It's the Gnome Display Manager and has this description: > **GNOME Display Manager**
gdm provides the equivalent of a "login:" prompt for X displays- it
pops up a login window and starts an X session.

It provides all the functionality of xdm, including XDMCP support for
managing remote displays.

The greeting window is written using the GNOME libraries and hence
looks like a GNOME application- even to the extent of supporting
themes! By default, the greeter is run as an unprivileged user for
security. You do not need to have GDM to have Gnome installed. It is the login screen manager, basically. You can have Gnome installed with KDM (KDE Display Manager)--I do right now. Gnome and GDM are independent of one another.

In answer to the original question, it wouldn't install Gnome with "all that other stuff," but it would install Gnome with a lot of *other* other stuff. In other words, doing ```
sudo apt-get update
sudo apt-get install gnome gdm
``` would not just install the gnome base system--it would install a bunch of other crap, too--just not *Ubuntu's* other crap.

Same difference applies to the *kde* package as opposed to the *kubuntu-desktop* package. *kde* has a lot more crap than *kubuntu-desktop* actually.

---

### Post by vr04 on 2006-04-01
Thanks aysiu. I think I understand things a bit better now... maybe.

Is it safe to say that even if you build GNOME from source, it'll install a bunch of "other things," since those are a part of the GNOME environment?

---

### Post by aysiu on 2006-04-01
Building from source will just mean you're building from source--it doesn't change what *packages* you're using.

For example, if I build Thunderbird from source or if I apt-get install Thunderbird--either way, I'm installing Thunderbird.

Unfortunately, as far as I can tell, Gnome doesn't have a package similar to *kde-core*, which is the essential KDE, no frills.

What I would do is type ```
sudo apt-get install ubuntu-desktop
``` At a certain point, it'll tell you *all* the packages to be installed. Then it'll ask if you want to go ahead and do it. Say **no**. Take note of the package names and write down the ones you think might be essential. If you're not sure if it's essential, leave it *in*. Then type ```
sudo apt-get install
``` and type out the names of the packages you want.

The truth is that if you're looking for a minimalist system, you don't want Gnome at all. You should do a server install and do ```
sudo apt-get update
sudo apt-get install x-window-system-core icewm menu synaptic xterm
```

---

