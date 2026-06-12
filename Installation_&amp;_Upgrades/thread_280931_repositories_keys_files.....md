---
title: "repositories keys files...."
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by PardoX on 2006-10-20
Hi
I would like to add new repositories for ubuntu tls 6.0.6
but when i try to update system im geting key error
NO_PUBKEY F120156012B83718 
Where can i found this key (.gpg) files?

```

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

##
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Ubuntu
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## Backport
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free

```

thanks.

---

### Post by Arby on 2006-10-20
Which particular repository is it complaining it doesn't have a key for? All of them?

---

### Post by Kateikyoushi on 2006-10-20
Copy these lines to the terminal and should run fine as before.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

---

