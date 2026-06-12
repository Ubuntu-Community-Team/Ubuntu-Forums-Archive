---
title: "Updating R?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by dgoodin on 2010-06-08
I am trying to update my installation of the R statistical program from V2.10 to 2.11.  I have run sudo apt-get install r-base, and get back a message saying that the most recent version is installed.  However, when I open the program it is still 2.10.  I need 2.11 in order to install some new packages.  Any ideas?  I am a relatively new Ubuntu user (transitioning from Windows) and still struggle a bit with software installation.  Thanks.

---

### Post by squaregoldfish on 2010-06-08
The 2.11 release of R hasn't been added to the repositories.

I would suggest that you uninstall the version from Synaptic, and download the latest copy from the R website - they have .deb files specifically for Ubuntu.

Download the ones you need, and install them using:
```

sudo dpkg -i <file>.deb
```

Steve.

---

### Post by mi_di on 2010-06-08
I actually prefer to use R repositories. You can see a list of mirrors here:

[http://cran.r-project.org/mirrors.html](http://cran.r-project.org/mirrors.html)

And then just add the repository to your list of software sources by adding the following line to /etc/apt/sources.list

```

deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu lucid/

```

The advantage is that they more or less keep the pace with newer R versions while ubuntu repositories are normally one version behind.

---

### Post by squaregoldfish on 2010-06-09
mi_di's suggestion is much better than mine. I didn't know about that trick...

Steve

---

