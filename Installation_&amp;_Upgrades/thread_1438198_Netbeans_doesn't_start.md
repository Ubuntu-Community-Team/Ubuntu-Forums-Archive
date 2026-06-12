---
title: "Netbeans doesn't start"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by linusr on 2010-03-24
Installed netbeans via synaptic but when I click 'NetBeans' it doesn't open... no error nothing

Tried running 'netbeans' in terminal and it's the same!!!

Not sure how to fix this. Help is greatly appreciated.

---

### Post by 666f6f on 2010-03-24
Running from the console was a good idea.. What does it print when you run netbeans? can you post the output?

---

### Post by linusr on 2010-03-24
> **666f6f said:**
> Running from the console was a good idea.. What does it print when you run netbeans? can you post the output?

pretty much nothing in console output

> 
linusr@DeepBlue:~$ netbeans -verbose
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32	  use a 32-bit data model if available
    -d64	  use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -cacao	  to select the "cacao" VM
    -zero	  to select the "zero" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is server,
                  because you are running on a server-class machine.


    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions with specified granularity
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions with specified granularity
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                  see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
See [http://java.sun.com/javase/reference](http://java.sun.com/javase/reference) for more details.
linusr@DeepBlue:~$ 



---

### Post by 666f6f on 2010-03-24
Seems to me like a java setup problem. what is your *java -version* output? If it says anything about "OpenJDK" then, try to *sudo apt-get install sun-java6-jdk* and then *sudo update-alternatives --config java*

---

### Post by linusr on 2010-03-24
> 
linusr@DeepBlue:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)
linusr@DeepBlue:~$ javac -version
javac 1.6.0_0
linusr@DeepBlue:~$ 


netbeans should work with openjdk?

---

### Post by 666f6f on 2010-03-24
> **linusr said:**
> netbeans should work with openjdk?

Good question!

---

### Post by linusr on 2010-03-24
> **666f6f said:**
> Good question!

I was able to start netbeans as sudo but not as normal user.. tried with newly created user as well

Any file permission issue?

---

### Post by linusr on 2010-03-24
solved it!!!

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=541137]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=541137")

/etc/profile had wrong entry, possibly editd by me to make SOAP UI work

---

### Post by 666f6f on 2010-03-25
Would have never thought of that.. Thank you for sharing the solution!

---

