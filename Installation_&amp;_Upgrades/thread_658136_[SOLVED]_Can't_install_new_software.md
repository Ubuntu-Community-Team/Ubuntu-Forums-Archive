---
title: "[SOLVED] Can't install new software"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by Bandolin on 2008-01-04
Using Ubuntu 7.10. I launch Add/Remove, I find the software I want, I click on the check box next to the software I want and all I get is the Refresh or Cancel dialog box.

It won't let me download any new software. I've followed the instructions twice and still I can't install new software. I downloaded the software manually and installed it manually, but now its sitting on my desktop and not conveniently in the applications menu.

Can someone help me?

---

### Post by forestpixie on 2008-01-04
what do you get if you do this in a terminal

```
sudo apt-get update
```

Edit - before you post the result - do this as well ```
cat /etc/apt/sources.list
```

if that has # on every line except one that starts deb cdrom

read this thread first

[http://ubuntuforums.org/showthread.php?t=653781](http://ubuntuforums.org/showthread.php?t=653781)

---

### Post by Bandolin on 2008-01-04
:) Solved

Thank you. You redirected me to exactly the right solution. I have no understanding of what I did, but it seems like a permissions thing I guess.

---

### Post by forestpixie on 2008-01-04
no - if you needed to follow the thread to sort the problem - it was due to a net problem during installation - the repos couldn't be verified so they are stopped from working 

or at least that is what I've surmised

as to what you did
> 
cat /etc/apt/sources.list

printed your sources.list - which is a list of places the system goes to download software, you can add other 3rd party sources as well, but it's probably good practice to make sure you know the source
> 
gksudo gedit /etc/apt/sources.list

gedit is one of the text editors in ubuntu, sudo is superuserdo (I think), means that you have temporary rights to administrate your system - in this instance you're editing a system file, gksudo is used when you're sudoing with a graphical application - got that from psychocats - link in my sig

apt-get, like aptitude, add/remove and synaptic are methods of getting software onto the system - apt-get and aptitude work in the terminal and are generally quicker to explain and use

> sudo apt-get update - update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the   location(s) specified in /etc/apt/sources.list - got that from the manual

> sudo apt-get upgrade

upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded

descriptions for apt-get update and upgrade from manual page 

if you wanted to read the man page in a terminal you can
> 
man apt-get

Hope that helps - and if there are glaring errors - perhaps someone could say so if they see it - and educate me too :D

---

