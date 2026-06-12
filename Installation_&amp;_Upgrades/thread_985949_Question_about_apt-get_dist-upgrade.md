---
title: "Question about apt-get dist-upgrade"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by lotharz0r on 2008-11-18
Hi.
I am about to do a update on a ubuntu based server.
If I do a apt-get update, and an apt-get dist-upgrade, will I get the newest available distrobution?
The server has installed the official version from before 8.04.
If I do the dist-upgrade, will my installation be upgraded to 8.10?

---

### Post by inobe on 2008-11-18
yes, that will get you upgraded to 8.10


if you want to upgrade package just do

```
apt-get upgrade
```

---

### Post by Partyboi2 on 2008-11-18
If you are upgrading a server version of ubuntu then you can follow [[COLOR=Blue]this[/COLOR]]("http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29")

---

### Post by lotharz0r on 2008-11-18
Great! I used the **do-release-upgrade** command and it worked like a charm.
Is this a ubuntu-specific command, or is this a command I can use on debian servers as well?

---

