---
title: "[SOLVED] Java problems in Ubuntu Hardy"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by TriggerIsHappy on 2008-09-30
I'm trying to install Frostwire and it won't load after the install. It keeps telling me that i need to upgrade my Java to 1.5.x or so and I've done this. It still won't work. Help please

Trigger

---

### Post by Crafty Kisses on 2008-09-30
What are the results of this command?
```
java --version
```

---

### Post by TriggerIsHappy on 2008-09-30
eric@Eric:~$ java --version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

---

### Post by WWSmith36 on 2008-09-30
To instal java

```
sudo aptitude update
sudo apt-get upgrade
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by TriggerIsHappy on 2008-09-30
Thanks, WWSmith36. That did the trick.

---

