---
title: "frostwire for 8.04 lts"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by krysia on 2008-04-20
I have just upgraded from 7.10 to 8.04 lts and  so far it all works well with programs already installed except frostwire,I have removed it and re-installed it but I cannot get it to open.
help please.
krysia

---

### Post by atomkarinca on 2008-04-20
Can you open it with terminal and paste the output? Type this in a terminal window:

```
frostwire
```

---

### Post by markk1994 on 2008-04-20
I had that problem many times what you need to do is install SUN JRE 5

---

### Post by CyberAgeVoodoo on 2008-04-27
I am having the same problem:

cyberagevoodoo@Raptor:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f6bca66b755, pid=6200, tid=1093736784
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid6200.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  6200 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

---

### Post by atomkarinca on 2008-04-27
Type in the terminal

```
sudo update-alternatives --config java
```

change your java version and see if those work for you.

---

### Post by CyberAgeVoodoo on 2008-04-28
No luck, I first tried option 2, then option 1, and there is no joy in mudville :(


cyberagevoodoo@Raptor:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/cacao
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
cyberagevoodoo@Raptor:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fbebecbb755, pid=11896, tid=1088686416
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid11896.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 11896 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

cyberagevoodoo@Raptor:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/cacao
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/bin/cacao' to provide 'java'.
cyberagevoodoo@Raptor:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2
OOPS, your java version is too old [java = 1.4.2]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by atomkarinca on 2008-04-28
Can you try this:

```
sudo apt-get install sun-java6-jre
```

---

### Post by mjkelly on 2008-04-28
I have the same problem.

For 'sudo apt-get install sun-java6-jre'
i get its already installed messages.

Frostwire is looking in this directory:
 Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so

I didn't have that motif21 directory so i made it and then copied another version of libmawt.so into that directory and now im getting this error:

java.lang.UnsatisfiedLinkError: java.awt.Component.initIDs()V

And a bunch of references where that error exists.



Edit: I think i need to tell frostwire to look somewhere else for java but i dont know how.

---

### Post by CyberAgeVoodoo on 2008-04-28
I remember doing that already

---

### Post by CyberAgeVoodoo on 2008-04-28
I found the solution on another board: 

For anyone interested here it is

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by whistlerspa on 2008-05-02
Option 2 just worked for me

---

### Post by bigjay517 on 2008-05-04
I have tried all the above fixes to no avail.  I have amd64 version on Ubuntu if that makes a difference.  Here is my most recent attempt to launch frostwire. ```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fd2a6709755, pid=7740, tid=1083681104
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid7740.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  7740 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)

```

---

### Post by Mr_bleu on 2008-05-04
[I]Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"[/I]
Not sure which one's 1.4, still having probs with mine.

---

### Post by bigjay517 on 2008-05-04
Well the Java I am using is that one reccomened to be installed eariler in the thread.  ```
sudo apt-get install sun-java6-jre
```
That is what I am running, I also tried installing Java 5 and that still did not work.  I didn't think I would have to go all the way back to 4, but I might give that a try.

---

### Post by daniel2501 on 2008-05-08
> **CyberAgeVoodoo said:**
> I found the solution on another board: 

For anyone interested here it is

```
sudo update-java-alternatives -s java-6-sun
```

Thanks a lot. Fixed it for me!

---

### Post by fasoulas on 2008-05-24
> **CyberAgeVoodoo said:**
> I found the solution on another board: 

For anyone interested here it is

```
sudo update-java-alternatives -s java-6-sun
```

Thank you i just tried it and it worked

---

### Post by torpidnotion on 2008-05-25
Also running hardy 64-bit, having the exact same problem as bigjay517


```

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_06]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f255833a755, pid=13363, tid=1091344720
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (10.0-b22 mixed mode linux-amd64)
# Problematic frame:
# C  [libc.so.6+0x30755]  catgets+0x15
#
# An error report file with more information is saved as:
# /usr/lib/frostwire/hs_err_pid13363.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 13363 Aborted                 ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)


```

Still seeking a solution.

---

### Post by santonucci on 2008-05-28
The following was my solution to the exact same issue as mentioned above:

1.) Install Sun's version of Java:
# sudo apt-get install sun-java6-jre

2.)Then running the following command after the installation completes:
# sudo update-java-alternatives -s java-6-sun

Hope this helps someone!

-S

---

### Post by torpidnotion on 2008-05-29
Unfortunately installing sun-java6-jre and running update-java-alternatives -s java-6-sun does nothing for me, and I get the error as I posted previously.

---

### Post by torpidnotion on 2008-05-29
Running on hardy64, I ended up having to run the following to get it working:

sudo apt-get install ia32-sun-java6-bin

sudo update-java-alternatives -s ia32-java-6-sun

---

### Post by josteinaj on 2008-06-05
> **torpidnotion said:**
> Running on hardy64, I ended up having to run the following to get it working:

sudo apt-get install ia32-sun-java6-bin

sudo update-java-alternatives -s ia32-java-6-sun

thanks! That fixed this problem for me. :) (hardy x64)

---

### Post by aubreyisland on 2008-06-09
> **CyberAgeVoodoo said:**
> I found the solution on another board: 

For anyone interested here it is

```
sudo update-java-alternatives -s java-6-sun
```

This worked for me!

---

### Post by torpidnotion on 2008-06-09
It doesn't work for 64-bit ubuntu.
My solution I posted earlier works for 64-bit.

---

### Post by Therion on 2008-06-09
> **torpidnotion said:**
> [the] solution I posted earlier works for 64-bit.Yes, yes it does.  Many thanks for it too.

I've been booting into XP in a virtual box to use Frostwire of late...  But no more!!

---

