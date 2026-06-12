---
title: "Can't upgrade to 9.10"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Vebea on 2011-05-07
I can't upgrade my Ubuntu to the 9.10... I get this error:
**E: Problem executing scripts APT::Update: Pre-Invoke '/usr/bin/daptup --pre', E:Sub-process returned an error code**
can somebody help me?

---

### Post by kansasnoob on 2011-05-07
Probably because 9.10 has already reached end-of-life:

[http://www.ubuntu-news.net/2011/03/30/ubuntu-9-10-reaches-end-of-life-on-april-30-2011/](http://www.ubuntu-news.net/2011/03/30/ubuntu-9-10-reaches-end-of-life-on-april-30-2011/)

---

### Post by Vebea on 2011-08-30
and what can I do? how can I upgrade to the newest version?

---

### Post by howefield on 2011-08-30
Have a read at this page explaining how to carry out an End of Life upgrade ..

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by mcduck on 2011-08-30
> **Vebea said:**
> and what can I do? how can I upgrade to the newest version?

You could change your sources.list manually to use old-releases.ubuntu.com, but since both the version you are running and the next one are already out of support, and you'd need 4 upgrades to get to the latest release, the easiest way really would be to just make a fresh install of 11.04 instead.

---

### Post by Vebea on 2012-01-24
Now I have a new problem...I tried to do as you said..but when I'm trying to safe-upgrade it tells me: 
```
marya@dana:~$ sudo aptitude update
[sudo] password for dana: 
E: Type ‘<!DOCTYPE’ is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: Type ‘<!DOCTYPE’ is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
E: Type ‘<!DOCTYPE’ is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
E: Type ‘<!DOCTYPE’ is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: Couldn't read list of package sources

```

---

### Post by oldos2er on 2012-01-24
Edit your /etc/apt/sources.list.d/medibuntu.list file ```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
``` to look exactly like
 
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free assuming you're running Oneiric.

---

