---
title: "[SOLVED] Can't uninstall Netbeans6.1 beta"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by danjones on 2008-11-12
I installed netbeans6.1 beta from a .deb file because the netbeans that was available to install via add/remove wouldn't allow me to create any projects or anything.

This all worked fine until I upgraded to Ubuntu 8.10 yesterday. Now when netbeans displays code, all the words overlap and I can't understand it. So I figured I'd uninstall it and download the newest version of netbeans.

But I can't uninstall it. I had a look on synaptic but the version of netbeans I have installed isn't there. I tried 
```
$ sudo apt-get --purge remove netbeans
```
but it doesn't seem to think netbeans is installed.

How do I uninstall it?

Thanks,
DanJ

---

### Post by prshah on 2008-11-12
> **danjones said:**
> I installed netbeans6.1 beta from a .deb file 

Locate the same netbeans .deb file; Use this file with dpkg; Eg```
sudo dpkg --remove netbeans.deb
``` (Or use "--purge" to remove netbeans new config files also)

---

### Post by danjones on 2008-11-12
problem is I can't remember what the full name of the .deb file was. I don't suppose theres  quick way to list all .deb packaged is there??

DanJ

---

### Post by prshah on 2008-11-12
> **danjones said:**
> problem is I can't remember what the full name of the .deb file was. I don't suppose theres  quick way to list all .deb packaged is there??


Open a terminal (Applications, Accessories, Terminal) and give the command
```
find ~ -iname *.deb
``` Assuming the file is saved somewhere in your home directory. If its not in the home directory, expand the search to search _all_ directories (Warning will take a long time)```
find / -iname *.deb
```

---

### Post by danjones on 2008-11-14
Ok, I've uninstalled. Thanks for the help.

---

