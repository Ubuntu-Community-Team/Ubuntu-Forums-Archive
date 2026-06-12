---
title: "gwibber error, what to do?"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by loracska on 2011-02-24
Hi,
I just tried to install OO database using Ubuntu Software Center and got this error message:

installArchives() failed: Selecting previously deselected package libhsqldb-java. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `gwibber' contains empty filename

What should I do to fix this?

Thanks in advance,
L

---

### Post by dino99 on 2011-02-24
[http://ubuntuforums.org/showpost.php?p=9517188&postcount=26](http://ubuntuforums.org/showpost.php?p=9517188&postcount=26)

[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)
[https://launchpad.net/~gwibber-team/+archive/ppa](https://launchpad.net/~gwibber-team/+archive/ppa)

---

### Post by sikander3786 on 2011-02-24
Welcome to the forums :-)

Try using an older dpkg/status file.

Backup the existing one.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Use the older one,

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update
```

And try installation again.

---

