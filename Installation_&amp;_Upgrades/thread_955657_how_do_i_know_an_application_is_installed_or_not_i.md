---
title: "how do i know an application is installed or not in through terminal"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by sandhu987 on 2008-10-22
Hi
I want to know whether java is installed in my system or not?Moreover i want to know whether a particular application is installed in my system or not........

---

### Post by Orlsend on 2008-10-22
Alt+F2 and type the Name and if its there it will tell you.

You know if Java is installed if you have a link under **System>preference> ***java should be here*****

---

### Post by scragar on 2008-10-22
```
dpkg -l | grep **pakage name**
```
will list packages matching a pattern that are installed, honestly though, the easiest way to test for java is to try it:
```
java -version
```
will either display:
```

bash: java: command not found

```or something like```
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

```

---

