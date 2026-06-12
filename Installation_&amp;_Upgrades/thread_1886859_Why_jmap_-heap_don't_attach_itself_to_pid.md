---
title: "Why jmap -heap don't attach itself to pid"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by _XoR_ on 2011-11-25
I'm using Ubuntu 11.10 x64 with openjdk6.

```

$ dpkg-query -l "*jre*"|grep "^ii"|awk '{print $1, "\t", $2, "\t", $3}'
ii 	 gcj-4.6-jre-lib 	 4.6.1-4ubuntu2
ii 	 icedtea-6-jre-cacao 	 6b23~pre10-0ubuntu5
ii 	 icedtea-6-jre-jamvm 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre-headless 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre-lib 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre-zero 	 6b23~pre10-0ubuntu5

$ dpkg-query -l "*jdk*"|grep "^ii"|awk '{print $1, "\t", $2, "\t", $3}'
ii 	 openjdk-6-doc 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jdk 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre-headless 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre-lib 	 6b23~pre10-0ubuntu5
ii 	 openjdk-6-jre-zero 	 6b23~pre10-0ubuntu5

```

And when I execute jmap I get next error:

```


$ jmap -heap 4313
Attaching to process ID 4313, please wait...
Error attaching to process: sun.jvm.hotspot.debugger.DebuggerException: Can't attach to the process


```

Same happens on my other machine that runs sun-jdk and Ubuntu 11.04.

And other java process is started by same user that executes jmap command.

Also I get same bug when using -permstat.

JVisualVM works fine, it shows all stats perfectly...

Also jmap -histo works.

Is this some bug, or what?, I'm :confused:

---

### Post by SepH1r0th on 2012-03-28
Hi, 

Are you trying to dump the core as the user that started the JVM?

For instance, if its a tomcat process you need to su to that user,

su -

su tomcat

jmap dump:file=/a/dir/tomcat/has/permissions/to/write PID

?? 

hope this helps

---

### Post by _XoR_ on 2012-04-01
That wasn't a problem, because I executed tomcat as regular user...

---

### Post by daniel.kullmann on 2012-07-17
You have to enable debugging with this command:

```
echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
```

Solution found on [http://blog.thecodingmachine.com/fr/content/fixing-java-memory-leaks-ubuntu-1104-using-jmap](http://blog.thecodingmachine.com/fr/content/fixing-java-memory-leaks-ubuntu-1104-using-jmap)

---

### Post by _XoR_ on 2012-07-17
This is epic, answer after so much time. Thanks!

---

