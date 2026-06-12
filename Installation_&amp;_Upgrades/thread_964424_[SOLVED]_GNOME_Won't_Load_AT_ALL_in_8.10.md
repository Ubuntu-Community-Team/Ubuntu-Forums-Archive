---
title: "[SOLVED] GNOME Won't Load AT ALL in 8.10"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-10-30
everything works ok except one little thing, I can't get my desktop to load! I tried the live cd, wubi, and a traditional install, nothing works. After I log on, i get a black screen with a mouse in the middle. please help! i have no idea.

---

### Post by martrn on 2008-10-31
Do you fully see the login prompt via x11 ?

Try logging in to a terminal (or booting up in rescue mode) and type:

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

See if there is anything starting up that will cause a problem
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```
and remove any unecessary services.

If you think you might have some problems with X11 try:
```
dpkg-reconfigure x-server x-org
```

Err there might be other things.

---

### Post by andrewwg94 on 2008-10-31
> **martrn said:**
> Do you fully see the login prompt via x11 ?

Try logging in to a terminal (or booting up in rescue mode) and type:

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

See if there is anything starting up that will cause a problem
```

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```
and remove any unecessary services.

If you think you might have some problems with X11 try:
```
dpkg-reconfigure x-server x-org
```

Err there might be other things.

Thank you very much it worked, but could you explain what exactly those commands did?

---

### Post by martrn on 2008-10-31
> **andrewwg94 said:**
> Thank you very much it worked, but could you explain what exactly those commands did?

Err I can try :

> **martrn said:**
> 
Try logging in to a terminal (or booting up in rescue mode) and type:
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

See if there is anything starting up that will cause a problem


Compiz is a plug in for the windows manager that provides illusion-ary 3D effects such as spinning cubes, fading Xwindows, wobbly effects and other 3D illusionary effects for the gnome desktop.

Sudo runs a program as root and "apt-get remove compiz" removes this package which can cause problems or lockups in the 3D card or the X11 windowing system.

> **martrn said:**
> 
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf[/CODE]
and remove any unecessary services.


Everything on linux is a file and in your /etc/init.d/ directory you will have a bunch of init scripts that will run on boot.  Sudo will run a program as root and "sudo apt-get install sysv-rc-conf" installs a package called sysv-rc-conf.  When you run sysv-rc-conf (as root) you will be able to modify your /etx/init.d/ directory in a structured way.  Removing advanced power modules and screen saver effects can stop X11 or Xorg from crashing sometimes.

See [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491") for more info.


> **martrn said:**
> 
If you think you might have some problems with X11 try:
```
sudo dpkg-reconfigure x-server x-org
```
Err there might be other things.

Everything in linux is a file (no registry).  Running the command "dpkg-reconfigure x-server x-org" reconfigure you X11 windowing system to provide a valid /etc/X11/xorg.conf which is required by the XOrg foundation - [http://www.x.org/wiki/]("http://www.x.org/wiki/").  Ubuntu sometimes shreds or produces an invalid Xorg file with BulletProofX.  So running this will produce a valid one and sometimes kick xorg into play.

Err thats all.

---

