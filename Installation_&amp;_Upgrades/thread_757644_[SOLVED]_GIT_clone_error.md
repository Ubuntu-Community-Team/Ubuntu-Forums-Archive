---
title: "[SOLVED] GIT clone error"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Khalis7 on 2008-04-17
Hi..

I'm trying to clone a repo but every time i issued the command, i received an error

```
$ git clone http://intellinuxwireless.org/repos/ipwraw.git
Initialized empty Git repository in /home/khalis7/ipwraw/.git/
/usr/bin/git-clone: 310: curl: not found
Cannot get remote repository information.
Perhaps git-update-server-info needs to be run there?
```

I've been looking around the forum and found a similar problem but then it didn't worked out for me.
Any idea anyone???

---

### Post by alostale on 2008-04-28
Try installing curl:

sudo apt-get install curl

---

