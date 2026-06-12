---
title: "update-manager 8.04 upgrade not an option"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by mondomunchies on 2008-05-08
I have gone to update-manager and checked for updates 100 times but the option to upgrade to 8.04 never appears.

#sudo apt-get dist-upgrade says it is making changes to 0 packages and finishes.

It's like there's no new distribution at all.  Internet works fine as well as everything else.

 Thanks

I have Ubuntu 7.10 fully updated with kernel 2.6.22-14-generic #1 SMP.

---

### Post by mondomunchies on 2008-05-09
I tried sudo apt-get -d -c too and that didn't work.

Does anyone know why upgrading through update-manager is not an option for me?

---

### Post by Pumalite on 2008-05-09
Post:
cat /etc/apt/sources.list

---

### Post by schmy on 2008-05-18
I'm in a similar position; though I'm trying to from Feisty to Gutsy to Hardy (as the site suggests).

I do have a live CD for Gutsy (somewhere) but was hoping I didn't need to search for it (or download it again).

Happy to take any (sane) suggestions.

I'd post the details from "cat /etc/apt/sources.list but there's a lot of text. Not sure what you're looking for.

Cheers.

---

### Post by cdtech on 2008-05-18
This was my old list. I could not use this list because of some issues with the us server.
```
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb http://mirror2.ubuntulinux.nl/ dapper-seveas all
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://download.webmin.com/download/repository sarge contrib
```

So I copied this list to my sources.list:
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

I verified that my current install was completely up to date:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```

```
sudo aptitude install update-manager-core
```
start the upgrade using:
```
sudo do-release-upgrade
```

This worked for me. Just a thought.

---

### Post by mondomunchies on 2008-05-26
I did your suggestion cd-tech.  everything worked great until "sudo do-release-upgrade" all it said was checking for a new distro, no new distro found.  When I go to system > admin > update manager it asks to perform a partial distro upgrade.

---

### Post by Pumalite on 2008-05-26
Make sure you got rid of all third parties in your sources.list

---

### Post by mondomunchies on 2008-05-26
I did so.  It again didnt work.  Opening package manager allowed me to add one more package, python, during another partial upgrade.

---

### Post by mondomunchies on 2008-05-26
Instead of all these dapper repos should I have the hardy heron ones?

---

