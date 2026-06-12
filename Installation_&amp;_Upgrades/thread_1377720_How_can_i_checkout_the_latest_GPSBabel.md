---
title: "How can i checkout the latest GPSBabel"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by chasem1991 on 2010-01-10
the latest cvs version has support for the Bushnell Onix 400. 

I need to figure out how to check it out.

```
 cvs -d:pserver:anonymous@gpsbabel.cvs.sourceforge.net:/cvsroot/gpsbabel login

cvs -z3 -d:pserver:anonymous@gpsbabel.cvs.sourceforge.net:/cvsroot/gpsbabel co -P modulename
```

I have CVS installed, but when I try to check it out, it asks for a password, but on their page it says nothing about a password, please help.

[https://sourceforge.net/projects/gpsbabel/develop]("https://sourceforge.net/projects/gpsbabel/develop")

---

### Post by truskhan on 2010-07-02
The solution is easy, just hit Enter when you are prompted for password. It is mentioned on [http://sourceforge.net/scm/?type=cvs&group_id=58972](http://sourceforge.net/scm/?type=cvs&group_id=58972) , good luck ;).

---

