---
title: "apt-get update fails"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by ddwelley on 2007-08-07
When I run apt-get update, It gets to 99% and fails with the error message "failed to fetch packages.gz" This is a fresh 7.0.4 LAMP install standard 32 bit. It also mentions package not in gzip format.

Thanks in advance.
D

---

### Post by milosz.galazka on 2007-08-07
Hello, please put here output of 

sudo apt-get update

and

cat /etc/apt/sources.list

---

### Post by ddwelley on 2007-08-08
I reinstalled Server 7.0.4 and things seem to be working now.

---

