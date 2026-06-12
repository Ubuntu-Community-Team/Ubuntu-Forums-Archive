---
title: "How will I run my java code in Ubuntu 8.04"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by cupid on 2010-06-11
Hello everyone ,
I am new to Linux environment. 
I wanted to run some Java code but dont know how to run it !
Could anyone help me !  
:p:p:p

---

### Post by BoneKracker on 2010-06-11
Assuming Java is set up on your machine already, which I would assume Ubuntu takes care of for you:
```
java <application name>
```

---

### Post by cupid on 2010-06-11
But how would i know is java installed in my system.
also i have made a folder on desktop named codes. and some code is there within the folder.how will i run that code ?

---

### Post by cupid on 2010-06-11
I installed sun-java6-bin sun-java6-jre from synaptic.
and after the installation i typed java -version on the terminal window 
it gave me the following result :
[B][COLOR=Yellow]
[COLOR=Black]mac@mac:~$ java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)[/COLOR][/COLOR][/B][COLOR=Black]
[/COLOR]
so now i want to know that do i have to install jdk also ie., sun-java6-jdk 

I AGAIN ASK :
i a have a folder in desktop named codes where my java code is there.
How will i compile it ?

---

### Post by GregBrannon on 2010-06-12
You've been asking how to RUN the code.  That's different than compiling.

To compile:

```
javac SourceFile.java
```

---

