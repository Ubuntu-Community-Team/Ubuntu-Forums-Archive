---
title: "apt-get issues"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by lesemi on 2008-02-11
Bit of a weird issue that i haven't seen yet.

i just switched routers - and i've had a few issues since - very sporatic so i'm not sure if it's related (linksys).

I'm trying to sudo apt-get update or install and here's the result:

i just can't get past the last repository - i haven't changed anything else - any idea?

[COLOR="Red"]Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
[/COLOR]

---

### Post by taurus on 2008-02-11
Maybe that mirror site is down.  Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change it to Main Server.  Now, see what happens if you run that command again from a terminal, after closing down synaptic first.

```
sudo apt-get update
```

---

### Post by mikewhatever on 2008-02-11
Do you have Kubuntu 6.06 or Gutsy?

---

