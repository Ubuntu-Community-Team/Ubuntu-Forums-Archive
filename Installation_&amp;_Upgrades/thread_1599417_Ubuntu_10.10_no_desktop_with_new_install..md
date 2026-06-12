---
title: "Ubuntu 10.10 no desktop with new install."
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by DarkDancer on 2010-10-17
I just installed Ubuntu 10.10 and on first boot I get these errors. 

> Could not update ICEauthority file /home/username/.ICEauthority

> There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

> Nautilus could not create the following required folders: /home/username/Desktop, /home/username/.nautilus

Before running nautilus, please create these folders or set permissions such that Nautilus can create them.

How do I fix this, tried rebooting and reinstalling.

---

### Post by DarkDancer on 2010-10-21
Never mind I am so beyond this now....

---

### Post by timur_ba on 2010-10-25
I deleted the initial user and then created a new one. The same problem appeared, as described here.

---

### Post by timur_ba on 2010-10-26
There is a discussion on [http://www.uluga.ubuntuforums.org/showthread.php?t=1558636](http://www.uluga.ubuntuforums.org/showthread.php?t=1558636), but that's not what I did. 
Previously, I created a new user with "useradd" and it didn't create home folder. With "adduser", home folder was created and everything went fine.

---

