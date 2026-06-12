---
title: "No desktop after Server install"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Unklebob on 2007-05-17
I installed the server version 7.04 from the ISO I downloaded and burnt to a CD. After the install completed I was prompted to login. I did with the user I created during the install and when I did I was sent to a command prompt.  How do I get to the Desktop/GUI??  Also how do I get the desktop/GUI  to load upon bootup/login??

Thanks!!

---

### Post by taurus on 2007-05-17
Server version is a command prompt so if you want Gnome window manager, you need to install it.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Unklebob on 2007-05-17
Thanks for the quick reply!!! Got it!!  2 more quick questions:

- Is the Gnome install package already on my hard drive or do I have to get it from the install CD or elsewhere??

- My intent for installing the server is to build an intrusion detection system (Snort/AIDE) for my network.  Is this the forum for questions about this or is t here another forum more appropriate??

Thanks again!!

---

### Post by mbradlcu on 2007-05-17
after the initial install, packages are mostly retrieved via package repositories using the apt-get command. these repositories are found in /etc/apt/sources.list . other sources can be added if needed.
have fun

---

