---
title: "Upgrade 12.04 LTS to 14.04 LTS (&quot;No new release found&quot;)"
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by DigiAngel on 2016-02-29
Topic says it...I saw a post a couple years ago with this same issue, but I thought I'd ask here again.  I have three 12 machines that are at 12.04.5 LTS, /etc/update-manager/release-upgrades is set to Prompt=LTS.  List of sources:

```
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

```

These machines haven't been modified much at all.  do-release-upgrade and do-release-upgrade -c all give me "No new release found".  Any thoughts on what I might be missing?  Thanks.

---

### Post by grahammechanical on 2016-02-29
There are 2 options for being notified of a new release. For any new version & For Long Term Support versions.

Makes sure that Software Sources (or whatever it is called in 12.04) is set to notify of the next LTS release and not any new version. 

Regards

---

### Post by deadflowr on 2016-02-29
What version of update-manager-core do they have?
Try
```
apt-cache policy update-manager-core
```
to find out.

---

### Post by DigiAngel on 2016-03-04
> **deadflowr said:**
> What version of update-manager-core do they have?
Try
```
apt-cache policy update-manager-core
```
to find out.

Bah....and of course I got sick this week and didn't have access to the servers 8-|  Anyway here's the update-manager-core output:
```
update-manager-core:
  Installed: 1:0.156.14.19
  Candidate: 1:0.156.14.19
  Version table:
 *** 1:0.156.14.19 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:0.156.14.5 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     1:0.156.14 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages

```

Thank

---

### Post by DigiAngel on 2016-03-04
And running this on a different machine I see that candidate 1:0.196.11 is available from trusty/main and it's upgrading...so I'm at a loss on why some machines can't see this.

---

### Post by DigiAngel on 2016-03-08
Long story short, firewall was blocking launchpad.net 8-|

---

