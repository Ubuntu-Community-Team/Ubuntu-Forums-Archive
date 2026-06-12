---
title: "Please save me from Bill Gates ???? Java installation"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2007-12-19
Hello Friends I want to switch from vista to Linux any Linux will do for me and the choice was Ubuntu.
But the learning curve is bit painful, I have used lots of time now just trying install,java, ant
I hope some body will assist thanks.
I have, I thought installed java but please read my java version check command result bellow.
I have google for long time now, bought about java and ant.
a supplementary question, where can I set environment,path variables  and how ?
I am missing something because I have set my java and ant home in ect/environment

quickmind@quickmind-laptop:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
quickmind@quickmind-laptop:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.
quickmind@quickmind-laptop:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
quickmind@quickmind-laptop:~$

---

### Post by hoboy on 2007-12-19
ok, don't worry problem is solved, it was my classpath that was wrong, nothing to do with ubuntu.
Thanks

---

