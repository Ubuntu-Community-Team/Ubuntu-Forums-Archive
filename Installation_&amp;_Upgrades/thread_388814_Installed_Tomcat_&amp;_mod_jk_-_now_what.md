---
title: "Installed Tomcat &amp; mod_jk - now what?"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by mvoorberg on 2007-03-19
I've got my machine running Tomcat though Apache but all the How-to's I've seen about Tomcat neglect to mention how to make Tomcat start when I reboot the machine.  Currently I need to start it manually but that's not a long term solution...

Also does it matter if Apache runs as root and Tomcat runs as me?  Is it worth changing?

BTW, my machine is setup to login as me automatically as it's as physically secure as the TV in my livingroom. ;)  

Thanks in advance,
Mark

---

### Post by mvoorberg on 2007-03-21
bump...

---

### Post by mvoorberg on 2007-04-12
Ok, I've found a simple solution to my own problem.  Since it took me a while to find it and I didn't see anything here that was nearly so simple I thought I'd share.

This works in my case 'cause the machine is already set to login automatically.  

Under [ Preferences -> Settings ] there's a tab called "Startup" just add the command used to start Tomcat.  It behaves exactly like the Startup menu group in Windoze.

---

### Post by jonathan_c on 2007-04-14
You could put it in /etc/rc.local if you want it to start even if you don't log into X

/etc/rc.local is a file that gets executed on boot-up

---

