---
title: "Pidgin in Ubuntu Repositories"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Redenbacher on 2008-03-05
Pidgin is releasing new updates rather consistently, however Synaptic still shows only 2.2.1 and I am now compiling 2.4. It would be nice if the update manager would update pidgin just like it does everything else, even wine, which I find to be less important to the typical user than pidgin.

Perhaps there is just something wrong with my install, but I've never seen pidgin upgraded through the update manager even though synaptic says 2.2.1 is installed, while I am running 2.4.

---

### Post by Oldsoldier2003 on 2008-03-05
> **Redenbacher said:**
> Pidgin is releasing new updates rather consistently, however Synaptic still shows only 2.2.1 and I am now compiling 2.4. It would be nice if the update manager would update pidgin just like it does everything else, even wine, which I find to be less important to the typical user than pidgin.

Perhaps there is just something wrong with my install, but I've never seen pidgin upgraded through the update manager even though synaptic says 2.2.1 is installed, while I am running 2.4.

The repos are locked with the stable version of the app when the OS is released. only security upgrades and other urgent things come down the pipeline. Be sure you lock your packages after you  install your newly compiled pidgin, lest update manager bug you about it and try to DOWNGRADE your pidgin.

[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)

---

### Post by imtheguru on 2008-03-05
Deb packages available at [http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

---

### Post by zvacet on 2008-03-05
You can add getdeb as repository 

```
gksudo gedit /etc/apt/sources.list
```

add this line

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Save and close file.

```
sudo apt-get update
```

---

