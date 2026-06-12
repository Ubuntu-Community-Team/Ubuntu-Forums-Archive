---
title: "Kernel Upgrade Not Recognizing Architecture"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by lvleph on 2010-04-07
I wanted to upgrade my kernel to 2.6.33 so that I could get hibernate working. But, I got this weird error.
**sudo dpkg -i linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb**
```
dpkg: error processing linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb

```
but
**uname -a**
```

Linux erichs 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

```

---

### Post by falconindy on 2010-04-07
You're trying to install a 64 bit kernel on a 32 bit system. Not going to happen easily.

---

### Post by lvleph on 2010-04-07
Except that I have a 64 bit system and have 64 bit kernel already running.Or at least I recall installing 64 bit system. Maybe I am just confused.

---

### Post by Slim Odds on 2010-04-07
> **lvleph said:**
> Except that I have a 64 bit system and have 64 bit kernel already running. Which is why I posted the **uname -a**.

Except that uname is showing that you have a 32 bit kernel (i686). 64 bit would be x86_64.

---

### Post by lvleph on 2010-04-07
That is weird. You are right that is what it shows. I remember installing 64 bit. I guess I will just start from scratch then.

EDIT: This proves that drinking and installations don't mix.

---

