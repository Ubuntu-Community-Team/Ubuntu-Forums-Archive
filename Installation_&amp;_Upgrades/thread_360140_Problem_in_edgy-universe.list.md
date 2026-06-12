---
title: "Problem in edgy-universe.list"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by djcaston on 2007-02-12
Apparently I have a malformed line in etc/apt/sources.list.d/edgy-universe.list. Could someone please post the correct line 3 for me? Thanks

---

### Post by taurus on 2007-02-12
Why don't you post your /etc/apt/sources.list.d/edgy-universe.list here and somebody will have a look at it?

```
cat /etc/apt/sources.list.d/edgy-universe.list
```

---

### Post by djcaston on 2007-02-13
Here's the list:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe

---

### Post by taurus on 2007-02-13
The second line is off.  Edit /etc/apt/sources.list.d/edgy-universe.list

```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```
and place a # in front of the second line.

```
#deb http://security.ubuntu.com/ubuntu edgy-security
```
Save it and run these two commands again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

