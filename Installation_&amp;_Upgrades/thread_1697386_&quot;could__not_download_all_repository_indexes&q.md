---
title: "&quot;could  not download all repository indexes&quot;"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by lunokhod on 2011-02-28
Hi I'm brand new to ubuntu I had an old laptop and a friend gave me a ubuntu version 8 i think instal disk and I'm trying to install from the add/remove applications it will usally get to about 44 then stop and come up the message "could not download all repository indexes" . I can't even get the current list of applications. Any help would be greatly appreciated

---

### Post by plucky on 2011-03-01
> **lunokhod said:**
> Hi I'm brand new to ubuntu I had an old laptop and a friend gave me a ubuntu version 8 i think instal disk and I'm trying to install from the add/remove applications it will usally get to about 44 then stop and come up the message "could not download all repository indexes" . I can't even get the current list of applications. Any help would be greatly appreciated

Open a terminal (**Applications > Accessories > Terminal**) and input ```
sudo apt-get update
``` and post the output to the forum.

Also ```
cat /etc/apt/sources.list
```

Good luck

---

