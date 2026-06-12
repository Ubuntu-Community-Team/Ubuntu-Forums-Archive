---
title: "Unable to configure  Sun JDK on Ubuntu 9.10"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by swiftguy121 on 2010-01-07
Hello,

Installed SUN JDK usnig the following command on Ubuntu[ 9.10 Karmic Koala]. It seems already there is a default version(open jdk) but i want to use SUN JDK for Android development.

when i run a simple program i get the following error
# javac HelloWorld.java
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>

I guess the system is getting confused between the sun jdk and open jdk versions ?

I also ran 
$sudo update-java-alternatives -s java-6-sun

update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.


Kindly help me out in configuring the JAVA development environment.

Thanks in advance!

---

### Post by darkod on 2010-01-07
Unless you are asking about some specific configuration settings, all I did was open Synaptic Package Manager, type jdk in the search box, and select to install sun-java6-jdk. It will select the dependent packages automatically.
That should be it.
Is that the jdk you want?

---

### Post by Mighty_Joe on 2010-01-07
It sure looks like you installed the JRE, not the JDK.  You may have to take the extra step of telling the java-alternatives system which Java to use: [see here]("https://help.ubuntu.com/community/Java").  java-alternatives will also show you which Java versions are available.
Be aware that the Sun JDK will not be updated for Karmic, not even for security updates.  If you want to use Sun's version, you'll have to [install it yourself]("http://sites.google.com/site/easylinuxtipsproject/java").

---

