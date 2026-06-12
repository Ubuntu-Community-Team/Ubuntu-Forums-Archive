---
title: "Can't download,need help with Java 6 jdk...docs"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by BioLuke on 2010-06-23
Hi, I'm relatively new to Ubuntu 9.10, and have encountered a problem downloading anything. Here's the recurring error message my terminal displays:
####################################################
Setting up sun-java6-doc (6.20dlj-0ubuntu1.9.10) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u19-docs.zip jdk-6u18-docs.zip jdk-6u19-docs-ja.zip jdk-6u19-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit          [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)        now and download.  

The file should be owned by root.root and be copied to /tmp.
#####################################################
I tried finding these at Oracle/Sun/Java, and can find no such archive ".docs." 
Can anyone help me find these or something else that will work instead?
I tried Oracle's help forum, no help, just the run around.
Thanks in advance.

---

### Post by lykeion on 2010-06-26
The download link for the docs is there if you look carefully.

1. Browse to [http://java.sun.com/javase/downloads](http://java.sun.com/javase/downloads)
2. Scroll down the page to the (gray) Additional Resources header 
There you'll see a download link for Java SE 6 Documentation
3. Click on it and follow the instructions to download jdk-6u18-docs.zip
4. Open a terminal and go to the place where you downloaded it (usually ~/Desktop)
5. Change the owner/group of the archive to root:root like this:
```
sudo chown root:root jdk-6u18-docs.zip
```
6. Move the archive to /tmp like this:
```
sudo mv jdk-6u18-docs.zip /tmp
```
7. Finally repeat the installation of sun-java6-doc:
```
sudo aptitude install sun-java6-don
```
Hope this helps

---

### Post by chimiasanchi on 2010-08-01
I couldn't find that download following the above instructions, but I found it here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u18-docs-oth-JPR@CDS-CDS_Developer]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u18-docs-oth-JPR@CDS-CDS_Developer")

---

### Post by rfay on 2010-09-13
It seems that only version 21 is available now (jdk-6u21-docs.zip). However, I renamed it to jdk-6u19-docs.zip and copied it into /tmp and it seems to have worked.

---

