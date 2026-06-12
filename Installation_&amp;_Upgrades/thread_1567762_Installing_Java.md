---
title: "Installing Java"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Harris6310 on 2010-09-04
I am trying to install Java on Ubuntu. I have download the Linux (self-extracting file). But I have no idea what to do now. How do I install it?

---

### Post by howefield on 2010-09-04
Any reason for not installing it via the Partner repository ? it is the easiest method :)

It is version 6.20 as opposed to 6.21 that you have probably downloaded.

I use 64 bit, to install the .bin package and starting with the .bin file in my home folder, the commands I use look like this, if you are not using 64 bit, amend to suit.

```
cd /opt
sudo mkdir java
cd java
sudo mkdir 64
sudo mv ~/jre-6u21-linux-x64.bin /opt/java/64
sudo chmod 755 /opt/java/64/jre-6u21-linux-x64.bin
cd /opt/java/64
sudo ./jre-6u21-linux-x64.bin
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_21/bin/java" 1
sudo update-alternatives --set java /opt/java/64/jre1.6.0_21/bin/java
mkdir ~/.mozilla/plugins
ln -s /opt/java/64/jre1.6.0_21/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
```

---

### Post by jcolyn on 2010-09-04
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

After deleting any java files you downloaded..

---

### Post by Harris6310 on 2010-09-04
> **jcolyn said:**
> ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```After deleting any java files you downloaded..

When I try that, this happens:

```

harris@harris-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
[sudo] password for harris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
harris@harris-desktop:~$ 

```

Edit: Problem fixed now. :)

---

### Post by akoskm on 2010-09-04
> **Harris6310 said:**
> When I try that, this happens:

```

harris@harris-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
[sudo] password for harris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
harris@harris-desktop:~$ 

```

Edit: Problem fixed now. :****)

You need to enable the restricted software sources:
System > Administration > Software Sources.
Here check *Software restricted by copyright or legal issues*.

---

### Post by shantiq on 2010-09-04
hi there 

Java is called openjdk-6 in your synaptic System/admin/synaptic


 one could never guess that

i think you need to tick first 6 boxes


then run ```
java-version
``` in your terminal


and you will see

```
java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9pre) (6b20~pre2-0ubuntu2)
OpenJDK Client VM (build 17.0-b16, mixed mode, sharing)

```


see attached image

---

