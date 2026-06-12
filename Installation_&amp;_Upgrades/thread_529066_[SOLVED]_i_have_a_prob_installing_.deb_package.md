---
title: "[SOLVED] i have a prob installing .deb package"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by cc93 on 2007-08-18
i tried to install virtual box for ubuntu and sudetly it stuck  an i closed it by force quit
now i can't to install any .deb package or run package manager 
error screenshot  for .deb installation : [IMG]http://i11.tinypic.com/5xhenav.png[/IMG]

error from package manager:[IMG]http://i11.tinypic.com/6feu96v.png[/IMG]

---

### Post by taurus on 2007-08-18
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by forestpixie on 2007-08-19
If you haven't fixed it yet try this in a terminal

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

then you can start again

---

### Post by cc93 on 2007-08-19
thx i will try it

---

### Post by cc93 on 2007-08-19
thx man :)

---

### Post by forestpixie on 2007-08-19
mark it solved then :D

---

### Post by cc93 on 2007-08-19
ok i did it

---

