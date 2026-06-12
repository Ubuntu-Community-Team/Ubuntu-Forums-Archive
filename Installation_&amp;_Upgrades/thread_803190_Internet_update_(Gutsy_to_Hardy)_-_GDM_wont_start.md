---
title: "Internet update (Gutsy to Hardy) - GDM wont start"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by DriftShin on 2008-05-22
So, i updated my Gutsy to Hardy using an internet update.I was waiting for it till about 4am when it finished and started installing the packages. I fell asleep and only woke up an hour later to find we had had a power failure. Booted the machine, no problem, was presented with the login prompt, no problem, login was a success.

Now thats where the problem is, GDM isn't starting. I can see the mouse pointer but nothing else. What do i do? Btw, grub is still showing me 7.10, not 8.04.

---

### Post by iaculallad on 2008-05-22
> **DriftShin said:**
> So, i updated my Gutsy to Hardy using an internet update.I was waiting for it till about 4am when it finished and started installing the packages. I fell asleep and only woke up an hour later to find we had had a power failure. Booted the machine, no problem, was presented with the login prompt, no problem, login was a success.

Now thats where the problem is, GDM isn't starting. I can see the mouse pointer but nothing else. What do i do? Btw, grub is still showing me 7.10, not 8.04.

Try this one (maybe caused by failed installation after that power failure):

Boot into recovery mode open your terminal:

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by trukulo on 2008-05-22
You can try also:

sudo aptitude reinstall gdm

---

