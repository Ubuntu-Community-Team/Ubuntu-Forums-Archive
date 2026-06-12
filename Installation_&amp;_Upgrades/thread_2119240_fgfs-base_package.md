---
title: "fgfs-base package"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by minerbog on 2013-02-23
Hi guys,

I made a complete c**k up today. I upgraded to flightgear 2.10. I also want new aircraft so I downloaded a few and installed them. Because the /usr/share/games/flightgear directory was a bit messy, I just started deleting stuff! DOH! I didn't realise it was part of the fgfs-base package!!!

So, here's where I'm at. The aircraft in the game won't load properly coz some numb-nut deleted stuff! And I can not re-install fgfs-base because it think's it's still there.

When ever I try and remove/re-install it with either apt-get of dpkg I get the following error and it just exit's.

```
Setting up fgfs-base (2.10.0-1~getdeb1) ...
ln: failed to create symbolic link `/usr/share/games/flightgear/Timezone': No such file or directory
dpkg: error processing fgfs-base (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 fgfs-base

```

Any idea's people??

Thanks,

Gavin.

---

### Post by MAFoElffen on 2013-02-23
> **minerbog said:**
> 
```
ln: failed to create symbolic link `/usr/share/games/flightgear/Timezone': No such file or directory

```
Any idea's people??

Gavin-

I've got a sort of off the wall idea...

It says it can't find '/usr/share/games/flightgear/Timezone'. Have you checked to see if it exists? What would happen if you manually create it then try? When it installs it should create a file 'zone.tab' in that directory. Other user's in the past just created it, then copied the file in from the github or from another user (from the flightgear forum).

The .deb... did you get it from the Ubuntu Flightgear ppa? Or from github?

---

