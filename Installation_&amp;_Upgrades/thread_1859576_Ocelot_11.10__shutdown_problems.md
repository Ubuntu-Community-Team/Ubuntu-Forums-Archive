---
title: "Ocelot 11.10  shutdown problems"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by rad_sci_guy on 2011-10-14
I've installed it on my desktop, laptop and netbook and all three have an issue with shutdown taking forever (a few minutes).  They do eventually shutdown but when I press escape I see that ubuntu is having trouble killing running processes.  :(

Any fix?

---

### Post by dino99 on 2011-10-14
sadly no one fix it

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

---

### Post by robert shearer on 2011-10-14
This page of the thread on the oneric testing forum may be of help...
[http://ubuntuforums.org/showthread.php?t=1853484&page=3](http://ubuntuforums.org/showthread.php?t=1853484&page=3) [COLOR="Red"]post #25[/COLOR]

this fix worked for me...
[http://ubuntuforums.org/showpost.php?p=11317856&postcount=27](http://ubuntuforums.org/showpost.php?p=11317856&postcount=27)

In a terminal type ```
gksu gedit  /etc/init/network-manager.conf
```

and then add the line..
stop on runlevel [6]

so it looks like this...

> # network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description	"network connection manager"

start on (local-filesystems
	  and started dbus)
stop on stopping dbus
stop on runlevel [06]
expect fork
respawn

exec NetworkManager


save and close. 
You might need to log out and in or reboot.

---

