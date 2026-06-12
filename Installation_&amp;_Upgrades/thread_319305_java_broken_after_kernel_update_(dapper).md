---
title: "java broken after kernel update (dapper)"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by giosue_c on 2006-12-15
I recently restarted my computer after the kernel update to 2.6.15-27-386.  Since then I have not been able to do certain things in java such as run inetlliJ or build my projects with ant.  I have tried several installations of java.  One is the java 5 install packaged by ubuntu

ii  sun-java5-jdk                          1.5.0-06-1                              Sun Java(TM) Development Kit (JDK) 5.0
ii  sun-java5-jre                          1.5.0-06-1                              Sun Java(TM) Runtime Environment (JRE) 5.0

the other is BEA's jRockit 1.5 JDK.  While running intelliJ both exit with the same problem:
ERROR:
java.io.StreamCorruptedException: invalid stream header
        at java.io.ObjectInputStream.readStreamHeader(ObjectInputStream.java:763)
        at java.io.ObjectInputStream.<init>(ObjectInputStream.java:278)
        at com.intellij.ide.startup.StartupActionScriptManager.b(StartupActionScriptManager.java:22)
        at com.intellij.ide.startup.StartupActionScriptManager.executeActionScript(StartupActionScriptManager.java:21)
        at com.intellij.ide.plugins.PluginManager.initClassloader(PluginManager.java:228)
        at com.intellij.ide.plugins.PluginManager.bootstrap(PluginManager.java:357)
        at com.intellij.ide.plugins.PluginManager.main(PluginManager.java:77)
        at com.intellij.ide.plugins.PluginManager.main(PluginManager.java:215)
        at com.intellij.idea.Main.main(Main.java:2)
Exception in thread "main" java.lang.AssertionError:
        at com.intellij.openapi.diagnostic.DefaultLogger.error(DefaultLogger.java:49)
        at com.intellij.openapi.diagnostic.Logger.error(Logger.java:60)
        at com.intellij.ide.plugins.PluginManager.initClassloader(PluginManager.java:340)
        at com.intellij.ide.plugins.PluginManager.bootstrap(PluginManager.java:357)
        at com.intellij.ide.plugins.PluginManager.main(PluginManager.java:77)
        at com.intellij.ide.plugins.PluginManager.main(PluginManager.java:215)
        at com.intellij.idea.Main.main(Main.java:2)


Here is the output of my ant build that no longer works:
genAll:
     [java] Generating 1 domain objects to /home/pair/trunk/devel/srcGenerated/com/foobaz/ae/insurance
     [java] log4j:ERROR Parsing error on line 1 and column 2
     [java] log4j:ERROR An invalid XML character (Unicode: 0x0) was found in the prolog of the document.
     [java] log4j:ERROR Could not parse input source [org.xml.sax.InputSource@10babaf].


However, some java programs work, and I can do simple things like compile a simple java class and run it just fine.  

Everything was working fine yesterday before the restart.  Both errors seem I/O related.  Has anyone else had any problems?  For now I am going to try rolling back to the previous kernel.

---

### Post by giosue_c on 2006-12-15
Looking at my synaptic history, I don't actually see a kernel update in the log, but I know I just got a kernel update!  Anyway.  I rolled back to a previous kernel and everything is still broken, so it must be something else.  Other updates I remember are hal and lvm, but I don't really see how that could be related.  Anyway, I have 3 other workstations that are identical.  I'm tempted to update another one to see if it has the same problem.

---

### Post by giosue_c on 2006-12-18
Well, after trying the other kernel and not finding any difference I was thinking it had to be something else.

Here is the fix I got from the intelliJ support forums.

Just delete .IntelliJIdea60/system/plugins/action.script and intelliJ works again.  Now I've gotta go figure out what is wrong with my build.  Turns out it was all just a nasty coincidence that intelliJ, and my build went screwy right after a restart for a kernel update.

Whee!

---

