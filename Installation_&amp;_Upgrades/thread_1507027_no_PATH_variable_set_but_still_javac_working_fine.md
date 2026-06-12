---
title: "no PATH variable set but still javac working fine"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by daudiam on 2010-06-11
Hi

I thought that setting up the PATH variable was a must if we wanted to use java or javac commands on linux (preferably in the bashrc file), but I am able to use these commands anywhere without setting up the PATH variable.. Similarly, without specifying . in the CLASSPATH variable (in  fact, not specifying the CLASSPATH variable at all), I am able to access class files in the same directory. How is it possible ?

---

### Post by daudiam on 2010-06-14
There was a javac and java file in the /usr/bin directory which are automatically searched for any command. But I was confused because I thiught the path should have been to Sun's java's bin.
Actually, when I typed ls -l ```
/usr/bin/javac
``` it showed that the javac file here is actually a link to the /etc/alternatives directory's java. In the /etc/alternatives directory I typed ```
update-alternatives --list javac
```, I got the actual location of the javac. The alternatives system is there to present the user with a single interface for accessing different programs, i.e. he could type javac to invoke the javac of any of Java's versions that are installed.

As for the classpath, the default class path is the current directory.

---

