---
title: "How can i install a java c compiler?"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by ainigma on 2007-11-20
Well...I'm trying to use the command ''ant gen'' and the command ''ant compile'' for an installation.Ths sytem tells me that 
''Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-1.5.0-sun-1                    .5.0.08/lib/tools.jar
Buildfile: build.xml

BUILD FAILED
Target `gen' does not exist in this project."


for the compile command the system tells me that 

''Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/lib/tools.jar
Buildfile: build.xml

init:

compile:
    [javac] Compiling 191 source files to /opt/OpenIMSCore/FHoSS/bin

BUILD FAILED
/opt/OpenIMSCore/FHoSS/build.xml:44: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK"


what can i do....the synaptic manager choice does not seem to help

---

### Post by taurus on 2007-11-20
Did you install sun-java6-jdk (instead of sun-java6-jre)?

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by ainigma on 2007-11-20
trying...to do it now

---

