---
title: "How to remove add-apt-respository sources?"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Nigggo on 2010-02-16
Hi there. I added some PPA sources with add-apt-repository but they are not listed ind sources.list.... how could remove them again?
the problem is that i added a ppa for xbmc svn version and now want to chance to another branch which uses older versions and so apt-get ignores these packages.
thx

---

### Post by phillw on 2010-02-16
> **Nigggo said:**
> Hi there. I added some PPA sources with add-apt-repository but they are not listed ind sources.list.... how could remove them again?
the problem is that i added a ppa for xbmc svn version and now want to chance to another branch which uses older versions and so apt-get ignores these packages.
thx


Hi, the list is stored at /etc/apt/sources.list  - you can edit it to add / remove sources.

you can also use Synaptics to do it via GUI, you can also 'pin' a package so it won't be changed on updates, even if there is one available.

Regards.

Phill.

---

### Post by snowpine on 2010-02-16
If they are not listed in /etc/apt/sources.list, look in the folder /etc/apt/sources.list.d

---

### Post by Nigggo on 2010-02-16
THX, there it was :p
sources.list.d was the solution.

---

### Post by mrebanza on 2010-09-21
```
 sudo gedit  /etc/apt/sources.list

 sudo gedit  /etc/apt/sources.list.d
```

:guitar:

---

### Post by alwinlin on 2011-09-09
I got the same problem, and now it is solved.
Thanks Nigggo, for your ask =)

---

### Post by levimaen on 2012-04-11
> **Nigggo said:**
> THX, there it was :p
sources.list.d was the solution.
Thank you Nigggo! It is an excellent and simple solution!):P

---

### Post by oldos2er on 2012-04-11
Closed, necromancy.

---

