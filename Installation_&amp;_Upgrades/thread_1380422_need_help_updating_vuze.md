---
title: "need help updating vuze"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by SGC622 on 2010-01-13
i installed vuse on my computer and when i  open it up it says i need to upgrade and gives me a link, i downloaded the update and   opened a file saying updateAzureus and it had a command to type into terminal which said     

> scott@Home:~$ sudo java -cp ./plugins/azupdater/Updater.jar org.gudy.azureus2.update.Updater updateonly `pwd` ~/.azureus
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/update/Updater
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.update.Updater
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
Could not find the main class: org.gudy.azureus2.update.Updater. Program will exit.
Is this fixable? if so how thank you

---

### Post by andou on 2010-02-07
I hope so... I'm having the same problem - posting here now to be able to find it again, if I find a solution.\

edit: OK, I am not sure if this is the best way, but it worked for me.

First, I clicked on 'Update Now' in Vuze which opened a new browser window with a link to download the newest version.

That gave me Vuze_installer.tar.bz2 which I extracted.

Inside there was a readme.txt:
> REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.

So, I opened up Synaptic Package Manager and marked Vuse for uninstall, then searched for Sun Java and installed it.

Then, I clicked the file azureus in the extracted directory (where the README.txt file was).

That worked for me. There's got to be a 'better' way, but I hope that helps until you (we) find it.

---

### Post by DeadlyOats on 2010-02-17
Should I do all of that to update Vuze, or will the Ubuntu community come up with an update for it that I can get through Synaptic Package Manager?

Shall I wait, or not wait?

---

