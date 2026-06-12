---
title: "How do I uninstall a deb package (non repository)"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2008-08-26
How do I please uninstall a Virtual Box package that I installed as the system does not seem to know of its existence when I try to run it from a terminal, saying that it is not installed. When I run the deb package with Gdebi it says it is already installed but I cannot find it anywhere. Where should I look for the command to start it please.

---

### Post by nbayiha on 2008-08-26
Go look for the  package in synaptic and remove it from there.

---

### Post by spiderbatdad on 2008-08-26
perhaps in usr/bin
```
usr/bin/package_name
```
Have you tried locate?
```
sudo updatedb
locate package_name
```

---

### Post by Julian David Pitt on 2008-08-28
The programe name is "Virtualbox_1[1].6.4-33808_Ubuntu_hardy_i386.deb", do I need to search for that or will Virtualbox suffice? If I then find it how do I actually uninstall it? Thanks.

---

### Post by Julian David Pitt on 2008-08-28
When I run the code > julian@Hardy:~$ sudo updatedb 
I am returned to the prompt after about 20 seconds
When I run > locate Virtualbox
I get
**julian@Hardy:~$**
I can see a folder called Virtualbox in /usr/bin, is that where it is installed. what should I be typing to start the program? Thanks

---

### Post by kerry_s on 2008-08-28
> **Julian David Pitt said:**
> When I run the code 
I am returned to the prompt after about 20 seconds
When I run 
I get
**julian@Hardy:~$**
I can see a folder called Virtualbox in /usr/bin, is that where it is installed. what should I be typing to start the program? Thanks

when you install virtualbox you need to log out and back in, then there will be a menu entry in system tools to launch it.

yes, from commandline it's: VirtualBox or VBox

---

