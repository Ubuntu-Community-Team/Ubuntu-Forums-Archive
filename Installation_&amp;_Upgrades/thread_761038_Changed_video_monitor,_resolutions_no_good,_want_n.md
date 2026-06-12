---
title: "Changed video monitor, resolutions no good, want new xorg.conf"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by wb0gaz on 2008-04-20
This problem has troubled me for several releases of Ubuntu, although I've found work-arounds that are cumbersome.

Now I'm on Ubuntu 7.10/Gnome (standard desktop install), and following a change to video monitor, I am constrained by the resolution(s) of the previous monitor. This is such a common situation (changing the monitor) that I was hoping the replacement monitor would be auto-detected, and everything would fall into place.

So my question is this - what is the recommended procedure to rebuild xorg.conf so it is aware of the new monitor and it's capabilities?

Thanks,

Dave

---

### Post by Rocket2DMn on 2008-04-20
You can run the following command to autoreconfigure X
```
sudo dpkg-reconfigure xserver-xorg -phigh
``` then do CTRL+ALT+BACKSPACE to restart X.  Otherwise you may need to configure manually by removing the -phigh flag.  If you need further help, post
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

