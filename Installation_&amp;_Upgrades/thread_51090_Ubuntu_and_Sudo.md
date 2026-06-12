---
title: "Ubuntu and Sudo"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by sprucio on 2005-07-22
Is there a way to get rid of sudo in Ubuntu as well as gksudo and other similar packages for desktops?

Is there a well documentation that I can read on how the first user (that is created during install) gets all the appropriate admin priviliges?

---

### Post by DJ_Max on 2005-07-22
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Look at the bottom for "Enabling the root account"

---

### Post by damonw5 on 2005-07-22
Also try: [http://ubuntuguide.org/#usersadministration](http://ubuntuguide.org/#usersadministration)

---

### Post by sprucio on 2005-07-24
Is it just me or does anyone else find this to be mighty annoying?

I've tried using Ubuntu now twice and had to resort back to Debian.

I honestly wish that there was a way to disable this from the installation.

---

### Post by codejunkie on 2005-07-24
[QUOTE=sprucio]Is it just me or does anyone else find this to be mighty annoying?

I've tried using Ubuntu now twice and had to resort back to Debian.

I honestly wish that there was a way to disable this from the installation.[/QUOTE]

i've tried i dont think that theres a way to remove it from the default installation i just enable the root account, remove the sudoers file and edit my .desktop files that use ```
gksudo
``` to use ```
gksu
``` like debian. but you might be able to do it by doing an expert install and just install the gnome or kde packages manually and leave out ubuntu-desktop and kubuntu-desktop packages it might work.

---

### Post by Xian on 2005-07-24
[QUOTE=sprucio]Is it just me or does anyone else find this to be mighty annoying?[/QUOTE]
Heh. I've actually started using sudo on my other distros.
It really does make sense for a number of reasons.

But I can understand it can take some getting used to....  ;-)

---

### Post by charlieg on 2005-07-24
I've quickly grown to like sudo.  I even accidentally started typing 'sudo -s -H' on my Gentoo box!

---

### Post by DJ_Max on 2005-07-24
[QUOTE=sprucio]Is it just me or does anyone else find this to be mighty annoying?

I've tried using Ubuntu now twice and had to resort back to Debian.

I honestly wish that there was a way to disable this from the installation.[/QUOTE]
By default OS X/Darwin is the same way. I've also setup my Debian server the same way, since it makes sense if you're worried about security. Honestly, is it that big of a fuss? It doesn't take much to change it. :???:

---

