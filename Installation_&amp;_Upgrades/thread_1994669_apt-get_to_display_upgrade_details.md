---
title: "apt-get to display upgrade details"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by AnotherMuggle on 2012-06-03
Morning All,

Does anyone know if it's possible to get "apt-get upgrade" to tell you the details of the upgrade for individual packages, like you see in Update Manager?

I'd like to see details of the changes in each of the updates before I go ahead and install them.  Mainly out of curiosity and partly to see if any of the bugs I know about are about to get fixed :D

Cheers,
TK

---

### Post by PaulW2U on 2012-06-03
Try these:

```
sudo apt-get -V upgrade
```

will show the old and new version numbers while

```
apt-get changelog <package name>
```

will show the change log if there is one.

If you type **apt-get** in a terminal window you'll see the various options available.

---

### Post by AnotherMuggle on 2012-06-03
> **PaulW2U said:**
> Try these:

```
sudo apt-get -V upgrade
```

will show the old and new version numbers while

```
apt-get changelog <package name>
```

will show the change log if there is one.

If you type **apt-get** in a terminal window you'll see the various options available.

This looks like what I wanted!

I had a look at the man pages and got a bit of an idea on what I needed to do but I don't like to run commands I'm not totally happy I understand.

Thanks for the info :D

---

