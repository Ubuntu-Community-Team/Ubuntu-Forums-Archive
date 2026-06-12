---
title: "Symantic package manager"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by Eycks on 2007-09-03
How do I find where the Symantic package manager puts the files it downloads? I think I have successfully downloaded Tomcat but I need to set the environment variable CATALINA_HOME to the Tomcat installation directory?  Does the package manager have log files and where do I find them?

---

### Post by forestpixie on 2007-09-03
they go here 

/var/cache/apt

they get installed generally in /bin or /usr/bin I believe

to find something use whereis in a terminal

```
whereis something
```

---

### Post by rainwalker on 2007-09-03
In Synaptic, go to the package you installed, right-click and choose "Properties", and go to the "Installed Files" tab. That lists all of the places things were installed.

---

