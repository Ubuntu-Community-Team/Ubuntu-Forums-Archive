---
title: "Upgrade sqlite3.4.2 to sqlite3.5.9"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by deevabone on 2008-07-15
Hi all, 

In an application I am writing I need to use the latest version of sqlite3 - 3.5.9.

How can I install this and replace the current hardy version of 3.4.2?

All help is appreciated.

D.

---

### Post by deevabone on 2008-07-15
Nevermind - I was able to grab the source files and compile.

BUT - while working with Python be sure to have the ./configure --prefix=/usr set as python will look into this folder upon import of sqlite3 or pysqlite2

D.

---

