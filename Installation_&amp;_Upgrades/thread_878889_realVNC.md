---
title: "realVNC ?"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by rhendrix9 on 2008-08-03
I setup ubuntu 7.04 in a virtual setup using vmplayer.
Somewhere/how I got/installed realvnc vncviewer i don't remember the details.

Anyway, I decided to get a little more serious, so I repartioned my drive and installed 8.04 on a partition.  

I've been able to set everything back up like I want it, except for realvnc.
(I need to connect to windows pc's runing vncserver)
I tried to "alien"  the rpm but it said int work but I'll be damed if i know where it put it!i tried the terminsl server (after update for vnc) but it says libraries a missing.

Should I go back to 7.04 or where did the alien->rpm->deb put realvnc?

---

### Post by rhendrix9 on 2008-08-05
is anybody familiar with VNC?

---

### Post by redraiderbum on 2008-08-05
I'm not very familiar with vnc in linux, but you could try XDMCP as an alternative.  You can use the Xming client to access your XDMCP linux box in windows:

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

Fortunately XDMCP is actually built in to linux.  All you so do enable it is go to the system menu and find the 'login screen' option.  You can also just use a command line and type:

sudo gdmsetup

Both will take you to the same place.  You go to the 'Remote login' tab and choose 'Same as local'.  Also, there is a bug in the current ubuntu so you will want to go the system menu and find the 'sound' option so you can uncheck the box that say 'ESD Sound'.  

That should be it.  All you do now is install Xming on a windows box, choose XDMCP login, type in the ip address of the linux box and you should get a full login screen.  The nice thing about XDMCP is multiple people can log on to different accounts at the same time.  It is much like windows terminal services.

---

### Post by maybeway36 on 2008-08-05
Are you trying to install the client or server on Ubuntu?

---

### Post by redraiderbum on 2008-08-05
That is a good question, I may have jumped the gun.

---

### Post by rhendrix9 on 2008-08-05
> **maybeway36 said:**
> Are you trying to install the client or server on Ubuntu?

I want to run vncviewer on ubuntu (not vncserver)
I have this in my virtual machine and i'm thinkin i didn't have to "find", the vitual machine is 7.04.  I think I'm gonna chunk 8.04 and go back to 7.04. (big sigh)

---

### Post by KatBuntu on 2008-08-05
I've changed VNC for FreeNX

---

### Post by andale on 2008-08-10
I'm trying to install a server on my ubuntu 8 install, I wanna use it from my windows desktop with realvnc.

---

