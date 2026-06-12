---
title: "trying to update to edgy"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by a-hamster on 2007-06-24
[COLOR="Red"]well as the title says i'm trying to update however the return of 

```
$ sudo update-manager -c
```
is
```
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

```

and then the updater starts and says i'm upto date :( any advice? (i'm kinda a noob)[/COLOR]

---

### Post by a-hamster on 2007-06-25
[COLOR="Red"]bump

HELP[/COLOR]

---

### Post by eapache on 2007-06-25
Try sudo "update-manager -c" (with the quotes) and see if it makes a difference.

---

### Post by a-hamster on 2007-06-25
[COLOR="Red"]the return of that was
```

a-hamster@a-hamster-laptop:~$ sudo "update-manager -c"
Password:
sudo: update-manager -c: command not found

```[/COLOR]

---

### Post by a-hamster on 2007-06-25
[COLOR="Red"]for some strange reason (or none at all) when i opened update manger and told it to check for updates it found it :smile: [/COLOR]

---

