---
title: "Problem with Warning Target package is configured multiple time"
date: 2018-12-31
forum: Installation &amp; Upgrades
---

### Post by thp64 on 2018-12-31
Hello,
I have this problem of Target package multiple time configured.
I've searched for solution but... not fin the one that works for me.
When I check for my list source (without the comments), I have this :

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-updates main restricted universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic-updates universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse

Sure that I have to delete some of the source, but which one ?
Probably the problem comes from the fr source and the general Ubuntu source ?
I'am on Kubuntu 18.04 KDE plasma 5.12.7

so if someone have a clue, thank a lot and happy new year tio evrery one !

---

### Post by Bashing-om on 2018-12-31
Hello thp64 - Welcome to the forum.

Please show us the outputs - between code tags - of terminal commands:
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo apt update
sudo apt upgrade

```
so we see the exact error and in context. Then we know where we go to from here.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by deadflowr on 2018-12-31
You're hitting the bionic-security repos twice.
Recommend commenting out the second entry.

---

### Post by Bashing-om on 2018-12-31
deadflowr
Has good eye :)

-seek and ye shall find-

---

