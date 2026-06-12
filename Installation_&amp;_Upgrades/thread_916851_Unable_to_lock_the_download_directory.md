---
title: "Unable to lock the download directory?"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2008-09-11
Trying to install updates I got this error message:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

What does this mean?

---

### Post by aysiu on 2008-09-11
It means you have another package manager frontend running.

The package manager manages installation and removal of software. Only one package manager frontend can access it at a time.

Frontends include aptitude, apt-get, dpkg, gDebi, Update Manager, Synaptic Package Manager, Adept Package Manager, and Add/Remove

If you have more than one of these in use, the second one in use will report that it's locked.

---

### Post by ustazz on 2009-02-08
Hi, I got the same problem but let me give some history.

first I was trying to install java6-jre which end up in a licence file, from where I was unable to get further so I closed the window.

Then I came up with "unable to lock the administration directory" error, I searched here and found "sudo rm /var/lib/dpkg/lock", which was ok but now it is "could not get lock /var/lib/dpkg/lock" error.

Any ideas !!! and Thanks

(new at ubuntu)

---

### Post by nicknitro71 on 2009-02-11
Same Update Manager error here:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by t1010011 on 2009-02-12
Same error
I got no other packge manager running at the time, even rebooted and still the same.
 any ideas?

---

### Post by t1010011 on 2009-02-12
turns out that dpkg was running in background

```
sudo killall dpkg 
```

solved for me

---

### Post by ub-khalid on 2011-10-18
thanks for [t1010011]("http://ubuntuforums.org/member.php?u=705877")

---

