---
title: "Upgrade from 6.06"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by blamecanada on 2007-04-16
I have a fresh install of 6.06, and would like to upgrade to 7.04, but I realize I need to go to 6.10 first. The problem is my update manager won't display any dist upgrades even if i use:

gksu "update-manager -c"

It is the AMD 64 version, and when I run the above command, I get

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

---

### Post by panty31772 on 2007-04-16
[COLOR="Red"]Method A ( official ):[/COLOR]
Just do
Code:

```
sudo aptitude update && sudo aptitude upgrade
```

now that your update manager is up to date do :
Code:

```
gksudo "update-manager -c -d"
```

[COLOR="Red"]For method B (alternative ):
[/COLOR]
do


```
sudo gedit /etc/apt/sources.list
```

and replace all the dappers to edgy.
You might also want to uncomment all sources ( for in case you'll need universe later )

Now this is very important


```
sudo aptitude update 
sudo aptitude dist-upgrade
```

Try this ! has worked for me with no problems .

---

### Post by blamecanada on 2007-04-16
Ok option 2 seems to be working, as the terminal seems to be downloading everything.

---

