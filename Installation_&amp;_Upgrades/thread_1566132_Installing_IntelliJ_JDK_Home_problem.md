---
title: "Installing IntelliJ JDK Home problem"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by fashaikh on 2010-09-02
Hi!
I am facing a problem that has made my life miserable. I am using Ubuntu 10.04 and I have download the java jdk 6 by the command
[COLOR=#2e496b]sudo apt-get install sun-java6-jdk [/COLOR]
I can see the java version by java -version 
 
I downloaded the intellij Idea and extracted in my /work folder. 
 
Secondly I tried
[COLOR=#2e496b]export JDK_HOME="/usr/lib/jvm/java-6-sun/" [/COLOR]
[COLOR=#2e496b]and [/COLOR][COLOR=black]started ./idea.sh but it is giving me error[/COLOR]
 
Cannot find Java Home or JDK Home and IDEA Home 
something like that. 
 
I just dont know what Am I missing.
Please help me in this regard as I am already late for work I was supposing to be doing.
 
Thanks

---

### Post by lykeion on 2010-09-02
Have you tried to edit the startup script and added the JDK_HOME line there?

The startup script idea.sh is a text file in the bin subfolder of the idea folder: 
<idea_install_folder>/bin/idea.sh

Open it up in a text editor and under this:
```
# -------------------------------------------------------------------
# Before you run IntelliJ IDEA specify the location of the
# JDK 1.6 installation directory which will be used for running IDEA
# -------------------------------------------------------------------
```
add this:
```
export JDK_HOME=/usr/lib/jvm/java-6-sun
```

Works for me anyway...

---

### Post by OwnSurname on 2010-09-09
Hi fashaikh,
I ended up in the same situation. What the output says it's correct, you're pointing to Sun's Java JRE and not to the JDK. But the path you gave is correct too. The problem is that you don't have the JDK installed at all under the same folder, but only the JRE (that's what you check with java -version).
And that's because funny Ubuntu guys moved Sun's JDK into Partner repository [1]. You've to add the Partner repository, and then install the JDK (sudo apt-get install sun-java6-jdk). That should work, hope it helps.

1. [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

---

### Post by nasims on 2010-10-17
Hi
I install intellij idea in suse and run this command:
export JDK_HOME=$JAVA_HOME

when I   run this command: ./idea.sh i see this error:
Exception in thread "main" java.lang.NoClassDefFoundError: com.intellij.util.lang.ClassPath
   at java.lang.Class.initializeClass(libgcj.so.9)
   at com.intellij.util.lang.UrlClassLoader.<init>(UrlClassLoader.java:51)
   at com.intellij.ide.ClassloaderUtil.initClassloader(ClassloaderUtil.java:102)
   at com.intellij.ide.Bootstrap.main(Bootstrap.java:23)
   at com.intellij.ide.Bootstrap.main(Bootstrap.java:19)
   at com.intellij.idea.Main.main(Main.java:38)
Caused by: java.lang.ClassNotFoundException: sun.misc.Resource not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:../lib/bootstrap.jar,file:../lib/util.jar,file:../lib/jdom.jar,file:../lib/log4j.jar,file:../lib/extensions.jar,file:../lib/trove4j.jar,file:/usr/lib64/jvm/java/lib/tools.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.9)
   at java.lang.ClassLoader.loadClass(libgcj.so.9)
   at java.lang.ClassLoader.loadClass(libgcj.so.9)
   at java.lang.Class.initializeClass(libgcj.so.9)
   ...5 more

please help  me.:(

---

