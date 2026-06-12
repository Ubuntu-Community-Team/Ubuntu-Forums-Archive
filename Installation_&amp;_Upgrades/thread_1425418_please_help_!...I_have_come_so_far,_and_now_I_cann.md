---
title: "please help !...I have come so far, and now I cannot run Java class in terminal"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by honey toast on 2010-03-09
Hi , 

After about 2 weeks of fiddling with my class path settings and the environment variables, I was able to get my laptop to recognise my sun jdk download. 
```

  Selection    Path                                  Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-sun/jre/bin/java   63        auto mode
* 1            /opt/java/32/jdk1.6.0_18/bin/java      1         manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manual mode



```

Only now I seem to have another problem. I am trying to run a simple java app from inside of my bash terminal.
 ```
public class Hya {
 
    public static void main(String[] args) {
        
        
        
        System.out.println("Hello");
        
        
        System.out.print("pepper steak");
                
    }
        
        
    }



```
here's what it looks like in terminal
```


Rodney@tomatoe://home/rodney/workspace/Data_structersChapter1/src/arrays$ ls
Currency.class  Currency.java



```
and I get this when I try to java Currency

```


Exception in thread "main" java.lang.NoClassDefFoundError: Currency (wrong name: arrays/Currency)
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClassCond(ClassLoader.java:632)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:616)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:283)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: Currency.  Program will exit.



```

so far, I have already tried to modify my bash.bashrc file by putting this in there:
```

export JAVA_HOME='/opt/java/32/jdk1.6.0_18/bin'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jdk1.6.0_18/bin
/bin:$PATH


```

but that did not change anything for the good.

I also put this into my /etc/environment file:```


PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/  /usr/games:/usr/lib/jdk1.6.0_18/bin"


```

I'm now at my witts end, and I don't want to spend another 2 weeks on this simple task. Is there anyone that can direct me to the answer that I'm looking for?

---

### Post by GregBrannon on 2010-03-09
The java filename has to be the same as the main class, so in your case, your source file should be called Hya.java (case matters.)

Then the command to compile the source is,

```
javac Hya.java
```

From there, you should be able to use the command

```
java Hya
```

in a script file, assuming the script can find the Hya file.

---

