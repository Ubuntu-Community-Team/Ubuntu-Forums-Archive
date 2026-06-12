---
title: "VirtualBox Start up error GLib-GIO:ERROR"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by william2011 on 2011-10-16
After installed successfully,in terminal typed VirtualBox, it has the following error
  
# VirtualBox ** GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL) Aborted   

[http://s7dhansh.wordpress.com/category/comp/linux/](http://s7dhansh.wordpress.com/category/comp/linux/) i use chmod +x ed.sh then ./ed.sh VirtualBox, then no response
  ubuntu 11.04 and virtualbox-4.1

---

### Post by dino99 on 2011-10-16
you may have followed a wrong way to install it:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

sudo apt-get install synaptic
sudo synaptic

purge all the installed virtualbox packages first (complete removal). Then add the source url (into synaptic source tab) to update the packages, and finally install virtualbox package.

---

### Post by william2011 on 2011-10-16
i follow [http://askubuntu.com/questions/66765/how-to-install-virtualbox-4-1-4-in-ubuntu-11-04-fluently](http://askubuntu.com/questions/66765/how-to-install-virtualbox-4-1-4-in-ubuntu-11-04-fluently)

similar to your link

after tried your way, tell you later

---

### Post by william2011 on 2011-10-16
in synaptic, i paste 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
[FONT=Verdana]in repository-> other software -> add
then reload
[/FONT]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. if available an older version of the failed index will be used . Otherwise the reposiory will be ignored. Check your network connection and ensure the respository address in the preferences is correct 

unable to find expected entry 'contrib/source/Sources' in release file (Wrong sources.list enry r malformed file) some index file failed to download. The have been inored or old noes used instead.

---

### Post by dino99 on 2011-10-16
what you needs:

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib

not natty as you have done (if you are really using 11.04 of course)

---

### Post by william2011 on 2011-10-17
using 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric contrib

same error

---

### Post by william2011 on 2011-10-18
:p This link give the same error, how to do?

---

