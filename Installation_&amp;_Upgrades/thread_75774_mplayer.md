---
title: "mplayer"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by abominable on 2005-10-14
I can't find mplayer..

I tried:
>>apt-get install mplayer-386
E: couldn't find package mpalyer-386

I have these repositories:

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


Do I need something else?

---

### Post by adwait on 2005-10-14
try mplayer-586

---

### Post by abominable on 2005-10-14
[QUOTE=adwait]try mplayer-586[/QUOTE]

Same. How can I see all the packages I can install through apt-get? Or to give a certain word and show all the packages with a name containing the word?

---

### Post by wezzer-foo on 2005-10-14
```
apt-cache search [keyword]
```

for example ```
apt-cache search firefox
```

```
apt-cache search firefox | grep firefox
``` is useful also.

---

### Post by abominable on 2005-10-14
[QUOTE=wezzer-foo]```
apt-cache search [keyword]
```

for example ```
apt-cache search firefox
```

```
apt-cache search firefox | grep firefox
``` is useful also.[/QUOTE]

Tried apt-cache search mplayer,  and got no results familiar with mplayer. Do you know any repos for this?

---

### Post by Pablo_Escobar on 2005-10-14
What about :
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

??

---

### Post by Pablo_Escobar on 2005-10-14
You can always look for a package at :
[http://packages.ubuntu.com]("http://packages.ubuntu.com")

There is a search tool - type in a name of package and it'll tell You if it's in the repos and which one :)

Hope this helps :)

---

### Post by heart_reaver on 2005-10-15
Can't  we have some thing to be added in source.list so that it package appears in synaptics.

Just like for 5.04 given on [www.ubuntuguide.org](www.ubuntuguide.org) to add extra repositories.

:KS

---

