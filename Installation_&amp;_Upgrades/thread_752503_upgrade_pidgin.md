---
title: "upgrade pidgin"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by darkthunderfx on 2008-04-11
*I run Kubuntu*

I want to upgrade my pidgin, is there a way I can have this automatically done with adept updater?

---

### Post by petzworld999 on 2008-04-11
There is a very website called [GetDeb]("http://getdeb.net") that has up-to-date packages. Just go there, search for Pidgin, download the file, execute it, and you are good to go. That's how I updated my Pidgin.

---

### Post by zvacet on 2008-04-12
You can add getdeb as repository if you want to 

```
kdesu kate /etc/apt/sources.list
```

add line    

    deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Save and close.

```
sudo apt-get update
```

---

