---
title: "How do i switch from Ubuntu 10.04 to Xubuntu 10.10"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by campb.andrew on 2010-12-08
Hey all,

I'm new to Ubuntu and I've been trying to work this out on my own but I'm stuck.

I recently installed Ubuntu yesterday and finally got all the settings right so that it would run rather decently on my computer. I have rather limited RAM resource, 192MB to be exact and i would have preferred to have installed Xubuntu from the start, but kept getting errors when using Wubi in Windows XP. 

So here i am, with Ubuntu 10.04, wanting to upgrade to Xubuntu 10.10....but not knowing what to do. I'm currently installing the desktop environment for Xubuntu via the Software Manager but I'm not sure if this is what I'm supposed to do.....

HELP! Please?:oops:

---

### Post by oldfred on 2010-12-08
I do not know wubi. Not sure if this will work or not.

Normal installs let you install any desktop you want. I once installed kubuntu desktop but then decided to go back and had real issues housecleaning all the new K files.

Change apt-get install to desktop you want:
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install [COLOR=Red]ubuntu-desktop[/COLOR]
sudo /etc/init.d/gdm restart
sudo service gdm start

---

### Post by campb.andrew on 2010-12-08
I'll try the install i just did of the xubuntu desktop environment and let you know what happens.

---

