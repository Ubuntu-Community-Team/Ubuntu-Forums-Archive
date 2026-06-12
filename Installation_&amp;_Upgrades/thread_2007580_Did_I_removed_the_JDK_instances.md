---
title: "Did I removed the JDK instances?"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by masterserver on 2012-06-21
Hi to everyone

Recently I installed JDK in my Ubuntu 12.04. The problem is that I installed more than one instance of JDK until I managed to make it work. I think I installed two .sh filed which I downloaded from oracle's website and two instances from the software center of Ubuntu. Now I am trying to clean up everything and make a right installation of the jdk. I think that I have managed to delete the isntances by removing the folders from the /usr/lib/jvm/*jdk*

When I am running the command ```
java -version I get
```
```
java version "1.7.0_04"
Java(TM) SE Runtime Environment (build 1.7.0_04-b20)
Java HotSpot(TM) 64-Bit Server VM (build 23.0-b21, mixed mode)
```


when I run the command ```
javac -version I get
```


```
The program 'javac' can be found in the following packages:
 * default-jdk
 * ecj
 * gcj-4.6-jdk
 * openjdk-6-jdk
 * gcj-4.5-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>
```


What does this means? Do I have uninstalled all the jdks?

And also when I run the command sudo update-java-alternatives -l
then I get

```
java-1.6.0-openjdk-amd64 1061 /usr/lib/jvm/java-1.6.0-openjdk-amd64
java-1.7.0-openjdk-amd64 1051 /usr/lib/jvm/java-1.7.0-openjdk-amd64
```

but there is not such folders in the /usr/lib/jvm/ directory. Is it proper? Do I have to empty the sudo update-java-alternatives -l command's list?

Thanks in advance

---

### Post by masterserver on 2012-06-21
I think that I have removed the JDKs but when I run the command ```
sudo update-java-alternatives -l
``` I get this list 


```
java-1.6.0-openjdk-amd64 1061 /usr/lib/jvm/java-1.6.0-openjdk-amd64
java-1.7.0-openjdk-amd64 1051 /usr/lib/jvm/java-1.7.0-openjdk-amd64
```

Why?

I assure you that in the directory /usr/lib/jvm/ there are not files with the names java-1.6.0-openjdk-amd64 and java-1.7.0-openjdk-amd64. I deleted these files one day ago.

Any ideas?

---

