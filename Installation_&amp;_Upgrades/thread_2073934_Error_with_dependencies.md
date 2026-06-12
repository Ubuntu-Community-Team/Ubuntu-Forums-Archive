---
title: "Error with dependencies"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by agnes1984 on 2012-10-20
Hi there,

I am running Ubuntu 12.04.1 64 bit. I have come across an apt-get error. After running apt-get update which returns no errors, I do apt-get upgrade:
```

Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.1) but 8.0.3+8.0.2-0ubuntu3.2 is installed
 libglapi-mesa:i386 : Conflicts: libglapi-mesa but 8.0.3+8.0.2-0ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.

```

I have run apt-get install -f with the following results:
```
dpkg: error processing libglapi-mesa:i386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 libglapi-mesa:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

apt-get autoremove returns:

```
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.1) but 8.0.3+8.0.2-0ubuntu3.2 is installed
 libglapi-mesa:i386 : Conflicts: libglapi-mesa but 8.0.3+8.0.2-0ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.

```

So I guess this is one of those dependency hells I've heard about. Any help will be appreciated.
Thank you
Agnes

---

