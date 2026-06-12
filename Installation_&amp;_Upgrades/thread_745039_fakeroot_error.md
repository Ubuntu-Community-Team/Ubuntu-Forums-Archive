---
title: "fakeroot error"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by philmetz on 2008-04-04
name@computer:~$ sudo apt-get install fakeroot make-jpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
E: Couldn't find package make-jpkg

How can i install the make-jpkg then as you see am getting the error above?

Thanks
Phil

---

### Post by kellemes on 2008-04-04
> **philmetz said:**
> name@computer:~$ sudo apt-get install fakeroot make-jpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
E: Couldn't find package make-jpkg

How can i install the make-jpkg then as you see am getting the error above?

Thanks
Phil

fakeroot you already have so no need to install it again..
make-jpkg isn't an existing package, for this you need to install "java-package"

```
sudo apt-get install java-package
```

---

