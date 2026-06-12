---
title: "software-center crashes seconds after startup"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by ttime007 on 2013-01-24
Hi, I am seeing the below error when trying to start software-center.  Ubuntu 12.04

2013-01-24 16:48:43,960 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-01-24 16:48:43,964 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-01-24 16:48:44,351 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-01-24 16:48:44,542 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-01-24 16:48:44,891 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Illegal instruction (core dumped)

Already tried a couple of suggestons from the forums (apt-get update/upgrade, uninstall and reinstall software center, etc...) but no luck so far.  Any suggestions?

---

### Post by slickymaster on 2013-01-24
Try to uninstall it, clear up and install again the "software-center" with commands below, at a terminal window:

```
sudo apt-get purge software-center
rm -r .cache/software-center/
rm -r .config/software-center/
sudo apt-get install software-center ubuntu-desktop
sudo update-software-center
```

---

### Post by ttime007 on 2013-01-24
No luck with the above code.  Still the same error as before.  But thanks for your effort!

---

### Post by slickymaster on 2013-01-24
There's a known bug, first showed in 12.10-dev, that seems to also affect 12.04:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1000238](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1000238)

Besides that, the only thing I can think of is to try the following command:
```
sudo apt-cache gencaches make debianpkg
```

---

### Post by ibjsb4 on 2013-01-24
A temporary solution until you can get the software center working would be using another package manager.  In terminal:

```
sudo apt-get install synaptic
```[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en")

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by ttime007 on 2013-01-24
Thanks. i'll give synaptic a try.

---

### Post by nDman on 2013-04-16
I was have this problem too on Ubuntu 12.04, but after deleting this file:

```
dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en
```

from this folder:

```
/var/lib/apt/lists/
```

problem solved :)

---

