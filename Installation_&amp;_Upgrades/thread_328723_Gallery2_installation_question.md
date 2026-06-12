---
title: "Gallery2 installation question"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by mr.dad on 2006-12-31
I am building personal web server for photo sharing and have installed Ubuntu 6.10. Using the “Synaptic Package Manager, I have added apache2, php5, and mysql.  I have created a simple $HOME/public_html/index.html test page which I can access just fine from other PCs on my home network. 

The gallery2/README.html instruction page links to the index.php installation script. Attempting to follow this link gives a Firefox popup to open with a text editor or save it to disk. I think I want to run it.   What am I doing wrong?

---

### Post by Georges on 2007-02-04
you have to enable php:

```

sudo a2enmod php5
sudo apache2ctl stop
sudo apache2ctl start

```

---

