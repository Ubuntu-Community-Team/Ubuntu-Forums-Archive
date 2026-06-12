---
title: "Installing softwares without synaptic manager"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by arpit625 on 2011-05-23
I have ubuntu 11.04 on my pc.....
i have downloaded some packages from :

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

when i extracted them they contain some config files....there was no .deb files...
how can i install softwares downloaded from this site..?????

I tried these commands but they didnt work:
./configute
make
make install

---

### Post by joshuachoo on 2011-05-23
You most likely have to install them through the command line (I hope you are familiar with this). Using the command line, navigate to the directory where you have extracted your installation files (there should be a file called "*configure"*). In that directory, type ./configure in the command line. If all goes well and no errors are reported, you should be able to do:
```
make
```
```
make install
```

Note: You may have to type *sudo* before each command to run with administrator privileges.

The *make install* should install the packages into your system. Some times other dependencies are required, which would be another problem depending on the packages you are trying to install.

---

### Post by arpit625 on 2011-05-23
i have tries these commands even with sudo .....
what are the other dependicies you are talking about.  ????

yeah actually the setup did start but after some times it says some other packages or something else are not found....
i think it the same thing u are talking about.....

How can this problem be solved ???

---

### Post by linuxinstalledfromhdd on 2011-05-23
If you are just trying to install software in general this might help:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by oldos2er on 2011-05-23
Which packages? Why aren't you using packages.ubuntu.com?

---

