---
title: "something wrong with java ???"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by baz on 2006-12-06
It seems a couple of different people are having trouble running
java apps in Ubuntu.  I can't run Shredder Chess for Linux.

We get this error message

===================================================
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
===================================================

what's up with this? and how can we fix it???

many thanks,

baz

---

### Post by taurus on 2006-12-06
Do you have a java installed on your machine?  What is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

---

### Post by bazder on 2006-12-08
> **taurus said:**
> Do you have a java installed on your machine?  What is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```

```
~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)



```

---

### Post by meng on 2006-12-08
Suspect you'll need sun's java. Check these instructions:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by gutek on 2006-12-14
propably you need to install this package: libgcj7-awt

Gutek

---

