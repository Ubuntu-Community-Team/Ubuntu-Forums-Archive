---
title: "Synaptic Package Manager"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by rahulthewall3000 on 2006-12-12
"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

[http://ubuntu.compiz.net/dists/edgy/Release.gpg:](http://ubuntu.compiz.net/dists/edgy/Release.gpg:) Temporary failure resolving 'ubuntu.compiz.net'
[http://ubuntu.compiz.net/dists/edgy/main-edgy/i18n/Translation-en_US.bz2:](http://ubuntu.compiz.net/dists/edgy/main-edgy/i18n/Translation-en_US.bz2:) Temporary failure resolving 'ubuntu.compiz.net'

Now what I am supposed to do about this! Please Help!

---

### Post by taurus on 2006-12-12
Edit your /etc/apt/sources.list and place a # in front of those two lines to comment them out...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rahulthewall3000 on 2006-12-27
Hey, thanks for your reply! I guess I am a little late, but I was busy with exams!:(

---

