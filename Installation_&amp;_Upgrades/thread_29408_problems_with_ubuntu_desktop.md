---
title: "problems with ubuntu desktop"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by freemanen on 2005-04-24
Then i am trying to start ubuntu it dosen't work.  then i start in console mode. And use dselect it say something with ubuntu-desktop and to configure. but ubuntu-desktop --configure dosen't work. and I see some errors with mozilla-firefox, mozilla-firefox gnome support and yelp to. then I try apt-get dist-upgrade it says "4 not fully installed or removed" and then it says E: Sub-process /usr/bin/dpkg returned an error code(1)

---

### Post by kelvinq on 2005-04-24
TOugh. You need to give out more details, like have you started X before? Or you met with the problem *immediately* after a fresh install?

And the complete error message.

Have you tried typing at console, "startx"?

---

### Post by freemanen on 2005-04-24
startx dosen't work 

here is screenshoots 
[http://min.mac.se/mikael.freeman/bild1.tiff](http://min.mac.se/mikael.freeman/bild1.tiff)
och
[http://min.mac.se/mikael.freeman/bild3.tiff](http://min.mac.se/mikael.freeman/bild3.tiff)

---

### Post by kelvinq on 2005-04-25
Your screenshots don't say much and we would need to know the error msgs that come with startx.

---

### Post by freemanen on 2005-04-25
startx say comand not found

---

### Post by az on 2005-04-25
You seem to have some missing packages.  Perhaps your cd was not intact.

Try:
sudo apt-get -f install

and see what gets installed.

It if complains about the packages not being okay on the cd, you will have ot get them from the net (are you connected?)

You will have to log in and edit the /etc/apt/sources.list file.

The first line should be the cd.  Put a "#" at the beginning of the line and then do
sudo apt-get update

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=azz]You seem to have some missing packages.  Perhaps your cd was not intact.

Try:
sudo apt-get -f install

and see what gets installed.

It if complains about the packages not being okay on the cd, you will have ot get them from the net (are you connected?)

You will have to log in and edit the /etc/apt/sources.list file.

The first line should be the cd.  Put a "#" at the beginning of the line and then do
sudo apt-get update[/QUOTE]



Then if that works put

sudo apt-get install ubuntu-desktop 

in terminal.

---

