---
title: "vncserver will not automatically start"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by zuehls on 2013-03-04
I can run vncserver manually but when I reboot it does not automatically start.  It was working in the past but just stopped.  Here's some of the things I've checked:

1.  I've used update-rc.d to remove and readd its config (sudo update-rc.d vncserver defaults)
2.  I've checked /etc/init.d/vncserver is executable
3.  I've checked ~/.vnc/xstartup is executable
4.  When I run vncserver start manually there are no errors and it starts properly...but after a reboot it never starts.

What can I do to troubleshoot this?  I cannot find any logs anywhere.  I have many other services that auto-start properly.

thx

---

### Post by zuehls on 2013-03-04
I made some progress.  I renamed the startup script in /etc/init.d/vncserver to servervnc.  Of course I removed it and readded it with update-rc.d and now it works.  Another thing I tried was renaming it to vnc and it fails again...weird.

---

### Post by MAFoElffen on 2013-03-04
Hmmm. That is strange... 

*** Maybe , even though you found a work-around, that you should report this as a "bug" to launchpad for someone there to look into it. Not going to get resolved there if they "don't" know about that. That way it can work for you and others as it's installed by default/how it's supposed to work.

---

