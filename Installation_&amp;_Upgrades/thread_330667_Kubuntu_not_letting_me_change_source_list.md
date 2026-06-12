---
title: "Kubuntu not letting me change source list"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by Kinn on 2007-01-03
Hey everyone this is probably an easy fix.

I'm trying to set up kubuntu as a ftp, samba, and apache webserver (with openSSL, modSSL, PHP, and MySql) for my company.

I simply do not have permissions to write (or do anything rather) to my sources.list file. I used ubuntu a while back (badger i believe) and I know the source.list is needed to install packages, but I can't uncomment any of the lines. Speaking of that, could someone also tell me what lines I need to uncomment (or give me a source.list to copy/paste)?

---

### Post by ajgreeny on 2007-01-03
Try 
gksudo gedit /etc/apt/sources.list
in a terminal.  This will open the file as root and you can then change things as needed.

There are a few example sources.list files in the forum if you search, but you will need the right one for your version of ubuntu

---

### Post by Kinn on 2007-01-03
I'm using Kubuntu 6.06.1 LTS. gedit doesn't appear to work, whats the command in KDE?

---

### Post by kebes on 2007-01-03
In Kubuntu you can type in a terminal:
kdesu kwrite /etc/apt/sources.list

Or you can do it entirely in the terminal by going:
sudo nano /etc/apt/sources.list

(Ctrl+X to exit out of nano)

As to what you should uncomment, it depends on what you need. But if you want to be safe, you can uncomment all the lines that start "deb" (you usually don't need the "deb-src" lines). After saving changes, you can go:
sudo aptitude update

(and then "sudo aptitude install packageX" to install packageX or whatever)...

---

