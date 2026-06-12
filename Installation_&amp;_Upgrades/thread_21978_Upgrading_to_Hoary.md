---
title: "Upgrading to Hoary"
date: 2005-03-24
forum: Installation &amp; Upgrades
---

### Post by Icarus315 on 2005-03-24
Hi, I'm relatively new to Linux and have installed Warty 4.10 on my machine.  I've read in the Ubuntu overview that releases are every six months and it's possible to upgrade vs reinstalling the entire system.

My question is, how do you perform this update?  I'm using KDE as my desktop environment (Version 3.2.3), will that be upgraded to KDE 3.4 automatically as well?

---

### Post by poofyhairguy on 2005-03-25
[QUOTE=Icarus315]
My question is, how do you perform this update?  I'm using KDE as my desktop environment (Version 3.2.3), will that be upgraded to KDE 3.4 automatically as well?[/QUOTE]

In the konsol type:

sudo pico kwrite /etc/apt/sources.list

change every word that says Warty into Hoary.

hit control (key) plus x to exit and save.

type this into consol:

sudo apt-get update

sudo apt-get dist-upgrade

You will get KDE 3.4 automatically.

---

### Post by Icarus315 on 2005-03-27
Well, I did the apt-get dist-upgrade and while it was upgrading apt-get quit with an error that mentioned having a broken pipe to one of it's subprocess'.  It suggested that I try it again using the -f option which I did and it got a bit farther before it encountered the same error.  This time using the -f option had no effect, it was simply hung up.  Luckily I had only just installed warty so it was no big loss - the drive was practically empty.  So what I did was reinstall warty and immediately used apt-get dist-upgrade to move over to hoary.  Once that was done I then added kde3.4.  So it wasn't perfect, but all in all Ubuntu is still pretty sweet.

---

