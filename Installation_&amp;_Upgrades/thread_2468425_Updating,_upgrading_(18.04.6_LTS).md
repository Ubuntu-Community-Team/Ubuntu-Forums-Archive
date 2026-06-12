---
title: "Updating, upgrading (18.04.6 LTS)"
date: 2021-10-29
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2021-10-29
I'm running an Ububtu 18.04.6 LTS server and through the years whenever I saw packages to update when logging in, like:

```
13 updates can be applied immediately.
9 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

No mail.
```

I did an apt-get update followed by an apt-get upgrade and the reminder to update/upgrade certain packages was now.
Since some time these messages stay as if something doesn't get updated.

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.6 LTS"

me@mysite:~$ uname -a
Linux mysite.org 4.15.0-118-generic #119-Ubuntu SMP Tue Sep 8 12:17:48 UTC 2020 i686 i686 i686 GNU/Linux
me@mysite:~$ 
```

Subsequent apt-get update ; apt-get upgrade doesn't make the demand note for upgrading go away.

```
me@mysite:~$ apt list --upgradable
Listing... Done
linux-generic/bionic-updates,bionic-security 4.15.0.161.150 i386 [upgradable from: 4.15.0.118.105]
linux-headers-generic/bionic-updates,bionic-security 4.15.0.161.150 i386 [upgradable from: 4.15.0.118.105]
linux-image-generic/bionic-updates,bionic-security 4.15.0.161.150 i386 [upgradable from: 4.15.0.118.105]
ubuntu-advantage-tools/bionic-updates 27.2.2~18.04.1 all [upgradable from: 17]
ubuntu-drivers-common/bionic-updates 1:0.8.6.3~0.18.04.2 i386 [upgradable from: 1:0.5.2.5]
me@mysite:~$ 
```


How can I enforce the upgrading process?

---

### Post by guiverc on 2021-10-29
Have you used a `apt full-upgrade` ?

There are cases where packages need to be removed first; and `apt upgrade` will not do that; you given permission by using the `full-upgrade`

From `man apt` on my release (sorry it's not *bionic* or 18.04)

> full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.

---

### Post by deadflowr on 2021-10-29
Run
```
sudo apt full-upgrade
```
or
```
sudo apt-get dist-upgrade
```
The linux packages listed will never get installed using the apt-get upgrade command.
So every time you run that command those packages are kept back.
The two commands posted will install those packages.
Either should do the trick.

---

### Post by Krischu on 2021-10-29
Thanks. Next time I'll try this first (full-upgrade). For now my problem is solved. I did an

```
apt-get distupgrade
```

and silence.

---

