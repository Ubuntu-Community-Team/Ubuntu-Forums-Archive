---
title: "checkinstall Version Numbers"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by element103 on 2008-03-06
I recently used checkinstall to install a program (Pidgin) from source since it wasn't updated in the repo, but I used a normal version number (2.4.0) in the checkinstall options and now it doesn't work right with synaptic/update manager.  The repo version numbers seem to have some extra prefixes and suffixes that mess with the newer-than/older-than checking (i.e. 1:2.2.1-1ubuntu4.1)

Is there some way to tell it to trim the version numbers before comparing?

---

### Post by zvacet on 2008-03-06
No need for install from source.You can download latest version at [getdeb.](http://www.getdeb.net/)You can add getdeb as repository

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

### Post by element103 on 2008-03-07
> **zvacet said:**
> No need for install from source.You can download latest version at [getdeb.](http://www.getdeb.net/)You can add getdeb as repository

```
gksudo gedit /etc/apt/sources.list
```

add this line

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Save and close file.

```
sudo apt-get update
```

Thanks, that did the trick.  Also updated some other stuff I didn't know was a little outdated.

Just for reference though, let's say I install a beta of something and use checkinstall just so its easier to get rid of it later.  Is there any way to get update-manager to stop complaining about an old version when its not really older, just doesnt have the extra crap on the number?

---

### Post by aidanr on 2008-03-07
When running checkinstall hit 3 and change the version to 1:2.4.0

---

### Post by element103 on 2008-03-07
does the 1 in front mean anything?  I thought about doing that but it just seemed like a hackjob

---

### Post by aidanr on 2008-03-07
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version)

---

### Post by element103 on 2008-03-07
sweet thats what i was looking for, thanks

---

