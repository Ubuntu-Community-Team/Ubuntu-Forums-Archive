---
title: "Tomcat 6 Admin tools /manager/html"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Kismet on 2010-05-10
Tomcat 6 doesn't seem to be installing right for me, now that I upgraded to Lucid.

First it simply did not work, I assumed due to the change from JSVC to catalina.sh. 

So I removed, purged, and reinstalled everything.

No matter what I tried, /manager/html was not available.

Finally I manually put in a manager.xml in the /etc/tomcat6/Catalina/localhost/ directory pointing towards /usr/share/tomcat6-admin/manager

catalina.out says 
"May 10, 2010 12:06:38 PM org.apache.catalina.startup.HostConfig deployDescriptor
INFO: Deploying configuration descriptor manager.xml"

with no errors.

Now however, I cannot access it, it just sits and loads perpetually. It never asks for login or password. The catalina.out says nothing.

/docs and /examples work fine.  /manager /host-manager don't work.

---

### Post by lfsanmartin on 2010-05-18
Hello,  I'm new to Tomcat, and I have next problem that persists even after  having read the documentation. I took manager.xml file that came with the  installation and I have placed in CATALINA_HOME / conf.
It contains the following lines:

<Context  path = "/ manager"
DOCBASE = "/ usr/share/tomcat6-admin/manager"
antiResourceLocking  = "false" privileged = "true" />

By invoking the  application [http://localhost:8080/manager/list/](http://localhost:8080/manager/list/), I get a blank screen.
However if I add  the same line to the server.xml, everything works fine. Should not work the first setup? What am I doing  wrong?

Thanks

---

### Post by HDave on 2010-10-15
Did either of you get to the bottom of this?  I have the same issue...

---

### Post by mlzarathustra on 2011-05-25
Yes.  

For some reason, the web.xml file likes to get clobbered.  I was able to get it back by copying over the /manager directory from a clean install.

---

