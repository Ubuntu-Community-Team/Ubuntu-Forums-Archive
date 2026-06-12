---
title: "Limewire doesn't start"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by moisessalum on 2007-05-11
Hi, I am using Ubuntu Fesity Fawn, and I installed Limewire, but it doesn't start anything.
I have installed the Sun Java 5.0 Web Start and nothing. I also tried Frostwire, but still nothing, it also doesn't load my Azureus. I don't know what to do. Help Please!!!!

---

### Post by taurus on 2007-05-11
Can you try to run them from a terminal so you can paste the error messages here?

```
java -version 
limewire
frostwire
azureus
```

---

### Post by moisessalum on 2007-05-14
This is what appears when I start java -version and limewire

> King@Laptop:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
King@Laptop:~$ limewire
Starting LimeWire...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


---

### Post by taurus on 2007-05-14
Well, you need to install a newer version of java for your Feisty.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by moisessalum on 2007-05-14
It worked.
Thanks!!!!:)

---

### Post by celticbhoy on 2007-05-16
Having a slightly different problem with limewire, when it starts it asks if I want to upgrade to pro,I select later ands then just get a white window.

---

