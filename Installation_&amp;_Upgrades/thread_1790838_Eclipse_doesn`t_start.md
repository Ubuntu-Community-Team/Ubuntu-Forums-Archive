---
title: "Eclipse doesn`t start"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by calin_ionut on 2011-06-25
Hello! I have a problem...i want to use sun java and eclipse in ubuntu 11.04 and the problem is that eclipse is not starting:

```

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/calin/Applications/eclipse-jdk/jre/bin/java
java in your current PATH

```

what i do:

    Delete all installations of Java.
    Install the Java SDK (self-extracting) into /opt/jdk1.6.0_26 
    Create a symbolic link: ln -s /opt/jdk1.6.0_26 /opt/jdk

    Edit $HOME/.bashrc:

    JAVA_HOME=/opt/jdk
    PATH=$PATH:$HOME/bin:$JAVA_HOME/bin

    Logout and log back in.

In console if i use the command

```

java -version 

``` 
the result is
```

java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)

```

so that`s mean the java is set correct in my PATH


So what could be the problem????:confused:

---

### Post by robertor on 2011-07-22
Same problem here. From the bash works perfect, but if i add a launcher in gnome, it give the message
```
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/calin/Applications/eclipse-jdk/jre/bin/java
java in your current PATH
```

Any hint?
greets,
Roberto

---

### Post by calin_ionut on 2011-07-24
I removed all java installation and then i installed this way:

```

sudo add-apt-repository ppa:ferramroberto/java

```

```

sudo apt-get update

```

```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

```


Now everything works fine.

Cheers!:D

---

### Post by robertor on 2011-07-24
Yes, but what about if i a want to use a differrent version of java, different from the package.
I have solved in this way:
i have added an symbolic link to the  Java Run Environment
In my case, the eclipse is on the path
```
/home/roberto/herramientas/eclipse
```
and i  do the following:
Change to the path of eclipse
```
cd /home/roberto/herramientas/eclipse
```
I create a directory called jre
```
mkdir jre
```
Change to the directory that i create
```
cd jre
```
And do a symbolic link to the xternal virtual machine, that i downloaded from Sun/Oracle
```
ln -s /opt/jdk1.6.0_20/jre/bin/ bin
```

it works perfect...

Greets,
Roberto

---

