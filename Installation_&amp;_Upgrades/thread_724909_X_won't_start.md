---
title: "X won't start"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by RandomUsr on 2008-03-15
I have installed ubuntu-desktop on Gutsy Server
however, when I > startx I get

some erroneous errors, possibly due to missing libs or a config file issue.

one error has something to do with xauthority and the system's ability to access it, I believe there is a sym link that links to a missing directory and I had to manually create /etc/X11/X

also just a guess, but is it bad if /usr/bin/Xorg doesn't exist?

Please tell me what I've missed

Thanks

---

### Post by PmDematagoda on 2008-03-15
You will have to install the ubuntu-desktop packages since the Ubuntu Server ISO does not contain them by default.

---

### Post by RandomUsr on 2008-03-15
I thought I already installed the ubuntu-desktop packages?

Sure thought I did

---

### Post by zvacet on 2008-03-15
```
sudo nano -Bw /etc/apt/sources.list
```

add line 


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse

Ctrl+o  >Enter >Ctrl+x

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by RandomUsr on 2008-03-16
OK so

> 
xauth: creating new authority file /home/*CurrentUser*/.serverauth.4850
xauth: /home/*CurrentUser*/.Xauthority not wrietable, changes will be ignored
xauth:  error in locking Authority file /home/*CurrentUser*/.Xauthority
cannot read from /etc/X11/X  Symbolic Link [invalid argument], aborting 
xinit connection refused [errno 111]: unable to connect to xserver
xinit no such process [errno 3]: Server Error
xauth: error in locking authority file /home/*CurrentUser/*.Xauthority


What gives?

---

