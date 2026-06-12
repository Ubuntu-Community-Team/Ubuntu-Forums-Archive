---
title: "Missing shared library file for equinox lancher"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by etrainerspy on 2011-10-25
A few days ago, I upgraded to Ubuntu 11.10.  Now I am having problems with my Eclipse programming application.  When I try to run the app, I get the following error message:
"The Eclipse executable launcher was unable to locate its 
companion shared library."

I then ran Eclipse at the command line for a more detailed explanation and got this message:
"plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.200.v20090519: cannot open shared object file: No such file or directory"

I looked for this file inside the plugins directory and discovered that the file does not exist.  I reviewed the eclipse.ini and saw that the file is referenced there:
---------------------------------------------------------------------------------------------
-startup
plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.200.v20090519
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vmargs
-Xms128m
-Xmx512m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
---------------------------------------------------------------------------------------------

I am using Eclipse version 3.7.  How can I fix this problem?  Do I need  change the referenced file to a different name or do I need to somehow download this launcher from the Eclipse website?

Also, I did a command line search (find / -name 'org.eclipse.equinox.launcher.*' 2>/dev/null) for a launcher and found these files:

/usr/lib/eclipse/dropins/sdk/plugins/org.eclipse.equinox.launcher.source_1.2.0.dist.jar
/usr/lib/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.100.dist


So, I have no idea how I am suppose to fix this.  Your help is greatly appreciated.

---

### Post by electronixid on 2011-11-07
The startup and launcher.library should be changed to the following in the ini file and you will be fine :)

```
-startup
plugins/org.eclipse.equinox.launcher_1.2.0.dist.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.100.dist
```

---

### Post by andrewlorien on 2012-08-29
an update to this answer:
i had the same problem upgrading to the next version.  the correct filenames for me were:

-startup
plugins/org.eclipse.equinox.launcher_1.3.0.dist.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.dist

it's a bit of a trick because the error message in the terminal is "plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.100.dist: cannot open shared object file: No such file or directory", but just changing that directory name doesn't fix it - the launcher doesn't exit either.

---

### Post by masuch on 2012-12-02
thanks a lot for this help.

---

