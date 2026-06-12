---
title: "Pure LXDE borked xsession autologin"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by BoredOutOfMyMind on 2010-11-27
Installed 10.10 Ubuntu and found the Dell D820 did not digest Gnome that easily.   I tried adding Lubuntu from repos after adding PPA.  Seemed unstable to use, so I followed Psychocat direction for Pure LXDE and removed Ubuntu.  

Now login is giving error "xsession:unable to launc "openbox-gnome" X Session --- "openbox-gnome" not found; falling back to defaultsession."  :o
Where do I correct the xsession login to allow auto login. (I know the chances for autologin, and still choose to use it) ;)

---

### Post by mikewhatever on 2010-11-28
If you get the login screen after that, change the default session there.

---

### Post by BoredOutOfMyMind on 2010-11-28
> **mikewhatever said:**
> If you get the login screen after that, change the default session there.

I want to skip the login screen and go directly to LXDE desktop. In Gnome it is found System> Preferences > Login.  My system has no gnome anymore so I cannot alter. 

How do you set autologin for the xsession using LXDE?

---

### Post by mikewhatever on 2010-11-28
You should be able to correct the default session at the login screen and worry about how to autologin later. In case you get loggedin straight into lxde, just logout.

---

### Post by BoredOutOfMyMind on 2010-11-28
> **mikewhatever said:**
> You should be able to correct the default session at the login screen and worry about how to autologin later. In case you get loggedin straight into lxde, just logout.

You are not answering the question on how to autologin to LXDE.  I do not want other sessions and do not want to use the login screen.

---

### Post by mikewhatever on 2010-11-28
Hm, it looks like I misunderstood the original question. Anyway, since you use gdm, the default login manager, the very same configuration utility should work. Try opening it with 
**gksudo gdmsetup**

---

### Post by cavalier911 on 2010-11-28
This applies if your running **LXD**isplay**M**anager
```
sudo nano /etc/lxdm/default.conf
```
autologon=*your.username*
session=_/usr/bin/startlubuntu_<-Lubuntu 10.04 not sure with PureLXDE

---

### Post by BoredOutOfMyMind on 2010-11-29
> **cavalier911 said:**
> This applies if your running **LXD**isplay**M**anager
```
sudo nano /etc/lxdm/default.conf
```
autologon=*your.username*
session=_/usr/bin/startlubuntu_<-Lubuntu 10.04 not sure with PureLXDE

Thanks for the help!

:p

---

### Post by kuric on 2011-10-27
Yep, thank you, it worked! 
So, in order to complete the answer above, this is how to set a default lxde session in Lubuntu 11.10 Oneiric Oncelot:

$ sudo leafpad /etc/lxdm/default.conf

Make this changes:
## default session or desktop used when no systemwide config
#session=/usr/bin/startlubuntu
**session=/usr/bin/startlxde**

---

