---
title: "ubuntu java support"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by ravisharma1987 on 2007-10-20
hello ubuntu users
I'm a student of cs, and have become frustrated trying running a java program......
whenever i try writing in terminal
gij x.java
it says java.lang.classnotfoundexception 
and nothing happens .............
plz tell me something

---

### Post by est on 2007-10-21
This isn't really an installation issue.

You need to compile your java code before it can be run.

Try `gcj x.java' to compile, followed by `gij x' to run (note the lack of .java or .class at the end).

---

