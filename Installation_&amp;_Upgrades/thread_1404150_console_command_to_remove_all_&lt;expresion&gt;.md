---
title: "console command to remove all &lt;expresion&gt;"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by midaskensai on 2010-02-11
Hello,

My console fu is a bit lacking, as it seems that I can't figure out how to uninstall all packages containing a certain expression.

I tried:
apt-get remove *expression*

obviously to no avail. Help would be greatly appreciated.

---

### Post by SecretCode on 2010-02-11
Try 
```
sudo aptitude remove ~ntext
```
or
```
sudo aptitude remove ?name(text)
```

Proceed with caution. I'm not 100% sure of this.
In fact add the -s parameter, to simulate only.

---

