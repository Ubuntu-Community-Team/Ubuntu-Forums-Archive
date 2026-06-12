---
title: "repositories enabled. update manager cant find main binaries?"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by boogiepop88 on 2007-05-23
hello,
I am upgrading a friends laptop from dapper to feisty, however when it starts to download the updates for edgy i get this message

cant fetch:
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

i checked and i have all the repositories enabled, so i dont know exactly what is wrong, unless maybe there is maintenence? The result is the same two days in a row. I've never experienced this problem myself while upgrading. Any help would be extremely appreciated, thanks in advance.

---

### Post by freelsjd on 2007-05-27
I have had the same problem for days.  Must be something wrong with the repository ?

---

### Post by Andy17MB on 2007-05-28
Same problem here.  If you run the "Official" upgrade method from the terminal you will still have a terminal window open.  I get a couple of messages which may help diagnose the problem:

Firstly a message that Dbus failed to initialise

Secondly when the error box comes up in Gnome an error comes up in terminal indicating that the Bzip error code is due to a public key not being available.

Andy

---

### Post by zvacet on 2007-06-03
You can not upgrade directly from Dapper to Feisty.It goes Dapper>Edgy>Feisty.If you have separate home partition it is better to do clean install.if you don´t have separate home make one if you have enough free space.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Andy17MB on 2007-06-04
I am definitely going from Edgy to Feisty and not trying to go from Dapper.  I did have a problem where sources.lst got overwritten with the  Dapper list. I've since put this right and am now pointing at the edgy repositories again.  I suspect that a key somewhere is still set for Dapper so that the security check fails.  Any Suggestions?

Andy

---

### Post by zvacet on 2007-06-04
if you changed source list 

```
sudo aptitude update
```

---

