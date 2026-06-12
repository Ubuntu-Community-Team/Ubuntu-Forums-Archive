---
title: "Problem installing Java and LucidWorks"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by hnmcc on 2010-07-04
Hi!

I am trying to install LucidWorks on Ubuntu 10.04.

At first attempt, I was told:

```
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
Try: sudo apt-get install <selected package>
```

I went for:

```
hamish@hamish-laptop:~/Downloads$ sudo apt-get install gcj-4.4-jre-headless
```

I was told that the system would update as follows:

```
The following extra packages will be installed:
  gcj-4.4-base gcj-4.4-jre-lib libgcj-common libgcj10
Suggested packages:
  fastjar gcj-4.4-jdk libgcj10-awt libgcj10-dbg
The following NEW packages will be installed
  gcj-4.4-base gcj-4.4-jre-headless gcj-4.4-jre-lib libgcj-common libgcj10
0 upgraded, 5 newly installed, 0 to remove and 64 not upgraded.
Need to get 22.2MB of archives.
```

I saw no error messages during installation.  When I tried to run Java and install LucidWorks afterwards, I was given the following messages:

```
hamish@hamish-laptop:~/Downloads$ sudo java -jar LucidWorks.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at java.awt.EventQueue.invokeLater(libgcj.so.10)
   at javax.swing.SwingUtilities.invokeLater(libgcj.so.10)
   at com.lucid.installer.InstallApplication.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.10)
   at java.lang.Runtime.loadLibrary(libgcj.so.10)
   at java.lang.System.loadLibrary(libgcj.so.10)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...3 more
```

As you can probably tell, I know nothing about Java.  What should I do to get past this point?

Thanks for your help,
Hamish

---

