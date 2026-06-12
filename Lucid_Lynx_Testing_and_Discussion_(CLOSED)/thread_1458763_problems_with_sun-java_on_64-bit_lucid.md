---
title: "problems with sun-java on 64-bit lucid"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by espen77 on 2010-04-20
Having some problems setting what java to use. Am I doing anything wrong, or is there a bug here somewhere?

> user@lucid:/$ sudo update-java-alternatives -l
ia32-java-6-sun 63 /usr/lib/jvm/ia32-java-6-sun
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

> user@lucid:/$ sudo update-java-alternatives -s ia32-java-6-sun
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/ia32-java-6-sun/bin/xjc
update-alternatives: error: alternative /usr/lib/jvm/ia32-java-6-sun/jre/lib/i386/libnpjp2.so for mozilla-javaplugin.so not registered, not setting.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

> user@lucid:/$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so for mozilla-javaplugin.so not registered, not setting.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

-Espen-

---

