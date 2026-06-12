---
title: "Perl 5.6 install."
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Grantham on 2008-06-06
Hi there,

So today I wanted to install Perl. Except, when I tried, it gave me this
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Except the thing is, I'm the only user on this, so shouldn't that make me the root and admin of it?

---

### Post by Partyboi2 on 2008-06-06
Make sure that  you are only using one package management process  (add/remove, synatpic package manager, apt-get)  at a time.
If trying to install from a terminal are you putting sudo infront of the install commands?
eg.
```
sudo apt-get install <package>
```

---

### Post by conscious on 2008-06-07
A guide:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Grantham on 2008-06-07
Ah. Thanks guys. I figured it out and got rid of the dpkg error but I just can't remember how.

---

