---
title: "Cryptkeeper doesn't launch in 14.04 Gnome"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2014-10-22
I recently upgraded from 12.04 to 14.04 using a something else install in which my / folder was formatted but my /home folder was intact, so my settings were preserved. It is not working according to plan though. On 12.04, I had whitelisted Cryptkeeper and my settings show that, but right now Cryptkeeper does not launch with the first click. It has to be clicked multiple times for the icon to appear on the top panel. This is happening in Nautilus as well as Nemo. I'm using Gnome Flashback Compiz.

Any help would be appreciated. Thanks in advance.

---

### Post by davit2 on 2014-10-22
Hi
Just run this in your terminal: gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

---

### Post by davy jones on 2014-10-22
It says - No such schema 'com.canonical.Unity.Panel

---

### Post by davit2 on 2014-10-22
try com.canonical.Gnome.Panel

---

### Post by davy jones on 2014-10-22
Same result :-(

---

### Post by davit2 on 2014-10-22
install dcont-tools, sudo apt-get install dconf-tools
run in terminal "dconf-editor"
and find the way to Panel
I don't have gnome environment in my PC, so i can't tell you the right way

---

### Post by davy jones on 2014-10-22
In the Panel option under Unity, Cryptkeeper is there, but it's not there in gnome-panel->layout. In the object-id list in this option I have 'menu bar' 'show desktop' 'window list' 'object 4' 'object 5' and so on.

I'm beginning to think that the problem is actually happening because my settings have been preserved from my earlier install but they haven't been implemented. In gconf-editor most of the keys have no schemas even though I can see that they're set to what I set them in my previous install.

---

