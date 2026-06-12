---
title: "tomcat and jenkins port 8080 conflict"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by edderd on 2011-11-23
I just upgraded Ubuntu 11.10 and the first thing I did was to install tomcat7 and then Jenkins via Synaptic. 

Tomcat works fine, but jenkins, installed as a standalone, wants to run on port 8080 and so does Tomcat. 

**What's the best way to switch one of the other to run on another port?**

Also I see that tomcat's defaults are at /etc/defaults/tomcat7 and I expected to see jenkin's defaults at /etc/defaults/jenkins, but that file does not exist. 

Where are Jenkins defaults? Not in (/etc/init.d/jenkins either)

---

### Post by MarioFuentes on 2011-12-16
See /etc/init/jenkins.conf

Bye!

---

