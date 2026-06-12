---
title: "nvidia driver 177.80"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by RC84 on 2008-10-14
Hi I am trying to get my nvidia driver 177.80 installed and need a little help.

I have tried to install but got error saying cannot install, X Server is still running.  

Now I got the driver from nvidia's site as a package. I need to know how to stop this X Server and install the driver from the desktop.

somewhat new to Ubuntu as I got it to learn how to really get my feet wet with it as I feel its a very nice learning platform for me

---

### Post by Partyboi2 on 2008-10-14
To stop the xserver
```
sudo /etc/init.d/gdm stop
``` to start again
```
sudo /etc/init.d/gdm start
```

---

### Post by RC84 on 2008-10-14
ok that doesn't seem to be running now but I go to start the installer it says the "driver must be run as root"  what do I have to do now?

---

### Post by tuxxy on 2008-10-14
use a sudo at the beginning of the install command

```
sudo command
```

---

