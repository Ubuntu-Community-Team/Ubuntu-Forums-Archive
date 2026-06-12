---
title: "server or desktop?"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by sawatdee on 2008-08-02
I can find info about the desktop installation and the server installation. But what if I want both? I have one system and I need it to be my desktop system as well as a web server, MySQL server, print server, etc. I assume I would install the server version for that but I would rather know for sure before going through the whole process.

---

### Post by scragar on 2008-08-02
I'd install the desktop version, and after than install mysql-server etc.

it is possible to install the command line version(server), then install the desktop:```
sudo apt-get install ubuntu-desktop
``` but I wouldn't recomend that, since the desktop is a lot more packages that are also larger, and if your internet is not automaticly picked up it will be harder to get it working.

---

### Post by redraiderbum on 2008-08-02
I don't know if you've done it already, but I use to install the desktop and recently stopped.  The reason I started using the server version and simply adding the ubuntu-desktop is that I want all of my computers to have a LAMP, ssh, samba, and CUPS install.  It is true you can do that with the desktop install, but I have found for some reason with the server install the server pieces work together flawlessly.  Sometimes with a desktop install when you add things it just doesn't work as nicely.

I guess the bottom line is I try to install as little as possible, then I add on what I need later.

---

### Post by Sef on 2008-08-02
I second instlling the server and adding the desktop afterwards.

---

