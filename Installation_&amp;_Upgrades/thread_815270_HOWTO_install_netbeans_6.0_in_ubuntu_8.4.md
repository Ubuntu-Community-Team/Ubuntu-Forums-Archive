---
title: "HOWTO install netbeans 6.0 in ubuntu 8.4"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by megazayed on 2008-06-01
plz i want to install netbeans in ubuntu 8.4 ( hardy )
i have a dvd from sun, 
my pc is intel 32 bit,
i downloadet 2 files from the dvd ( jdk-6u5-linux-i586.bin ) and ( netbeans-6.0.1-ml-linux.sh ) i installed the the first one after changing it's mood to be executable 
the problem when installing the second file ( netbeans-6.0.1-ml-linux.sh )
i chanaged it's mood too to be executable but he asks me about the jvm but i don't know where is it 
this what appeared to me :




Configuring the installer...
Searching for JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)






can any one help me plz ?

---

### Post by Partyboi2 on 2008-06-02
You can install netbeans from add/remove or by opening a terminal and typing
```
sudo apt-get install netbeans
```

---

### Post by Ameneon on 2008-06-04
A little comment here; although the instructions above indicate that JDK should be installed prior to installing netbeans, I found that installing it after worked fine in my situation at least, without any need for installing netbeans (again) after installing JDK

---

