---
title: "Eclipse Problems..."
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Cptnrodent on 2008-03-13
Hello all... I'm new to the forums and Linux, but here's the rundown.  Just switched to Ubuntu Gutsy because that's the environment we're using in my CS courses at Bucknell U.  I got all the good stuff figured out, I'm mucking about in my music library, watching movies, checking email, etc...but I can't seem to get Eclipse to work to do any of my actual HW.  Erm..

I'm using Eclipse 3.2.2 and j2re/j2sdk 1.4.  This is the message I get...

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...not found
  testing /usr/lib/jvm/java-1.5.0-sun...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/core/launcher/Main (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

Any thoughts would be greatly appreciated... Thanks.

---

### Post by kellemes on 2008-03-13
Will this thread help?
[http://ubuntuforums.org/showthread.php?t=368058]("http://ubuntuforums.org/showthread.php?t=368058")

Also.. as stated in the error-message(s) you need to enter in terminal..
```

sudo touch /usr/local/lib/eclipse/.eclipseextension
sudo chmod 2775 /usr/local/lib/eclipse/.eclipseextension
sudo chown root:staff /usr/local/lib/eclipse/.eclipseextension
```

---

### Post by Cptnrodent on 2008-03-13
That thread was helpful in understanding what's going on, but I'm still having the same problems.  (And I ran the commands it told me to originally, too...don't know how I missed that :-k
Eclipse is pointed in the right direction of my JVM, but there's this other error after it gets ahold of it.  

> Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/core/launcher/Main (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

UnsupportedClassVersionError? does this version of Eclipse not support j2se1.4? ...

---

### Post by kellemes on 2008-03-13
Maybe you need to set the default JVM?

```
sudo update-alternatives --config java
sudo update-alternatives --config javac
```

Now select the appropriate versions, hope it works.

---

### Post by Cptnrodent on 2008-03-13
Ok, I just uninstalled and purged everything to do with java and Eclipse, then went to the Sun and Eclipse websites and downloaded the latest versions.  Then I did what you said, and pointed it in the right direction.  Works like a charm.  Guess I have to stop playing Konquest now...

Thanks for the help!

---

### Post by ansicplusplus on 2008-03-15
Hy,

it might help to install the package sun-java6 and to create a file .eclipse/eclipserc with the following contents```
JAVA_HOME=/usr/lib/jvm/java-6-sun
```
It seems that eclipse has trouble with the default jvm.

Yours, ansicplusplus

---

