---
title: "Problem with packages"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by aekalex on 2005-09-23
hallo im a newbie.i tried to install ubuntu linux but in the installation i had some problems.some packages couldn't set up and they are remained unconfigured.what should i do to complete the installation?
the pachages are:
gnome-gv
hpi js
gs-common
ijsgimpprint
pnmzppa
python2.4-geoip
ubuntu-desktop
gnome-themes
mozilla-firefox
foomatic-db-hpi js
mozilla-firefox-gnome-support
python-geoip
foomatic-dp-gimp-print
yelp

thanx if someone helps

---

### Post by fordfan753 on 2005-09-23
```
sudo apt-get -f install
```

---

### Post by aekalex on 2005-09-23
where should i write that code?i log in the desktop but then it crashes and i can do nothing.

---

### Post by fordfan753 on 2005-09-23
Press Control + Alt + F1
This will log you into a terminal session.
Log in with your username and password.
Type the command "sudo -f install"
This should correct the problems you're having

---

### Post by aekalex on 2005-09-23
i do what u say but it does nothing.it says corrupted filesystem tarfile for some files like dpkg    and in the end it says error code 1.

---

### Post by fordfan753 on 2005-09-23
ouch!...I don't exactly know what it's doing, try..
```
sudo apt-get update
``` 
first, then the other command...

---

### Post by aekalex on 2005-09-23
now i think it doesn't crashes.it must be a problem with the mouse.the coursor is not moving!!!!!!

---

### Post by fordfan753 on 2005-09-23
try
```
sudo dpkg-reconfigure xserver-xorg
``` 
xorg is what handles a lot of your I/O stuff like mice, keyboards, and monitors

---

### Post by aekalex on 2005-09-23
](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

nothing really works!!!!
i dont know what to do....

---

### Post by RagingFuryBlack on 2005-09-23
[QUOTE=aekalex]](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

nothing really works!!!!
i dont know what to do....[/QUOTE]
 Are you working on hoarty or breezy?  If its breezy, download a copy of the hoarty hedgehog, as breezy isn't a full stable releace yet.  Also, if you are on hoarty, your iso may have been corrupt during install.  Try reburning it at a slower speed (I generally burn at 16x)

---

### Post by aekalex on 2005-09-23
ok ill try burning the cd again.But does anyone know what error code 1 is???
usr/bin/dpkg     error code 1!!!!

---

### Post by aekalex on 2005-09-23
i see that many users have the same problem with the mouse!do u think its a bug?i hope someone who knows better will help

---

