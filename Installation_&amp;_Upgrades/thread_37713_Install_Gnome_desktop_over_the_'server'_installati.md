---
title: "Install Gnome desktop over the 'server' installation"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2005-05-28
Hello All! Is there a chance to install the graphical Gnome desktop+all libraries required to run it over the system installed with the 'server' switch?
Thank you!

---

### Post by Kamping_Kaiser on 2005-05-28
Installing "ubuntu-desktop" using apt-get thus
sudo apt-get install ubuntu-desktop 
will give you a gnome desktop. if you deside you want kde, go for
sudo apt-get install kubuntu-desktop

---

### Post by PryGuy on 2005-05-29
Thank you but I can't install the package directly typing: > sudo apt-get install ubuntu-desktop it says there are dependency problems, but I can install it this way:> sudo apt-get install ubuntu-desktop
sudo apt-get -f install  And this works somehow. But the question is, how do I run the graphical desktop after that, 'cause there's no gdm and startx returns errors, saying:> xinit:  Connection refused (errno 111):  unable to connect to X server 
xinit:  No such process (errno 3):  Server error.                      
I'm sure one has to configure X first, but I don't know how. Please explain me this...

---

### Post by FrankVaLi on 2005-05-29
sudo apt-get install xserver-xorg  xserver-common gdm

...should do it, I believe.

---

