---
title: "installing virtualbox?"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by bots on 2009-11-29
> @-desktop:~$ sudo dpkg -i ~/a.deb
(Reading database ... 141833 files and directories currently installed.)
Unpacking virtualbox-3.0 (from /home//a.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /home//a.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /home//a.deb
@-desktop:~$ 

lsof /var/cache/debconf/config.dat
shows nothing

what's happening? how can I install virtualbox?

---

### Post by sakisds on 2009-11-29
It seems that something else is using /var/cache/debconf/config.dat, or its locked for a reason. I am not sure about this, you can try running "tasksel" and installing "Virtual Machine Host" from there. I think this will install Virtual Box.

---

### Post by GnubbyaBush on 2009-11-29
restart, make sure no other programs running. go to synaptic file manager search for virualbox and install, maybe that will solve the problem. Now it you want to be able to use USB through virtualbox you must go to their website and get the full version that suppots it, dowload the .deb and run it. I think its a deb file..maybe gtk.

---

### Post by bots on 2009-12-01
none of that has worked but don't worry about it...

---

### Post by baniasad on 2009-12-01
> **sakisds said:**
> It seems that something else is using /var/cache/debconf/config.dat, or its locked for a reason. I am not sure about this, you can try running "tasksel" and installing "Virtual Machine Host" from there. I think this will install Virtual Box.

in my country i cant download this link (maybe filtered)
[B]Forbidden 
Your client is not allowed to access the requested object.  [/B]
 
can anyone upload these links in  file hosting websites such as rapidshare.com etc.. 
[http://download.virtualbox.org/virtualbox/3.1.0/virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_i386.deb](http://download.virtualbox.org/virtualbox/3.1.0/virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_i386.deb) 
[http://download.virtualbox.org/virtualbox/3.1.0/VirtualBox-3.1.0-55467-Win.exe](http://download.virtualbox.org/virtualbox/3.1.0/VirtualBox-3.1.0-55467-Win.exe)
thanks

---

