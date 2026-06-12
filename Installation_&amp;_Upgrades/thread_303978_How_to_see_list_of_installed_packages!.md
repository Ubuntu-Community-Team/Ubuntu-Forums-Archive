---
title: "How to see list of installed packages!?"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by ghepardo on 2006-11-21
I need a command (like apt-cache search) to browse my installed packages for a particular package, or a group of packages, to see if they are installed.

For example I wanna see what packages containing beryl in their name are installed, so exists some command that does that!?

---

### Post by jclmusic on 2006-11-21
would a search in synaptic package manager do the job?

---

### Post by ghepardo on 2006-11-21
> **jclmusic said:**
> would a search in synaptic package manager do the job?

there isn't a shell command for that !?

---

### Post by eeGhoong0ais on 2006-11-21
> **ghepardo said:**
> I wanna see what packages containing beryl in their name are installed, so exists some command that does that!?

```
dpkg -l '*beryl*'
``` is probably what you want. The man pages for dpkg and dpkg-query will tell you how to get different kinds of information.

---

### Post by ghepardo on 2006-11-21
That is exactly what I was searching for. Thank you.

---

