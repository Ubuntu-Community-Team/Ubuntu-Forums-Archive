---
title: "Configuring wireless encryption Kubuntu"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by Waxer on 2005-09-07
Kubuntu installed great on a partition of a Dell Inspiron 6000.  For install purposes, I turned off security on my wireless network to ensure I got updates and stuff when installing...all good.

So, booted into Kubuntu for the first time, installed additional apps, auto updated itself via the wireless link, no probs, logged in, all working, got on the net no probs, all hardware OK etc.

I logged into my router from the laptop to reactivate the security (128 bit WPA), did so, then tried to use the KDE config app for wifi to get online again...no can do, says I may have to login as root for encryption issues in the manual, so I finished the session, and tried to login as root but it asks for a password and I did not set one during install...if I need to do this to set the wireless encrption, how do I do it?  Or is there some other way?  Thanks a lot all...

---

### Post by mlomker on 2005-09-07
By default the root password is the same as your regular user's password.  If KDE prompts you then just type it in.  Kwifimanager pretty much bites, imo.  If you are comfortable with the command line then take a look at wpa_supplicant and ifplugd.  You can get them through apt-get and Google will provide plenty of how-to's.

---

