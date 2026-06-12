---
title: "dpkg error"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by amendt on 2012-08-10
I get the following error
[I]Errors were encountered while processing:
 libxslt1.1
 libxslt1.1:i386[/I]
I think it is because I am running an AMD 64 chip and somehow this libxslt1.1 has a reciprocity dependency with libxslt1.1:i386 

I can's seem to remove either file.
Help.

---

### Post by raja.genupula on 2012-08-10
what actually you are doing there ? ? trying to install/removing ? please give us the complete information ,:D

---

### Post by amendt on 2012-08-10
I am trying to solve why my system wouldn't update.

---

### Post by raja.genupula on 2012-08-11
open your terminal and type as 
```
 sudo apt-get update 
```

give us the output of that command and tell us whats it giving you .

---

### Post by amendt on 2012-08-12
libxslt1.1 : Breaks: libxslt1.1:i386 (!= 1.1.26-8ubuntu1) but 1.1.26-8ubuntu1.1 is installed
 libxslt1.1:i386 : Breaks: libxslt1.1 (!= 1.1.26-8ubuntu1.1) but 1.1.26-8ubuntu1 is installed
E: Unmet dependencies. Try using -f.

Which I did.

---

### Post by raja.genupula on 2012-08-15
open up your terminal and type this

```
sudo apt-get install -f

```

---

