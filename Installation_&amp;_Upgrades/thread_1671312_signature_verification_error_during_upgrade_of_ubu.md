---
title: "signature verification error during upgrade of ubuntu 10.04 to 10.10"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by virupaksha swamy on 2011-01-19
when i was updating my ubuntu 10.04 using update manager i got the error
"W.A error occurred during the signature verification.
the post is not updated and teh previous index files are used .
GPG error: [http://deb.playonlinux.com](http://deb.playonlinux.com) lucid release.
can somebody help me pl's.. 
thanks in advance

---

### Post by zvacet on 2011-01-22
In terminal

```
gksudo gedit /etc/apt/sourcews.list
```


find line with [http://deb.playonlinux.com](http://deb.playonlinux.com) and replace **lucid **with **maverick**.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by zvacet on 2011-01-25
Now I see I posted wrong command,It is 

```
gksudo gedit /etc/apt/sources.list
```

---

