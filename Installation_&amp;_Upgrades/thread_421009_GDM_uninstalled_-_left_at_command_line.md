---
title: "GDM uninstalled - left at command line"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by ManSizeRooster on 2007-04-24
Hi,

I've recently installed 7.04 on my new laptop, and had it all configured and working nicely, but then made the completely dumb move of apt-get remove gdm.

I now can only log in via command line, and have no idea how to reinstall gdm - network devices/connections do not seem to have been mounted/initialised.
The options that I can see are installing the package from my LiveCD, but I can't find the package on it, or starting up a network connection and apt-get install gdm.


Can anyone tell me the location of the GDM installer on the LiveCD, or how to initialise a nework connection from scratch via command line?

Thanks!

---

### Post by lassegs on 2007-04-24
If you have a wired connection, go like this.

```
sudo ifup eth0
```
This should get your wired network connection online using DHCP (automatic IP). Then you just
 sudo apt-get install gdm

If this doesnt cut it, please post the output of 
```
sudo ifconfig
```

---

### Post by mpvano on 2007-04-24
Another approach might be to try typing "startx" into the command line after you login. If the only thing removed was gdm, this may start up your gnome desktop and allow you to fix things from a more familiar environment.

hope this helps,

Mario

---

### Post by bwhite82 on 2007-04-24
I think you may have inadvertently removed the entire desktop meta-package, of which is dependent on GDM.

---

### Post by zvacet on 2007-04-24
```
sudo aptitude gdm
```

---

### Post by ManSizeRooster on 2007-04-24
> **mpvano said:**
> Another approach might be to try typing "startx" into the command line after you login. If the only thing removed was gdm, this may start up your gnome desktop and allow you to fix things from a more familiar environment.

hope this helps,

Mario

When I try the X command, X starts and I get a screen without any functionality, and the 'X' cursor.

I'm going to try the ifup command when I get home. I'll let you all know how I got on.

---

### Post by ManSizeRooster on 2007-04-26
Ifup command worked like a charm, thanks everyone for your help.

I've now only gone and misconfigured my xorg.conf file, so much fun and hilarity is to be had getting X up again...

---

