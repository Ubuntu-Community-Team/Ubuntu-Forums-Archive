---
title: "convert bitmap to vector graphic (autotrace, frontline, delineate)"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by xy77 on 2005-04-16
Did anyone manage to install and run frontline or delineate?

Delineate (0.5) complaints about:
```

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/xpath/XPathAPI
        at net.sf.delineate.utility.XPathTool.string(XPathTool.java:68)
        at net.sf.delineate.utility.XPathTool.string(XPathTool.java:110)
        at net.sf.delineate.DelineateApplication.addControlTab(DelineateApplication.java:86)
        at net.sf.delineate.DelineateApplication.<init>(DelineateApplication.java:62)
        at net.sf.delineate.DelineateApplication.main(DelineateApplication.java:316)

```

I have autotrace and potrace installed.

Any help would be appreciated.

- David (xy77)

---

### Post by blueshome on 2005-05-02
I've the same problem
Someone can help me (us)....... ](*,)
I've installed java sdk with make-dpkg
and I supose it works...
at command java -version this is the answer
[INDENT]java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)[/INDENT]

---

### Post by xy77 on 2005-05-27
finally I figured out how to install frontline (locally):

install libgnome-dev libart-dev libautotrace-dev (and a lot of dependencies)
untested:
```
# apt-get install libgnome-dev libart-dev libautotrace-dev
```
download frontline source, extract it and enter it's directory
```
# ./configure
# make all
```

You may want to give it a try. If you need a more detailed explaination, feel free to ask.

greetings,
  David (xy77)

---

### Post by Pauan on 2006-10-05
Thank you so much! Your solution worked! The problem that was plaguing me has been aleviated. Thank you once again!

---

