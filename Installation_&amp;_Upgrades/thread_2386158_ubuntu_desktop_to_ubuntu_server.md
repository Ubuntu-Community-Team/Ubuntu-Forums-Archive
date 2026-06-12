---
title: "ubuntu desktop to ubuntu server"
date: 2018-03-01
forum: Installation &amp; Upgrades
---

### Post by bijupp on 2018-03-01
Is it possible to convert a ubuntu desktop to ubuntu server by installing server packages and uninstalling the other apps like open office, gimp etc.  The question looks funny.. but the reasons are follows
[LIST=1]
[*]I tried the installations in the real machine. not in virtual machine.  All most  all the tutorials are made with virtual machine installation in virtual machine is easy it doesnt require internet.
[*] I find installation of desktop is very easy just few settings but server needs more attention
[*]Desktop installation complete with in an hour but server installation needs internet connection and takes more time
[*]if any problem with internet connection then it will takes more time to install server..
[*]Both are using same linux kernal
[*]Iam able to install successfully the desktop version but server installlation requires additional drivers and ends up with some errors..pl. help
[*]
[/LIST]

Pl. clear my doubt

---

### Post by mg2003 on 2018-03-01
Yes, you should be able to do exactly what you're asking.

```

sudo apt-get install tasksel
sudo tasksel remove ubuntu-desktop
sudo tasksel install server
sudo apt-get update
sudo apt-get install linux-server linux-image-server
sudo apt-get purge lightdm
```

---

### Post by ajgreeny on 2018-03-01
It's not quite as simple and easy as mg2003 suggests.

Those commands will not remove as much of the full OS as you might think as the **ubuntu-desktop** package is not the full ubuntu OS but just a meta-package; it pulls in all the packages that make Ubuntu and removing it will remove only the **ubuntu-desktop** package itself, not all the rest of the OS.

It would be much easier to move from the server OS to the full GUI version of Ubuntu, but not so simple to do what you want.

---

### Post by SeijiSensei on 2018-03-02
I'd just install the server packages you need on top of the desktop installation.  My desktop has Apache, PostgreSQL, and a few other server packages installed for testing purposes.  (My real servers are in the cloud.)  

What services do you intend this machine to provide?  It might make answering this question easier.

---

### Post by bijupp on 2018-03-03
thank you for the replies

---

### Post by bijupp on 2018-03-03
> **SeijiSensei said:**
> I'd just install the server packages you need on top of the desktop installation.  My desktop has Apache, PostgreSQL, and a few other server packages installed for testing purposes.  (My real servers are in the cloud.)  

What services do you intend this machine to provide?  It might make answering this question easier.


I need postgresql, apache tomcat 8, samba server, ssh etc.

I tries to install server but only ended in blank screen,  I am able to control the server using ssh from another machine but i want to work from the same machine itself thats why I just seeking another option without losing much performance and I found it is easy to install desktop than server..

---

