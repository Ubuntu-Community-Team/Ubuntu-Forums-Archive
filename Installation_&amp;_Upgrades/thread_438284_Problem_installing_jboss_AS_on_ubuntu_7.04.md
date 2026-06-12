---
title: "Problem installing jboss AS on ubuntu 7.04"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by l.avoledo on 2007-05-09
Hi

Can somebody help me?

I'm trying to install JBOSS AS but when i launch java -jar jems-installer-1.2.0.GA.jar i get this error:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.Font.tk(libgcj.so.70)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.70)
   at java.awt.Font.<init>(libgcj.so.70)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.70)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.70)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.70)
   at javax.swing.UIManager.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at com.izforge.izpack.installer.GUIInstaller.loadLookAndFeel(GUIInstaller.java:301)
   at com.izforge.izpack.installer.GUIInstaller.<init>(GUIInstaller.java:116)
   at java.lang.Class.newInstance(libgcj.so.70)
   at com.izforge.izpack.installer.Installer.main(Installer.java:63)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: impossibile aprire il file oggetto condiviso: Nessun file o directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...15 more

Thanks
Lorenzo

---

### Post by meor on 2007-05-31
I too experience the same response when I try to install a software that need java. Pls, if anyone can help ?

---

### Post by shrek on 2007-07-18
I believe that the problem may be that Ubuntu comes with Free Java but the installs that you are trying to run need sun java packages. 

Here are instructions on installing Sun Java to replace Free Java 
[https://help.ubuntu.com/community/Java?highlight=%28Java%29](https://help.ubuntu.com/community/Java?highlight=%28Java%29)

---

### Post by orotrev on 2007-09-27
The installer is trying to open a GUI window which it cannot. Either install ubuntu with GUI or do not use the jems installer

---

