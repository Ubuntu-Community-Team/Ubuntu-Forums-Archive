---
title: "E: Couldn't find package"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by mikeylikesit on 2007-02-03
Hello, i am using Ubuntu 5.10 as a web server I would like to install phpsysinfo but whenever i try sudo apt-get install i get a message: E: Couldn't find package. I have tried it with php4 as well and it did not work. What am i doing wrong? any help would be great.


Thanks

---

### Post by taurus on 2007-02-03
Maybe you need to enable both universe & multiverse in /etc/apt/sources.list by removing the # in front of all those deb repos.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano -w /etc/apt/sources.list
```
Then, run

```
sudo aptitude update
```

---

