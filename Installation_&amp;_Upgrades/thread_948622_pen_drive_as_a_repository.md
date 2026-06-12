---
title: "pen drive as a repository"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-10-15
Hi all,

 I have read that by using the command **sudo apt-cdrom add** 
 we can use CD ROM as repository, in the same way how can we use pen drive as a repository ?

** NB: I use ubuntu 8.04**

---

### Post by wilbbe01 on 2008-10-15
The following site may help you.

[http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.en.html)

If you already have everything formatted correctly you may try adding something like the following (also taken from the website given previously) in your /etc/apt/sources.list file

```
deb file:///home/aisotton/rep-exact binary/
deb-src file:///home/aisotton/rep-exact source/
```

---

