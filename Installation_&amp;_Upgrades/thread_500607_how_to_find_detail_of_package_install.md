---
title: "how to find detail of package install"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by fire-fly on 2007-07-14
Hi pple
I am new to ubuntu. How can find out the details for package install ?
In rpm, I can execute "rpm -ql whatever". 

thanks in advance
Fire-fire

---

### Post by apoth on 2007-07-14
Perhaps

```
sudo aptitude show packagename
```

?

---

### Post by ajgreeny on 2007-07-14
For packages already installed use synaptic, and in the settings>properties menu dialogue set to "show package properties in the main window"  This will give you plenty of info about those already installed, including all the files and where they are.  For those not yet installed you get the same info less the files installed and where they are.

If you just want general info on what packages are available for ubuntu (and other linux distros) have a look at [http://linuxappfinder.com/](http://linuxappfinder.com/)

---

### Post by fire-fly on 2007-07-14
> **apoth said:**
> Perhaps

```
sudo aptitude show packagename
```

?

Thanks, not really what I am expecting, I want to know there the lib, shared doc etc is location. RPM can do i believe can be done in ubuntu too.

---

### Post by fire-fly on 2007-07-14
> **ajgreeny said:**
> For packages already installed use synaptic, and in the settings>properties menu dialogue set to "show package properties in the main window"  This will give you plenty of info about those already installed, including all the files and where they are.  For those not yet installed you get the same info less the files installed and where they are.

If you just want general info on what packages are available for ubuntu (and other linux distros) have a look at [http://linuxappfinder.com/](http://linuxappfinder.com/)

Thanks
looking for command line version, linux or unix has becoming too dependent on gui

---

### Post by fire-fly on 2007-07-15
Hey pple
thank you the help. Found the solution, is a debain package manager, dpkg
e.g. 
dpkg -L apache
/etc/
/etc/apache
/etc/apache/conf.d
..
..
..

---

