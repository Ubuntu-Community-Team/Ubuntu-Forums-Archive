---
title: "Trouble installing Gnome in 10.04?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Shmook on 2010-05-02
Hi all; so I've just upgraded to 10.04 which seems to have gone smooth except I'm unable to install gnome -- my default is xfce and when I try to install gnome: 

through the update manager it basically gives me an generic error saying something about dependencies

and through Synaptic it says it requires swfdec-mozilla 'but it is not going to be installed'

then when I install that separately it says it requires epiphany-extensions but it is not going to be installed -- apparently these two packages delete each other on installation 

that's how it seems to me at least ~~ any ideas?

---

### Post by mk1w86 on 2010-05-02
Was Gnome already installed and the upgrade has failed or are you trying to install Gnome after upgrading because it wasn't installed before? :?

---

### Post by Shmook on 2010-05-02
That's what I thought was funny -- it was installed on 9.04 but isn't shown as being installed in synaptic or update man. also it's a choice at login screen but when selected goes straight to xfce :confused:

---

### Post by Shmook on 2010-05-02
Whoops I might have made a mistake...yeah chalk this up to idiocy; yeah nevermind there isn't a problem gnome is working -- but I'm still confused as to why it shows it not being installed in synaptic?? whatevah

---

### Post by mk1w86 on 2010-05-02
You could try running:

```
sudo aptitude install ubuntu-desktop
```

in case any packages are missing.

---

### Post by mk1w86 on 2010-05-02
> Whoops I might have made a mistake...yeah chalk this up to idiocy; yeah nevermind there isn't a problem gnome is working -- but I'm still confused as to why it shows it not being installed in synaptic?? whatevah

Out of interest, what was it you were doing wrong?  Also what is the name of the Gnome package that shows as not being installed?

---

### Post by tuxsun on 2010-07-19
> **mk1w86 said:**
> You could try running:

```
sudo aptitude install ubuntu-desktop
```in case any packages are missing.

 How does that command differ from:

```
sudo apt-get install ubuntu-desktop
```or does it?

---

### Post by mk1w86 on 2010-07-19
> **tuxsun said:**
> How does that command differ from:

```
sudo apt-get install ubuntu-desktop
```or does it?

Aptitude is a terminal based front-end for apt-get.  Historically aptitude had more features than apt-get although apt-get has caught up recently (Ubuntu is not planning to include aptitude on the LiveCD in Maverick :frown:).  Aptitude arguably still handles packages better and by running aptitude without any arguments:

```
sudo aptitude
``` 

you get a nice ncurses based UI which can be useful on machines without a GUI or Synaptic.

However, I think now it mainly comes down to personal preference.  For all intents and purposes, both commands do the same thing. ;)

---

### Post by tuxsun on 2010-07-22
@mk1w86 <-- Thanks for the explanation.

---

### Post by maximus3446 on 2011-03-24
I'm still having the same issue how did you fix it?

---

