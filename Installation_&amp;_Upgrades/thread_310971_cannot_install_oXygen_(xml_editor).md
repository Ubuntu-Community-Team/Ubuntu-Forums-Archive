---
title: "cannot install oXygen (xml editor)"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by jansenh on 2006-12-02
Hi Forum.

I tried to install the oXygen xml editor ([http://www.oxygenxml.com/)](http://www.oxygenxml.com/)), which fails on finding Java libs, I think? Under my 'System -> Preferences' menu I can find a 'Sun Java 5.0 Control Panel' that tell me that I have Java 2 Standard Edition (Version 1.5.0 (build 1.5.0_08-b03)) installed. I run a ubuntu 6.10 that was upgraded from a 6.06.


This is the return I get from the ./oxygen.sh installer:

j[FONT="Courier New"][SIZE="1"]ava.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.EventQueue.isDispatchThread(libgcj.so.70)
   at java.awt.EventQueue.invokeAndWait(libgcj.so.70)
   at javax.swing.SwingUtilities.invokeAndWait(libgcj.so.70)
   at ro.sync.exml.Oxygen.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...4 more
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.EventQueue.isDispatchThread(libgcj.so.70)
   at java.awt.EventQueue.invokeAndWait(libgcj.so.70)
   at javax.swing.SwingUtilities.invokeAndWait(libgcj.so.70)
   at ro.sync.exml.Oxygen.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...4 more
[/SIZE][/FONT]

---

### Post by tricky001 on 2006-12-04
I'm having a similar problem..

Cannot start <oXygen/>.
Due to:java.lang.NoClassDefFoundError
com.jidesoft.swing.JideSwingUtilities.
java.lang.NoClassDefFoundError: com.jidesoft.swing.JideSwingUtilities
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.jidesoft.plaf.eclipse.EclipseMetalUtils.initComponentDefaults(Unknown Source)
   at com.jidesoft.plaf.LookAndFeelFactory.a(Unknown Source)
   at com.jidesoft.plaf.LookAndFeelFactory.installJideExtension(Unknown Source)
   at ro.sync.ui.application.ApplicationLauncher.B(Unknown Source)
   at ro.sync.ui.application.ApplicationLauncher.launch(Unknown Source)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at ro.sync.exml.Oxygen.main(Unknown Source)

---

### Post by baz on 2006-12-06
I think there's something wrong with Ubuntu Java.

I can't run Shredder Linux chess application because
of the same error: 

===================================================
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
===================================================

At first I thought it was Automatix that screwed up so
I reinstalled Java by hand but it's still wrong.

H-E-L-P  !!!

---

### Post by conorharris on 2007-05-07
I've had this same problem in the past. I have Oxygen version 8.2 working fine under Feisty now. I went to [http://www.oxygenxml.com/download.html](http://www.oxygenxml.com/download.html) and downloaded the "All (Linux, Unix,etc.)" package. I unpacked it, moved to the new folder and ran 

```
sh oxygen.sh
```

I pasted in my license key and everything is peachy.

I hope this helps!

---

### Post by offmessage on 2007-06-21
Guys

oXygen is not compatible with libgcj.  You need to ensure that you have Sun Java (sun-java6-jre) installed.

```
sudo aptitude install sun-java6-jre
```

If you still have the problem it is likely that your default java is still libgcj.  You can fix this by:

```
sudo update-alternatives --config java
```

and selecting ```
/usr/lib/jvm/java-6-sun/jre/bin/java
``` from the list

---

