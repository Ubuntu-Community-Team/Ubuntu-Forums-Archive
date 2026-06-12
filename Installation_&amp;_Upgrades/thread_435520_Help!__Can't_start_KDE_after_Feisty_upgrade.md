---
title: "Help!  Can't start KDE after Feisty upgrade"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by anachreon_ on 2007-05-07
Hi all,

Usually, when I upgrade Kubuntu on my machine with a GeForce 7600 GT, I always get kicked to a TTY upon restart, where I have to reinstall the nVidia proprietary drivers using Alberto Milone's Envy script.  After that, things work peachy.

After upgrading to Feisty and rebooting, I was taken to a terminal rather than KDE, as usual.  I had already downloaded and installed the new version of Envy, so I cleaned the old install of the nVidia driver and installed it again.  However, KDE won't start now.  Here is all I get :

```

sudo :/etc/init.d/gdm: command not found
Stopping K Display Manager: kdm
Starting K Display Manager: kdm

```

It just leaves me at a command line.  

I tried reconfiguring my xorg.conf by running "sudo dpkg-reconfigure xserver-xorg, thinking some settings from Beryl might be messing things up, but this didn't help.

Can't think of what I messed up here.  I recall at one point the terminal says something about "--composite" being unrecognized.  Any ideas?  Any help GREATLY appreciated!

---

### Post by anachreon_ on 2007-05-07
Bump.

Anyone?

---

