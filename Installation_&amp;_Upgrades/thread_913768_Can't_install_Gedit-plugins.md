---
title: "Can't install Gedit-plugins"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by siDDis on 2008-09-08
I get this error message when I do sudo apt-get

```

olav@Gosling:/usr/bin$ sudo apt-get install gedit-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gedit-plugins (2.22.2-0ubuntu1) ...
/var/lib/dpkg/info/gedit-plugins.postinst: 6: gconf-schemas: not found
dpkg: error processing gedit-plugins (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 gedit-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)
olav@Gosling:/usr/bin$ 

```

What is wrong?

---

### Post by Sef on 2008-09-08
What version of Ubuntu are you using?

---

### Post by b0n60 on 2008-09-08
hi siDDis please chack if you have the right repository, it seems like the error is in the version of it... try out to overwrite the old repo with a new f.ex.  # Hardy
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Multimedia
##deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) unstable main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

# Debian Unstable & Experimental
#deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) unstable main contrib non-free
#deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) experimental main contrib non-free

right?
hope that helped 
sry for my bad english ;)
gr33tz b0n60

---

### Post by siDDis on 2008-09-09
I found out what was causing the error, I had installed an old version of Python manually and this caused linking errors.
I had to manually fix the link to the default python installation for Ubuntu

---

