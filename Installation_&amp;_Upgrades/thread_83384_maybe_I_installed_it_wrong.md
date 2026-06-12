---
title: "maybe I installed it wrong"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by Snitz on 2005-10-28
I ran the ubuntu cd, type <server> and pressed enter and let it all install
now when it loads, it doesn't login into a graphical system, it's in a prompt like DOS

what did I do wrong in the installation?

---

### Post by Kyral on 2005-10-28
You asked for the Server install ;P Which is quite barebones.

You can A) reinstall completely or B) login and use Apt to pull in the rest

I'd go the second way because its much more fun IMO :D

Anyway login

and depending on if you want KDE, GNOME, or XFCE excute the following command

```
For GNOME
sudo apt-get install ubuntu-desktop
``` 
```
For KDE
sudo apt-get install kubuntu-desktop
``` 
```
For XFCE
sudo apt-get install xubuntu-desktop
``` 
If you don't know what those mean, just use the first one. Then just reboot when its done (it will take a while) and you should be at the GUI.

The terminal ain't scary. *points to the link below*

---

### Post by kalin on 2005-10-28
I guess you installed the server version. It comes with no GUI, since it's not needed on server setups.

If you want a desktop there are two options:

1) reinstall (do not type "server" this time)
or 2) apt-get install ubuntu-desktop

I would recommend the 1st option, if possible, it will probably take care better of your Ubuntu desktop configuration...

---

### Post by kalin on 2005-10-28
Heh, Kyral beat me to it :)

---

