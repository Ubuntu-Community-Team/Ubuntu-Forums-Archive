---
title: "[SOLVED] Installing Xubuntu from Ubuntu"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by coolbrook on 2007-05-12
**From the web...**

[i][http://www.xubuntu.org/get](http://www.xubuntu.org/get)

**Install Xubuntu from Ubuntu**

If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic (or Adept if you use Kubuntu) and install the xubuntu-desktop package. There you are! Next time you login, you can choose Xubuntu from the Session menu on the login screen.[/i]


I referred to that documentation and it isn't working as expected.

I followed the instructions.  When the system restarts there is a Ubuntu splash page with progress bar then there is no Xubuntu option in the menu.  When the GUI loads up I see a Xubuntu login window.  When I log in it goes back to Ubuntu.  Should I resort to a Xubuntu Live CD installation to resolve this problem?

---

### Post by taurus on 2007-05-12
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by coolbrook on 2007-05-12
I'll give that a shot.   I didn't do the first line when I tried terminal.

---

### Post by coolbrook on 2007-05-12
OK so I tried that. Still no Xubuntu option in the first menu and the Ubuntu progress bar pops up. 

Following that I get the Xubuntu login page.  I change the session to Xfce and I achieve my goal except I don't have a network connection.  I guess that it doesn't support my wireless NIC out of the box like Ubuntu does, so I'll read on.

---

