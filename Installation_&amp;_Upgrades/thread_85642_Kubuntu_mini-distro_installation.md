---
title: "Kubuntu mini-distro installation?"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by luxidio on 2005-11-03
I'm trying to install Kubuntu on an old disk (1Gb).

I've been able to install the server minimum core that works very well!!!:D 

The problem is that all the G/K/Xdesktop packages require not less than 1050Mb space for the installation!!!

Any idea on how to reduce the space required?
In other words how to install a basic kde wmanager and let it work with X properly???

Already tryed to install kdm but I was not able to go over the graphic kde login...

No solution found on the forums threads... 

Any suggestion??:confused: 

thank you all

---

### Post by az on 2005-11-03
sudo apt-get install x-window-system-core gdm xterm icewm mozilla-firefox menu synaptic


For just a barebones kde, try

sudo apt-get install x-window-system-core kdm konsole kdesktop konqueror kcontrol synaptic


A barebones kde will still run slow on old systems, where icewm (or xfce4) will fly...

---

### Post by luxidio on 2005-11-03
Thank a lot!!!

It works fine!

So, the secret is to install just the core of the packages and not the entire one (1Gb for X and Kde...)

Where do I can found additional details on the packages content (ful, core, etc..)?

Now I'm going to replace the HD with a MMC in order to have an old, silent, inexpensive server!!!

Hope to publish the results on the forum for all the people that want to customize their pc.

Salut, from France

---

### Post by az on 2005-11-03
Fire up synaptic and search through the packages.  You can enable the universe repository as well as others to enjoy thousands of additional packages.  You can get the informatino on the size by playing around.  

As for customising, you can go to the UserDocumentation page on the wiki (wiki.ubuntu.com) and take a look at the page that describes minimal installation.   You can perhaps add to that (those) page(s).


Bonne chance!

"Now I'm going to replace the HD with a MMC in order to have an old, silent, inexpensive server!!!"

How fast and how reliable is that?

---

