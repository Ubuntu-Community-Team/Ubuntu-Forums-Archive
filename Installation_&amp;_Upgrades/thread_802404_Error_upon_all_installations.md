---
title: "Error upon *all* installations"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by ftpvk on 2008-05-21
When I installed ubuntu 8.04, I decided to remove several programs that I did not need and while doing it got this error:

Setting up ekiga (2.0.12-0ubuntu2) ...
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-mastermind (0.3-1) ...
dpkg: error processing gnome-mastermind (--configure):
 subprocess post-installation script returned error exit status 139
Setting up sound-juicer (2.22.0-1ubuntu2) ...
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
Setting up tomboy (0.10.1-1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 ekiga
 gnome-mastermind
 sound-juicer
 tomboy
E: Sub-process /usr/bin/dpkg returned an error code (1)

They were not deleted, and I always get the same error while installing or removing totally different software no matter if I am using add/remove, synaptic or the sudo apt-get install / remove...

Thanks in advance,

---

### Post by zvacet on 2008-05-21
```
sudo dpkg --configure -a
```

---

### Post by ftpvk on 2008-05-22
did not work still get the same error

---

### Post by zvacet on 2008-05-22
```
sudo apt-get -f install
```

---

### Post by ftpvk on 2008-05-23
unfortunately I still get the 139 script error...

---

