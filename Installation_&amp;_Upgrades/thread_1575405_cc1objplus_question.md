---
title: "cc1objplus question"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by geckogenome on 2010-09-15
Hello,
I am trying to compile a program originally made for Mac, but there are instructions for compiling in Linux, which is the use make.  However, I get this error:

g++: error trying to exec 'cc1objplus': execvp: No such file or directory

I have installed g++ (sudo apt-get install g++) and build-essential, but to no avail.

Does anybody have an advice?  

Thank you!

---

### Post by spjackson on 2010-09-16
I think you need the gobjc package, the GNU Objective-C compiler.

---

