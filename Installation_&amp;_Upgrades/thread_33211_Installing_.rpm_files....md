---
title: "Installing .rpm files..."
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by YourSurrogateGod on 2005-05-09
How would you do that? is there a special command for that? To be more specific, I woud like to install VNC (allows you to access you computer from another machine) and Bochs (an x86 hardware simulator) on my machine.

---

### Post by bored2k on 2005-05-10
```
sudo apt-get install alien ; sudo alien -d filename.rpm
sudo dpkg -i newfile.deb
``` That is how you do it. Isnt ther a .deb for vnc? yes there is.

---

### Post by YourSurrogateGod on 2005-05-16
[QUOTE=bored2k]```
sudo apt-get install alien ; sudo alien -d filename.rpm
sudo dpkg -i newfile.deb
``` That is how you do it. Isnt ther a .deb for vnc? yes there is.[/QUOTE]
What's ".deb"?

---

### Post by Kimm on 2005-05-16
.deb is the file format for Debian package files ;-)

---

### Post by YourSurrogateGod on 2005-05-16
[QUOTE=Kimm].deb is the file format for Debian package files ;-)[/QUOTE]
Yeh I just noticed that. Bochs seems to be working ok, now I just need to get vnc firing on all cylinders.

---

### Post by YourSurrogateGod on 2005-06-08
How would you un-install previous packages?

---

### Post by az on 2005-06-08
[QUOTE=YourSurrogateGod]How would you un-install previous packages?[/QUOTE]

If you installed them with alien, they are in the dpkg database.  Use synaptic.

packages.ubuntu.com

Look for packages from the official repositories there.   Bochs and vnc are there...
You do not need any of this alien crap.

---

### Post by YourSurrogateGod on 2005-06-08
[QUOTE=azz]If you installed them with alien, they are in the dpkg database.  Use synaptic.

packages.ubuntu.com

Look for packages from the official repositories there.   Bochs and vnc are there...
You do not need any of this alien crap.[/QUOTE]
If I were to install the new packages from packages.ubuntu.com,  would that overwrite the existing ones? The thing is when I wanted to uninstall the bittorrent client that I installed today, it said that it would get rid of gnome-bittorrent as well as gnome-desktop and I don't want to do that, so I'm wondering if that will get overwritten.

---

