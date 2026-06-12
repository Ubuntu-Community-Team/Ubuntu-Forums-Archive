---
title: "lucid-proposed updates showing also when not enabled"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by okap on 2010-05-28
Hi
i'm using ubuntu lucid.
apt-get suggests me ubuntu updates from the lucid-proposed repository 
even if it's not enabled in my sources.list
Perhaps it was enabled in the past but now it's not.
this is my sources.list:
```

deb http://it.archive.ubuntu.com/ubuntu/ lucid main restricted
deb http://it.archive.ubuntu.com/ubuntu/ lucid universe
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://it.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse

```the directory sources.list.d is empty
I tried to reinstall apt and start with an empty /etc/apt but those packages
(for instance mysql-client-core-5.1 version 5.1.41-3ubuntu12.1)
keep showing on update-manager 

How can i avoid that unwanted packages ?
Thank in advance

---

### Post by okap on 2010-05-28
my error the packages I wanted to avoid are in lucid-updates

---

