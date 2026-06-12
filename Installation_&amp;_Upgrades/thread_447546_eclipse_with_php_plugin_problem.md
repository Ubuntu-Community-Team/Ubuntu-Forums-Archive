---
title: "eclipse with php plugin problem"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by paulus4605 on 2007-05-18
dear 
I installed eclipse with the php plugin and the installation went ok>
I can create a new project and I'm able to create a new file.
however when I want to edit this file I get the following errormessage:
an error has occured please check the errorlog for details.
1st question  where do I find this error log?
2nd question how to solve this problem
thanks for your coop and feedback

Paul

---

### Post by Paul41 on 2007-05-18
The error may be in here.

/home/username/workspace/.metadata/.log

My first thought was that you are having a permissions problem, but if you are able to create projects and files I don't guess that is the problem. Just to be 100% sure you could open Eclipse with root permissions to see if you have the same problem.

```
gksudo eclipse
```

---

### Post by paulus4605 on 2007-05-18
still the same problem and no logfile found

---

### Post by paulus4605 on 2007-05-19
this solved the problem for me 
Ubuntu Feisty 7.04 Fix

When you try to edit a .php file using the PHPeclipse editor, you will get an error message that tells you to look in the log. This problem arises due to problem with the default JVM used in Feisty. To fix the problem:

   1. Close eclipse and at the bash prompt:
   2. sudo apt-get install sun-java6-jre
   3. sudo nano -w /etc/eclipse/java_home
   4. Insert /usr/lib/jvm/java-6-sun on the line above /usr/lib/jvm/java-gcj
   5. Close and save the file

---

