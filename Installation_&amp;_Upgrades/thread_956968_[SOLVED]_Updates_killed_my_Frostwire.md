---
title: "[SOLVED] Updates killed my Frostwire"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by balagosa on 2008-10-23
The error produced by frostwire in Console:

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading FrostWire:
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
	at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

```

The output produced by ** update-alternatives --list java:**
```
/usr/lib/jvm/java-6-openjdk/jre/bin/java
/usr/lib/jvm/java-6-sun/jre/bin/java
```


I know the error is related with **Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/motif21/libmawt.so** But I do not know what the hell to do with it.

---

### Post by kostkon on 2008-10-23
I think Frostwire needs Sun Java to work well. I assume you got the update for Sun Java that came a few weeks ago. This update resets the system Java to the OpenJDK one.

Thus, to set again the Sun Java as the default Java in your system, open a terminal and give
```
sudo update-java-alternatives -s java-6-sun
```
it will ask you for a password, give yours.

---

### Post by balagosa on 2008-10-23
That solved it, time to pop it!

:popcorn:

---

