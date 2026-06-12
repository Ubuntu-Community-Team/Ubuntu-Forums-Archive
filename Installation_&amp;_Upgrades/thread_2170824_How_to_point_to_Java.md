---
title: "How to point to Java"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by xigen on 2013-08-27
I want to install google refine .. and I get an error message: are you sure your JAVA_HOME environment variable is pointing to a proper java installation?
Ubuntu 13.04

meow@meow:~/Downloads$   tar xzf google-refine-2.5-r2407.tar.gz 
meow@meow:~/Downloads$ cd google-refine-2.5/
meow@meow:~/Downloads/google-refine-2.5$ ./refine
./refine: 98: [: /tmp/refine.EqxIsYp: unexpected operator
Could not find the 'java' executable at '', are you sure your JAVA_HOME environment variable is pointing to a proper java installation?
meow@meow:~/Downloads/google-refine-2.5$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * gcj-4.7-jre-headless
 * openjdk-7-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
meow@meow:~/Downloads/google-refine-2.5$

---

### Post by QIII on 2013-08-27
Hello!

Have you installed OpenJDK 7 or Oracle Java 7?

Google may expect Oracle Java 7.  If you follow the Java link in my signature, go to "Command line methods" and look for "Using webupd8.org's strikingly simple method", you'll find the easiest way to install Oracle Java 7.

Cheers!

---

### Post by xigen on 2013-08-27
Woot!   That worked perfectly.

for ref:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Many thanks.

MW

---

### Post by chavi2 on 2014-07-10
I had the exact same problem and this helped as well.
I installed a different version of java using this guide [https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)

Thanks!!

---

