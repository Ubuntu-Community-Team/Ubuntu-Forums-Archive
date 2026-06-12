---
title: "Update stops with Python message and hang"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by kappel79x64 on 2011-03-25
Hello,

I was doing a update via Synaptic Package Manager, after it is nearly finished i get that message:

**Processing triggers for python-central ...**

Nothing happend so i ctrl-c it and the packet manger shows me no other errors or something else, even all the packages who was marked for upgrade are now upgraded but what about that python message? 

Do i have to do some check ? or maybe even a repair or even worse re install the OS?

dpkg.log

2011-03-25 13:25:32 startup archives unpack
2011-03-25 13:25:34 upgrade flashplugin-installer 10.2.152.27ubuntu0.10.10.1 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:25:34 status half-configured flashplugin-installer 10.2.152.27ubuntu0.10.10.1
2011-03-25 13:25:34 status unpacked flashplugin-installer 10.2.152.27ubuntu0.10.10.1
2011-03-25 13:25:35 status half-installed flashplugin-installer 10.2.152.27ubuntu0.10.10.1
2011-03-25 13:25:35 status half-installed flashplugin-installer 10.2.152.27ubuntu0.10.10.1
2011-03-25 13:25:36 status unpacked flashplugin-installer 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:25:36 status unpacked flashplugin-installer 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:25:36 upgrade software-center 3.0.7 3.0.8
2011-03-25 13:25:36 status half-configured software-center 3.0.7
2011-03-25 13:25:37 status unpacked software-center 3.0.7
2011-03-25 13:25:37 status half-installed software-center 3.0.7
2011-03-25 13:25:37 status triggers-pending shared-mime-info 0.71-3
2011-03-25 13:25:37 status half-installed software-center 3.0.7
2011-03-25 13:25:37 status triggers-pending desktop-file-utils 0.16-0ubuntu4
2011-03-25 13:25:37 status half-installed software-center 3.0.7
2011-03-25 13:25:37 status triggers-pending python-gmenu 2.30.4-0ubuntu1
2011-03-25 13:25:37 status half-installed software-center 3.0.7
2011-03-25 13:25:37 status triggers-pending gconf2 2.31.91-0ubuntu3.1
2011-03-25 13:25:37 status half-installed software-center 3.0.7
2011-03-25 13:25:37 status triggers-pending hicolor-icon-theme 0.11-1
2011-03-25 13:25:38 status half-installed software-center 3.0.7
2011-03-25 13:25:38 status triggers-pending man-db 2.5.7-4
2011-03-25 13:25:38 status half-installed software-center 3.0.7
2011-03-25 13:25:39 status half-installed software-center 3.0.7
2011-03-25 13:25:40 status unpacked software-center 3.0.8
2011-03-25 13:25:40 status unpacked software-center 3.0.8
2011-03-25 13:25:40 upgrade transmission-common 2.04-0ubuntu2 2.05-0ubuntu0.2
2011-03-25 13:25:40 status half-configured transmission-common 2.04-0ubuntu2
2011-03-25 13:25:40 status unpacked transmission-common 2.04-0ubuntu2
2011-03-25 13:25:40 status half-installed transmission-common 2.04-0ubuntu2
2011-03-25 13:25:41 status half-installed transmission-common 2.04-0ubuntu2
2011-03-25 13:25:42 status unpacked transmission-common 2.05-0ubuntu0.2
2011-03-25 13:25:42 status unpacked transmission-common 2.05-0ubuntu0.2
2011-03-25 13:25:42 upgrade transmission-gtk 2.04-0ubuntu2 2.05-0ubuntu0.2
2011-03-25 13:25:42 status half-configured transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:42 status unpacked transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:42 status half-installed transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:43 status half-installed transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:43 status half-installed transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:43 status half-installed transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:43 status half-installed transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:43 status half-installed transmission-gtk 2.04-0ubuntu2
2011-03-25 13:25:44 status unpacked transmission-gtk 2.05-0ubuntu0.2
2011-03-25 13:25:44 status unpacked transmission-gtk 2.05-0ubuntu0.2
2011-03-25 13:25:44 trigproc shared-mime-info 0.71-3 0.71-3
2011-03-25 13:25:44 status half-configured shared-mime-info 0.71-3
2011-03-25 13:25:45 status installed shared-mime-info 0.71-3
2011-03-25 13:25:45 trigproc desktop-file-utils 0.16-0ubuntu4 0.16-0ubuntu4
2011-03-25 13:25:45 status half-configured desktop-file-utils 0.16-0ubuntu4
2011-03-25 13:25:45 status installed desktop-file-utils 0.16-0ubuntu4
2011-03-25 13:25:45 trigproc python-gmenu 2.30.4-0ubuntu1 2.30.4-0ubuntu1
2011-03-25 13:25:45 status half-configured python-gmenu 2.30.4-0ubuntu1
2011-03-25 13:25:45 status installed python-gmenu 2.30.4-0ubuntu1
2011-03-25 13:25:45 status triggers-pending python-support 1.0.9ubuntu1
2011-03-25 13:25:46 trigproc gconf2 2.31.91-0ubuntu3.1 2.31.91-0ubuntu3.1
2011-03-25 13:25:46 status half-configured gconf2 2.31.91-0ubuntu3.1
2011-03-25 13:25:50 status installed gconf2 2.31.91-0ubuntu3.1
2011-03-25 13:25:50 trigproc hicolor-icon-theme 0.11-1 0.11-1
2011-03-25 13:25:50 status half-configured hicolor-icon-theme 0.11-1
2011-03-25 13:25:51 status installed hicolor-icon-theme 0.11-1
2011-03-25 13:25:52 trigproc man-db 2.5.7-4 2.5.7-4
2011-03-25 13:25:52 status half-configured man-db 2.5.7-4
2011-03-25 13:25:53 status installed man-db 2.5.7-4
2011-03-25 13:25:53 trigproc python-support 1.0.9ubuntu1 1.0.9ubuntu1
2011-03-25 13:25:53 status half-configured python-support 1.0.9ubuntu1
2011-03-25 13:25:54 status installed python-support 1.0.9ubuntu1
2011-03-25 13:25:54 startup packages configure
2011-03-25 13:25:54 configure flashplugin-installer 10.2.153.1ubuntu0.10.10.1 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:25:54 status unpacked flashplugin-installer 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:25:54 status half-configured flashplugin-installer 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:26:00 status installed flashplugin-installer 10.2.153.1ubuntu0.10.10.1
2011-03-25 13:26:00 configure software-center 3.0.8 3.0.8
2011-03-25 13:26:00 status unpacked software-center 3.0.8
2011-03-25 13:26:00 status unpacked software-center 3.0.8
2011-03-25 13:26:00 status unpacked software-center 3.0.8
2011-03-25 13:26:00 status half-configured software-center 3.0.8
2011-03-25 13:26:12 status installed software-center 3.0.8
2011-03-25 13:26:13 status triggers-pending python-central 0.6.15ubuntu2
2011-03-25 13:26:13 status triggers-awaited software-center 3.0.8
2011-03-25 13:26:13 configure transmission-common 2.05-0ubuntu0.2 2.05-0ubuntu0.2
2011-03-25 13:26:13 status unpacked transmission-common 2.05-0ubuntu0.2
2011-03-25 13:26:13 status half-configured transmission-common 2.05-0ubuntu0.2
2011-03-25 13:26:13 status installed transmission-common 2.05-0ubuntu0.2
2011-03-25 13:26:13 configure transmission-gtk 2.05-0ubuntu0.2 2.05-0ubuntu0.2
2011-03-25 13:26:13 status unpacked transmission-gtk 2.05-0ubuntu0.2
2011-03-25 13:26:13 status half-configured transmission-gtk 2.05-0ubuntu0.2
2011-03-25 13:26:13 status installed transmission-gtk 2.05-0ubuntu0.2
2011-03-25 13:26:13 trigproc python-central 0.6.15ubuntu2 0.6.15ubuntu2
2011-03-25 13:26:13 status half-configured python-central 0.6.15ubuntu2
2011-03-25 13:26:13 status installed software-center 3.0.8
2011-03-25 13:26:14 status installed python-central 0.6.15ubuntu2

---

### Post by zvacet on 2011-03-26
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by kappel79x64 on 2011-04-11
> **zvacet said:**
> ```
sudo dpkg --configure -a
sudo apt-get -f install
```


cheers and thx !

---

