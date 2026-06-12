---
title: "What is wrong with Java Environment Path?"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by esya on 2010-05-27
I set up java-6-sun-1.6.20 by using Synaptic Package Manager and I updated PATH variable and added JAVA_HOME by chancing /etc/environment file.

My environment file:
[PHP]
#begin
JAVA_HOME = /usr/lib/jvm/java-6-sun-1.6.0.20/
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.20/bin/"
#end
[/PHP]When I wrote echo $JAVA_HOME I got one empty line.

And I tried java. I got error. 

[PHP]~$ java
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
[/PHP]I did not understand what is wrong. What can I do to fix the problem?

---

### Post by dino99 on 2010-05-27
is java_home created ? why have you change the path ?

---

### Post by esya on 2010-05-27
I tired  ```
~$ echo $JAVA_HOME
```  in the terminal and I cannot see any result.
I think Java_home is not created.


I chanced path because I searched the error of Java command which is:

```
~$ java
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

```in the web and they were saying that add your Java path to the path environment and add Java_Home to the etc/environment file. So I added Java path to the end of  my path variable and I add  Java_Home variable to the beginning of the environment file.

---

