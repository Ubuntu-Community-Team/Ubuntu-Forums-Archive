---
title: "Installing the software GATE on Ubuntu 12.10"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by arv100kri on 2013-02-26
Hello all,

Firstly I love the Ubuntu forums and have got answers to many of my questions through them. But here is a very puzzling problem I have been struggling with for the past few hours.

I am trying to install this tool called GATE ([http://gate.ac.uk/download/](http://gate.ac.uk/download/)) via its generic installer which is basically a JAR file. The installation proceeds fine, but when I open the application, none of the text components of the Swing frame are rendered (please see the attached screenshot). Here are a few things I tried:
1) I downloaded and installed Sun's JDK and JRE. Also I set my $JAVA_HOME to the appropriate folder.
```

$ echo $JAVA_HOME 
/usr/lib/jvm/jdk1.7.0

```

and also
```

$ java -version
java version "1.7.0_15"
Java(TM) SE Runtime Environment (build 1.7.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 23.7-b01, mixed mode)

```

2) Tried the same installer on windows, but it seems to render perfectly (with all the text)! Something like this.
[IMG]http://upload.wikimedia.org/wikipedia/commons/0/0a/GATE5_main_window.png[/IMG]

Is there a solution for this problem?
Thanks in advance.

---

### Post by MAFoElffen on 2013-02-26
Are you running just the openjdk-7? Or with the Oracle java 7 jdk added as an alternate?

Was wondering if it spec's "Oracle" java v7, instead of just java version.

You know you can have the openjdk installed along with the Oracle java jdk/jre as an alternate right? That way it will first try the opnjdk's jre, and if something spec's Oracle's version instead, it will fallback to that...

---

### Post by arv100kri on 2013-02-26
Yes. I tried that. First I had open-jdk and then I tried it with Oracle's JDK (guess its not Sun anymore!). Both do not work however.

Also I tried previous versions of Java (the ones which GATE support) and still it doesnt work. I am unable to zero in on the actual cause of the problem.

---

