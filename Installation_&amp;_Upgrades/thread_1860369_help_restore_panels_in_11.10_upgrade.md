---
title: "help restore panels in 11.10 upgrade"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by eaglemystic69 on 2011-10-14
Help restore my panels.

I upgraded from 11.04 to 11.10 and lost access to my panels on the desktop.  I can get to my new 11.10 desktop, change background and surf thru folders and files.  I no longer have panels menus to to search for applications, or see open windows/trash/time/etc.  

I have attempted terminal commands:
Not in the order necessarily. . . 

apt-get autoremove
sudo apt-get clean
unity --reset
sudo apt-get install gdm ubuntu-desktop
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get install gnome-session-fallback (newest version installed)

Tried sudo synaptic and received. . .E: 'Lucid' is invalid APT. . .

---

