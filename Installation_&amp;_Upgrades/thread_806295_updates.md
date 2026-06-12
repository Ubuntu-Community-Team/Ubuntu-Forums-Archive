---
title: "updates"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by zezerbing on 2008-05-24
Hello. I  upgraded to new release and I'm having some problems. 1) when I try to load updates I get error message.' dpkg interrupted, manually configure-a " I tried to figure it out in the terminal. 2)  whenever a site opens a flash screen it shuts down my browser 3) is there any up dates for totem. thanks

---

### Post by Partyboi2 on 2008-05-24
What happened when you ran
```
sudo dpkg --configure -a
``` in a terminal?

---

### Post by zezerbing on 2008-05-25
Illegal instruction
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess post-installation script returned error exit status 132
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (= 6b09-0ubuntu2); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
Setting up openssh-client (1:4.7p1-8ubuntu1.2) ...

dpkg: dependency problems prevent configuration of icedtea-gcjwebplugin:
 icedtea-gcjwebplugin depends on openjdk-6-jre (>= 6b06); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea-gcjwebplugin (--configure):
 dependency problems - leaving unconfigured
Setting up ssh-askpass-gnome (1:4.7p1-8ubuntu1.2) ...

Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-gcjwebplugin
The first couple of times I got nothing, now I get all this.BTW.When I downloaded the updated verson when it came out I got errors at the end about some packages not working or something. but other than that the upgrade has been working.

---

### Post by zvacet on 2008-05-25
```
sudo dpkg --configure openjdk-6-jre-headless
```

```
sudo apt-get update
```

---

### Post by zezerbing on 2008-05-25
It worked, thanks.

---

### Post by zezerbing on 2008-06-24
You helped me with updates, but I'm still having this message:E: openjdk-6-jre-headless: subprocess post-installation script returned error exit status 132
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: icedtea-gcjwebplugin: dependency problems - leaving unconfigured.         I can update but I get this message all the time.Thanks.

---

