---
title: "java plugin for firefox"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by asemench on 2013-05-06
I am runnung Ubuntu 13.04 64 bit version. 

I would appreciate any suggestion on how to get java plugin running under Firefox. Any java plugin would be fine, not only Icedtea.

I have installed IcedTea plugins from the Ubuntu software center however Icedtea does not apprear in the Firefox plugin menu neither java is working. I have tried uninstalling and installing all java-related items.

Here are the alternatives that I have for Java:
------------------------------------------------------------
* 0            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      automatic
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual
  2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      manual

Thank you in advance.

---

### Post by zeljkojagust on 2013-05-06
Check this link: [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by slickymaster on 2013-05-06
To enable Oracle's Java plugin in your Firefox browser, just copy these lines into a script, and run it:
```
JAVA_HOME=/usr/lib/jvm/jdk1.7.0
MOZILLA_HOME=~/.mozilla
mkdir $MOZILLA_HOME/plugins
ln -s $JAVA_HOME/jre/lib/amd64/libnpjp2.so $MOZILLA_HOME/plugins
```

Note that you have to change the value of JAVA_HOME so that it correctly points to your installation of the JDK.

Make the script executable, by typing in ```
chmod +x name_of_script
```
Run the script using the command ```
./name_of_script
```

You can also look up the address ```
about:plugins
``` in Firefox to get the list of plugins installed in your browser.

---

### Post by QIII on 2013-05-06
A much simpler method than either already suggested would be to go to the Java wiki in my signature, "Oracle Java 7", "Command line methods" and follow the link "Using webupd8.org's strikingly simple method"

Best wishes.

---

### Post by asemench on 2013-05-07
Thank you all for quick responce. Java is up and running "using webupd8.org" link. Here is the direct link if anyone may need it.

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

