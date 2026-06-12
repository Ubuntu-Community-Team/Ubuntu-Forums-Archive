---
title: "installing the format .tgz"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by barath on 2007-04-12
I downloaded a file 

   magic-7.4.34.tgz
how do i install this .
It is a free ic layout designing tool for linux.
pls help me

---

### Post by taurus on 2007-04-12
Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf magic-7.4.34.tgz
cd magic-7.4.34
```
Now, either look in README of INSTALL to see what you have to do to build/install it.

```
more INSTALL
```
Otherwise, post the output of this command here.

```
ls -la
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by playertm on 2007-04-12
i'm not installing unikey for linux on ubuntu, plaese help me about it

---

### Post by barath on 2007-05-02
well when i typed 


 sudo tar xvzf magic-7.4.34.tgz

i got this on my screen...

tar: magic-7.4.34/scripts/config.cache: Cannot change ownership to uid 515, gid 100: Operation not permitted
magic-7.4.34/scripts/config.guess
tar: magic-7.4.34/scripts/config.guess: Cannot change ownership to uid 515, gid 100: Operation not permitted
magic-7.4.34/scripts/config.sub
tar: magic-7.4.34/scripts/config.sub: Cannot change ownership to uid 515, gid 100: Operation not permitted
magic-7.4.34/scripts/configure
tar: magic-7.4.34/scripts/configure: Cannot change ownership to uid 515, gid 100: Operation not permitted
magic-7.4.34/scripts/configure.in
tar: magic-7.4.34/scripts/configure.in: Cannot change ownership to uid 515, gid 100: Operation not permitted

tar: magic-7.4.34/wiring: Cannot change ownership to uid 515, gid 100: Operation not permitted
tar: magic-7.4.34: Cannot change ownership to uid 515, gid 100: Operation not permitted
tar: magic: Cannot create symlink to `magic-7.4.34': Operation not permitted
tar: Error exit delayed from previous errors


what to do?????
please help.......

---

