---
title: "Install as server but with gnome?"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by KristianThrane on 2005-10-04
Hello,
Being a linux n00b I have a couple of n00b questions :)
I want to use my ubuntu as webserver (lamp) and choose install as "server".
Now - as I am not that into text-commandos - I would like to have a GUI like Gnome and synaptic for packages installed: 
How is this done from the terminal, which is my desktop for now? And how do I boot into this after install? :)
Best regards
Kristian, Denmark

---

### Post by Hairy_Palms on 2005-10-04
sudo apt-get install gnome-core
sudo apt-get install gdm
sudo apt-get install xserver-xorg
and sudo apt-get install gnome-common 
the package names might not be spelt right as im doing this from memory

---

### Post by SilentCacophony on 2005-10-04
Hello. If it's just package management you want, you could try **aptitude**, which gives a pretty nice text ui to work with, and you could use **mc** for a nice text ui for file management and editing.

You could also use xfce4 or any number of windowmanagers as a lighter, graphical alternative to gnome.

**sudo apt-get install ubuntu-desktop** will get the whole gnome desktop installed, if you don't mind the space it'll take.

---

