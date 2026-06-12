---
title: "Error: Updating to 13.10 from 13.04"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by bhogal on 2014-04-15
Shows Error, while updating. Have also disabled Third Party Software. I have tried all options. Shows following error. 

Invalid package information

After updating your package information, the essential package 'ubuntu-minimal' could not be located. This may be because you have no official mirrors listed in your software sources, or because of excessive load on the mirror you are using. See /etc/apt/sources.list for the current list of configured software sources.
In the case of an overloaded mirror, you may want to try the upgrade again later.


[ATTACH=CONFIG]252096[/ATTACH]

---

### Post by ibjsb4 on 2014-04-15
So is there anything going on in your sources list?


```
cat /etc/apt/sources.list

```

---

### Post by bhogal on 2014-04-16
Thanks for your help. Changed the Server and worked.

---

