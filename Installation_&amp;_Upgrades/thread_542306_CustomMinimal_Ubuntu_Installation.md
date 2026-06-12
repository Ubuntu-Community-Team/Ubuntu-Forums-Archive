---
title: "Custom/Minimal Ubuntu Installation"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by Nazgulled on 2007-09-03
I like Ubuntu, it allows me to have a nice linux system without having to waste lots of time configuring and installing  everything but I also like to have some control over my system and right now, I don't have that over Ubuntu.

Why? Because the default installation install lots of packages/software I don't care/need. For instance, GIMP, OpenOffice, Ekiga, Evolution, etc... These are the most noticeable.

What I want? Have a minimal Ubuntu installation. For instance, I use Gentoo and love how I only have installed what I need, however, I didn't want exactly to install a Ubuntu system and just have a command line. My ideal Ubuntu system with minimal installation, would need to have a base GNOME installation, from there, I want to install only what I really want.

About the base GNOME installation, I'm saying this because on Gentoo I can have a full GNOME installation or a base GNOME installation and I prefer that one and I don't know if Ubuntu as something like that.

So, how can I accomplish a custom Ubuntu installation like this?

---

### Post by Pumalite on 2007-09-03
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Nazgulled on 2007-09-03
That guide might help but it's more for people with low-end system, I want something more like the current desktop cd but with minimal package installation. I mean, installing like that won't probably give me the ubuntu themes for GDM and GNOME right and the framebuffer splash also and I wanted to have all those things but the desktop cd installs so many packages that I don't need...

Is there such guide?

---

### Post by Pumalite on 2007-09-03
If you have good hardware, why do you want a barebones installation?

---

### Post by Pumalite on 2007-09-03
This is light and has good support: [http://www.ubuntu.com/getubuntu/releasenotes/606](http://www.ubuntu.com/getubuntu/releasenotes/606)

---

### Post by kerry_s on 2007-09-03
> **Nazgulled said:**
> That guide might help but it's more for people with low-end system, I want something more like the current desktop cd but with minimal package installation. I mean, installing like that won't probably give me the ubuntu themes for GDM and GNOME right and the framebuffer splash also and I wanted to have all those things but the desktop cd installs so many packages that I don't need...

Is there such guide?

follow that guide, but for the install command use>
**sudo apt-get install xorg gdm gnome-core**

---

### Post by Nazgulled on 2007-09-04
> **Pumalite said:**
> If you have good hardware, why do you want a barebones installation?

I never said I wanted a barebones installation, in fact, I don't even understand the exact meaning of that word... the original post, clearly states why I want a minimal installation and has nothing to do with hardware supporting Ubuntu.

> **Nazgulled said:**
> Why? Because the default installation install lots of packages/software I don't care/need. For instance, GIMP, OpenOffice, Ekiga, Evolution, etc... These are the most noticeable.

That's the reason!

@kerry_s
Will see if that works as I want. Thank you both.

---

### Post by twinax on 2007-09-12
Hi Nazgulled
I am going to be using Ubuntu at work so there are many things I don't need as well.  Did you get answer about min installation?
Thanks
RS

---

### Post by Nazgulled on 2007-09-12
Never tried it... I opted to install Gentoo instead.

---

### Post by capink on 2007-09-26
The alternative approach it to install from live cd, then uninstall packages you don't want. This sounds like tedious job. But I made a [script]("http://ubuntuforums.org/showthread.php?t=442974") that will keep only the packages you want on your system. All you have to do is to supply the script with a list of the packages you are interested in.

---

