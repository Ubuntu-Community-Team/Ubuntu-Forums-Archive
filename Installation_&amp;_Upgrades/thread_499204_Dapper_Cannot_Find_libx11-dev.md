---
title: "Dapper Cannot Find libx11-dev"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by cworley420 on 2007-07-12
We have just installed the server version of dapper and following a how to on installing vmware.
[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

The problem we have ran into is we cannot install libx11-dev and some other x11 libs.  I can find the package at packages.ubuntu.com under dapper but, apt-get cannot find them.

In /etc/apt/sources.list we have
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

Again we have the server version installed.  I remeber having problems getting X11 installed on the server release before, so i was thinking we might need to start with the desktop install.

Come on guys, I hate windows and this is our first linux box at this company.  We will be using it in our dev enviroment.  So, don't let me have egg on my face  ;)   kidding, i know there is a simple solution.

-chris worley

---

### Post by cworley420 on 2007-07-12
Also, if there is another how to with fiesty or an easier approach let me know.

---

### Post by cworley420 on 2007-07-12
Solution sollved.  

I added universe at the end of the lines in sources.list  and then i ran apt-get upgrade

the second step is what i left out when doing things.

Since our admin is new to linux we are going to go back and install the desktop so, he will have everything he will need.

---

