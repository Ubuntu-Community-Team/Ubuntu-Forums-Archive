---
title: "Upgrade to Gutsy fails, Packages not fully installed"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by the_weekend on 2007-10-25
So, I tried to upgrade from 7.4 to 7.10 (Ubuntu 64) last night. I've ended up with some sort of dependency problem. If I get my 3 offending programs to force install or something it seems the rest of the upgrade should be able to finish:

Errors were encountered while processing:
 gdm
 fast-user-switch-applet
 ubuntu-desktop

I've tried the

> Try doing a combination of:

'sudo apt-get -f install'

'sudo dpkg --configure -a'

'sudo apt-get upgrade'
 from [http://ubuntuforums.org/showthread.php?t=580135](http://ubuntuforums.org/showthread.php?t=580135)

Here's some output that should help track down my problem:

```
ecbowen@lane:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gdm (2.20.0-0ubuntu6) ...
chown: changing ownership of `/var/lib/gdm/:0.Xservers': Permission denied
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdm
 fast-user-switch-applet
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

"chown: changing ownership of `/var/lib/gdm/:0.Xservers': Permission denied"
seems it might be of key importance...but I'm not sure.

---

### Post by the_weekend on 2007-10-25
So, to update, if this helps, I tried to fix packages in synaptic, and change the timezone as well (I assume this might have to do with permissions somehow?) 

I was looking at the file that the gdm config/upgrade seems to fail on:

```
sudo ls /var/lib/gdm/ -l
total 4
-rw-r----- 1 gdm gdm 45 2007-10-24 13:24 :0.Xauth
?--------- ? ?   ?    ?                ? /var/lib/gdm/:0.Xservers
```

What does this mean for my install? Can I delete/change permissions? Is the file corrupted & thus preventing my upgrade? 

Any ideas? Help please? (Man this forum is busy.)

---

### Post by the_weekend on 2007-10-25
So poking around on IRC I'm told the reason the gdm files are locking me out is because they're in use...but isn't GDM usually upgraded/configured while it's in use? Does anyone know if this should solve my problem? Shutting down X with an incomplete upgrade makes me nervous...but GDM probably needs to not be running when I try to upgrade.

Here's the last package manager command I tried to run: [http://paste.ubuntu-nl.org/42119/](http://paste.ubuntu-nl.org/42119/)

---

### Post by the_weekend on 2007-10-25
Alright, I'm on my rescue 7.04 disk and have chrooted into my install and the gdm file is really really broken and I really need to be able to delete it I think. Anyone please help?

---

