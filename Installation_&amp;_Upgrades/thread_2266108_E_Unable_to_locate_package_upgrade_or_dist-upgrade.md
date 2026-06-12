---
title: "E: Unable to locate package upgrade or dist-upgrade"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by Renx on 2015-02-19
Freshly installed ubuntu and then tried to update/upgrade... Here is what I have done and got back:

I have verified that the /etc/apt/sources.list is correct...
I ran sudo apt-get update and then I try to run sudo apt-get install upgrade and it returns "E: Unable to locate package upgrade"
I then tried sudo apt-get dist-upgrade and I got "E: Unable to locate package upgrade"
I tried to run sudo apt-get install -f and it didn't fix the issues.

Things to note:
I am running 14.04 LTS 64-bit
7.5 GBs of RAM
AMD Phenom II (Triple Core)
Gallium AMD RS880 (Its the only one it seems to detect of the two my laptop has)

Any help is greatly appreciated... I am not totally new to linux I have just never encountered this problem where the solution wasn't my sources.list or install -f didn't fix it.

---

### Post by Renx on 2015-02-19
Fixed this issue with sudo apt-get -f install. It wont let me update my thread though.

---

