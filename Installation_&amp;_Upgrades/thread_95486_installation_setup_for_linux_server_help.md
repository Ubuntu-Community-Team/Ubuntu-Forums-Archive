---
title: "installation setup for linux server help"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by ryedawg on 2005-11-26
anyone have any luck installing plesk 7.5 on breezy badger???
is it possible?

---

### Post by SyphOn on 2006-01-17
Yes i got it working.

Download the Ubuntu 5.04 Autoinstaller build 75050908.11 from the swsoft website:

[http://www.swsoft.com/en/download/plesk75reloaded/](http://www.swsoft.com/en/download/plesk75reloaded/)

put in in let's say ~/plesk

```
chmod +x Autoinstaller
```

If MySQL is installed make a user called 'admin' with password 'setup' or leave the root password empty (not recommended). If MySQL is not installed, don't install it ;)

```
./autoinstaller
```

Follow onscreen instructions. Dont forget to choose the swsoft server as installation media.

If the installer fails after building dependencies, processing package list or returns to te first install screen, try to do: 

```
ctrl-c
apt-get update
apt-get -f install
```

Then run the installer again.

---

