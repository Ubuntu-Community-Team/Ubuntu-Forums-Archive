---
title: "No Java in Firefox"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmiller1977 on 2010-03-27
Has anyone else had issues with Firefox and Java?

I installed a fresh copy of 10.04 and Java doesn't appear to work.  No plugins in firefox for Java are listed even though JRE is loaded.

I can use IcedTea, but prefer real Java.

Anyone?

---

### Post by sgosnell on 2010-03-27
Try this:```
sudo apt-get install ubuntu-restricted-extras
```Worked for me.

---

### Post by kuvanito on 2010-03-27
you can try this:
1-sudo apt-get install sun-java6-plugin
2-sudo update-java-alternatives -s java-6-sun

or

1-sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


or

INSTALL (download java bin to home folder,not the RPM)
1-cd /opt
2-sudo mkdir java
3-cd java
4-sudo mkdir 32
5-sudo mv ~/jre-6u18-linux-i586.bin /opt/java/32
6-sudo chmod 755 /opt/java/32/jre-6u18-linux-i586.bin
7-cd /opt/java/32
8-sudo ./jre-6u18-linux-i586.bin
9-yes
10-sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32 jre1.6.0_18/bin/java" 1
11-sudo update-alternatives --set java /opt/java/32/jre1.6.0_18/bin/java
12-mkdir ~/.mozilla/plugins
13-sudo apt-get remove icedtea6-plugin
14-rm ~/.mozilla/plugins/libjavaplugin_oji.so
15-rm ~/.mozilla/plugins/libnpjp2.so
16-ln -s /opt/java/32/jre1.6.0_18/lib/i386/libnpjp2.so ~/.mozilla/plugins/
17-http://java.com/en/download/installed.jsp
REMOVE
1-gksudo nautilus
2-open opt folder and delete Java folder
3-rm ~/.mozilla/plugins/libjavaplugin_oji.so
4-rm ~/.mozilla/plugins/libnpjp2.so


all is fine here:P:P:P

---

### Post by gmiller1977 on 2010-03-27
Thanks for the reply - both of you.

kuvanito I tried your suggestion previous to posting, and was informed by apt-get that the package had been "updated" or "discontinued"

sgosnell I'm trying your suggestion now.

Out of curiosity, why would these packages be "restricted" given how important they are? :)

I'll post if it works.  

Again, thanks to both of you for your suggestions!

---

### Post by kuvanito on 2010-03-27
on my 3er sugg it will work 'cause it's straigh from java sun microsystems
and it's an independent way of doing it not from canonical

---

### Post by Uncle Spellbinder on 2010-03-27
You can't miss with this.

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-)

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-)

---

### Post by sgosnell on 2010-03-27
They are restricted because they're not open source, they're proprietary.

---

