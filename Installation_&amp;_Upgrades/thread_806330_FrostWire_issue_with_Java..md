---
title: "FrostWire issue with Java."
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Surreal Killa on 2008-05-24
So I'm running a clean install of Xubuntu 8.04, I have installed xubuntu-restricted-extras and the latest version of FrostWire downloaded from their website, and when I try to run it I get this error:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0]
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
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)

Any suggestions?

* I have now installed sun-java5-jre & sun-java6-jre and still the same problem.

* Shoot, I just saw another thread on this same topic and the solution is:

sudo update-java-alternatives -s java-6-sun

---

### Post by nucleuskore on 2008-06-25
Open gedit

Open /usr/bin/frostwire
Uncomment export AWT_TOOLKIT=MToolkit
Save

Open /usr/lib/frostwire/runFrostwire.sh
Uncomment export AWT_TOOLKIT=MToolkit
Save

---

