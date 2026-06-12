---
title: "no desktop effects on feisty upgrade"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by kyle_fransham on 2007-04-23
I upgraded to feisty, all excited about the built-in desktop effects, but I don't seem to have an entry for it in System->Preferences.  All of my menus look identical to the way they did in edgy.  I did in fact upgrade, since 
```

sudo lsb_release -a

```
gives me
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

```
I had 3D acceleration enabled in edgy using beryl

in case it matters, my /etc/apt/sources.list file looks like: (minus a few comments)
```

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

```

If anyone could help me figure this out, I'd be eternally grateful!

---

### Post by torstenprahl on 2007-04-23
Same problem here.  I have not been able to locate desktop effects.

any help would be great!

---

### Post by Spyrious on 2007-04-24
Me too

---

### Post by kyle_fransham on 2007-04-24
I did all that I could, and still couldn't get any entries in my menus that were any different than those that I had in edgy.  My final solution was to tar my entire home directory, burn it to CD, then re-install from scratch.  Pretty terrible I know, but now at least I have shadows on my windows!:)

---

### Post by torstenprahl on 2007-04-24
I figured out my problem.  For some reason Desktop Effects did not get installed.  I went to the Synaptic package manager and did a search for desktop effects, selected it, and installed.  My problem was solved :)

---

