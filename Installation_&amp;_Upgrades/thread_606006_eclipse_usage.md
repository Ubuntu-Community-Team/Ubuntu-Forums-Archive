---
title: "eclipse usage"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by hkullana on 2007-11-07
hi,
i am new in linux world. I installed eclipse classic 3.3.1.1 for linux to develop java software. And also i installed jdk1.6.0_03. But when i run the eclipse i gives many error like:

Error creating the view.
Reason:
org.eclipse.core.runtime.Plugin

when i want to open a java project it says:
An error has occurred.
Reason:
org.eclipse.jdt.launching.JavaRuntime

what did i missing?

thanks for help,
hkullana

---

### Post by sloggerkhan on 2007-11-07
With eclipse, I'd say first make sure you are using sun java instead of gnu java. I've also found that it tends to work better if you just dump eclipse from the eclipse website in your home folder rather than the one from the repos.

---

### Post by hkullana on 2007-11-07
i donwload the "jdk1.6" and "eclipse-SDK-3.3.1.1-linux-gtk.tar.gz" and i installed both of them. But when i click the eclipse executable is opens but it gives many errors and i cannot create projects. Also, can you please show a way that how can i change the gnu java to sun's java. 

Eclipse gives those errors:


java.lang.ClassNotFoundException: org.eclipse.core.runtime.Plugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClassInternal(BundleLoader.java:434)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass (BundleLoader.java:369)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:357)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.core.runtime.Platform.getPlugin(Platform.java:736)
   at org.eclipse.core.internal.preferences.legacy.InitLegacyPreferences.init(InitLegacyPreferences.java :43)
   at org.eclipse.core.internal.preferences.PreferenceServiceRegistryHelper.applyRuntimeDefaults(PreferenceServiceRegistryHelper.java:146)
   at org.eclipse.core.internal.preferences.PreferencesService.applyRuntimeDefaults (PreferencesService.java:337)
   at org.eclipse.core.internal.preferences.DefaultPreferences.applyRuntimeDefaults(DefaultPreferences.java:163)
   at org.eclipse.core.internal.preferences.DefaultPreferences.loadDefaults (DefaultPreferences.java:236)
   at org.eclipse.core.internal.preferences.DefaultPreferences.load(DefaultPreferences.java:232)
   at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java :307)
   at org.eclipse.core.internal.preferences.EclipsePreferences.internalNode(EclipsePreferences.java:543)
   at org.eclipse.core.internal.preferences.DefaultPreferences.node(DefaultPreferences.java:150)
   at org.eclipse.core.internal.preferences.legacy.PreferenceForwarder.getDefaultPreferences(PreferenceForwarder.java:130)
   at org.eclipse.core.internal.preferences.legacy.PreferenceForwarder.getString(PreferenceForwarder.java :636)
   at org.eclipse.ui.internal.intro.impl.model.IntroModelRoot.loadTheme(IntroModelRoot.java:260)
   at org.eclipse.ui.internal.intro.impl.model.IntroModelRoot.loadChildren(IntroModelRoot.java:177)
   at org.eclipse.ui.internal.intro.impl.model.AbstractIntroContainer.getChildren (AbstractIntroContainer.java:78)
   at org.eclipse.ui.internal.intro.impl.model.IntroModelRoot.loadModel(IntroModelRoot.java:150)
   at org.eclipse.ui.internal.intro.impl.model.loader.BaseExtensionPointManager.loadModel (BaseExtensionPointManager.java:95)
   at org.eclipse.ui.internal.intro.impl.model.loader.ExtensionPointManager.loadCurrentModel(ExtensionPointManager.java:61)
   at org.eclipse.ui.internal.intro.impl.model.loader.ExtensionPointManager.getCurrentModel (ExtensionPointManager.java:73)
   at org.eclipse.ui.intro.config.CustomizableIntroPart.init(CustomizableIntroPart.java:151)
   at org.eclipse.ui.internal.ViewIntroAdapterPart.init(ViewIntroAdapterPart.java:156)
   at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:343)
   at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:227)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart (WorkbenchPartReference.java:592)
   at org.eclipse.ui.internal.Perspective.showView(Perspective.java:2086)
   at org.eclipse.ui.internal.WorkbenchPage.busyShowView(WorkbenchPage.java:1027)
   at org.eclipse.ui.internal.WorkbenchPage.access$19 (WorkbenchPage.java:1008)
   at org.eclipse.ui.internal.WorkbenchPage$19.run(WorkbenchPage.java:3684)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchPage.showView (WorkbenchPage.java:3681)
   at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3657)
   at org.eclipse.ui.internal.WorkbenchIntroManager.createIntro(WorkbenchIntroManager.java:173)
   at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro (WorkbenchIntroManager.java:120)
   at org.eclipse.ui.internal.WorkbenchWindow$18.runWithException(WorkbenchWindow.java:2146)
   at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
   at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
   at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
   at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java :3296)
   at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2974)
   at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:801)
   at org.eclipse.ui.internal.Workbench$25.runWithException (Workbench.java:1342)
   at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
   at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
   at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages (Synchronizer.java:123)
   at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3296)
   at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2974)
   at org.eclipse.ui.internal.Workbench.runUI (Workbench.java:2309)
   at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2219)
   at org.eclipse.ui.internal.Workbench$4.run(Workbench.java:466)
   at org.eclipse.core.databinding.observable.Realm.runWithDefault (Realm.java:289)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:461)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at org.eclipse.ui.internal.ide.application.IDEApplication.start (IDEApplication.java:106)
   at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:169)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java :106)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run (EclipseStarter.java:176)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:508)
   at org.eclipse.equinox.launcher.Main.basicRun(Main.java:447)
   at org.eclipse.equinox.launcher.Main.run(Main.java:1173)
   at org.eclipse.equinox.launcher.Main.main(Main.java:1148)

-- 
Halit Erdogan

---

### Post by sloggerkhan on 2007-11-07
use sun java from the repos. Then you may have to switch which java is in use.

---

### Post by jacket87 on 2007-11-07
I had a similar problem, To fix it, I moved 
/usr/lib/jvm/java-gcj to the bottom of 
/etc/eclipse/java_home

I hope this helps

---

### Post by hkullana on 2007-11-08
hi, thanks for help but i cannot find a directory called java-gcj.

I want to tell what i did from the beginning.

i downloaded "jdk-6u3-linux-i586.bin"  and "eclipse-SDK-3.3.1.1-linux-gtk.tar.gz".
then i open the terminal and cd to the directories of these. Then i wrote "./jdk-6u3-linux-i586.bin" then it did something like installation. Then i wrote "tar -xzvf eclipse-SDK-3.3.1.1-linux-gtk.tar.gz" then it also did something like installation. Now i have a folder called eclipse, i enter it and click the eclipse executable, eclipse opens but it gives many errors in every window. It is like it cannot load some libaries. I realize that in ..eclipse/configuration directory there are some folders like "org.eclipse.core.runtime" , "org.eclipse.equinox.app" ... and these are all empty.

It is very significant for me to run eclipse and develop some software, so please help me!

---

### Post by jimmyxx on 2007-11-08
> **jacket87 said:**
> I had a similar problem, To fix it, I moved 
/usr/lib/jvm/java-gcj to the bottom of 
/etc/eclipse/java_home

I hope this helps

This worked for me, thanks!

---

### Post by jacket87 on 2007-11-08
hkullana, 
  After re-reading my previous post, I realize it was not very clear.

go the the /etc/eclipse directory and edit the file  Java_home 

in that file move the line /usr/lib/jvm/java-gcj to the bottom

I hope that helps

jacket87

---

### Post by hkullana on 2007-11-09
but i don't have a file called java_home!

---

### Post by jespdj on 2007-11-09
Run this to select the default Java on your system:
```
sudo update-alternatives --config java
```
Select Sun Java as the default Java to use.

---

### Post by bertvanbrakel on 2007-11-23
I have had the same issues. I've installed java manually and edited /etc/environment to set the JAVA_HOME but eclipse still complained. I fixed it by doing the following:

I have java installed under /opt/jdk1.6.0_10 (just unpacked the java tar.gz)

I have created a symlink /opt/java to point to /opt/jdk1.6.0_10

[INDENT]
sudo ln - s /opt/jdk1.6.0_10 /opt/java[/INDENT]

Set the JAVA_HOME and ECLIPSE_HOME environment variables (I only use the ECLIPSE_HOME variable so that I can reassign it later to point to a different eclipse installation, eclipse doesn't care and doesn't need it itself)

Edited /etc/environment to include:

[INDENT]JAVA_HOME="/opt/java"
ECLIPSE_HOME="/opt/eclipse"
[/INDENT]

You may need to logout and log back in for these variables to be set, if this doesn't work just reboot.

I have created the file /bin/java

[INDENT]sudo gedit /bin/java[/INDENT]

contents:

[INDENT]#!/bin/sh
$JAVA_HOME/bin/java $*[/INDENT]

and set the execute for all on it:

[INDENT]sudo chmod 755 /bin/java[/INDENT]

I did the same for javac and javadoc ($JAVA_HOME/bin/javac and $JAVA_HOME/bin/javadoc )

I installed eclipse under /opt/eclipse-3.3.1.1 and created symlink /opt/eclipse to it

[INDENT]sudo ln -s /opt/eclipse-3.3.1.1 /opt/eclipse[/INDENT]

I created a file under /usr/bin/eclipse 

[INDENT]sudo gedit /usr/bin/eclipse[/INDENT]

contents:

[INDENT]#!/bin/sh
$ECLIPSE_HOME/eclipse $*
[/INDENT]

and set the execute all on it

[INDENT]sudo chmod 755 /usr/bin/eclipse[/INDENT]

then I just ran eclipse

[INDENT]eclipse[/INDENT]

and it ran fine.

The important parts are the /bin/java, /bin/javac, /bin/javadoc, /usr/bin/eclipse files. Creating the symlinks /opt/java, /opt/eclipse etc is not important provided you set JAVA_HOME to point to /opt/jdk1.6 etc. However I find doing it this way all I have to do to upgrade is drop the latest java or eclipse into /opt/java-<version> or /opt/eclipse-<version> and update the symlinks and all works fine out of the box. This setup allows me to easily use a specific version later if I need to by just setting JAVA_HOME or ECLIPSE_HOME in the shell (eg `export JAVA_HOME="/opt/jdk-1.4/" ` before running java or eclipse) 

Hope this helps,
Bert

---

### Post by inanutshellus on 2007-12-19
Or you could change the link that /usr/bin/java is pointing to. 

$> cd /usr/bin
$> sudo mv java java-old
$> sudo ln -s /my/java/install/dir/java java

Voila. =)

This worked for me, anyway! But he's right, you'll want to make the symbolic link to a static source, that way it will continue working after you update your jdk version, like...

if you have java installed in /usr/local/jdk_1.6.0_03 ...

$> ln -s /usr/local/jdk_1.6.0_03 /usr/local/jdk
$> cd /usr/bin
$> sudo mv java java-old
$> sudo ln -s /usr/local/jdk/bin/java java

But yeah, this fixed my Eclipse issues after a new install of Gutsy (turned out it was looking at gij not my java, and "update-alternatives" wouldn't see it either since it wasn't "installed" just an unpacked tarball)

Hope this helps!

---

### Post by hieudc on 2007-12-30
I found another way around. 

1. Download   "Linux (self-extracting file)  filesize: 18.23 MB"   from
    [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com)
2. install java-packet from Synaptic
3. from terminal:  make-jpkg  jre-6u3-linux-i586.bin
4. it will notify the directory for: sun-j2re1.6_1.6.0+update3_i386.deb
5. from terminal:  sudo dpkg -i sun-j2re1.6_1.6.0+update3_i386.deb 
6. run Eclipse!

---

### Post by Hend on 2008-01-15
there is another easy way to eclipse :
System->Administration->Synaptic Package Manager->
from here you can search for eclipse and mark dependences

---

### Post by bertvanbrakel on 2008-02-01
yes, but then you can't have multiple versions of eclipse with multiple jvms for testing or trying out latest features etc.

---

### Post by rbradt on 2008-02-19
I was struggling with this same problem for the past week.  Thanks a lot for that solutions!!!

---

### Post by Nachtkriecher on 2008-02-20
ok... im somewhat new to ubuntu, and ive tried prcatically all the solutions you guys have offered, but it still doesnt seem to want to work. (i have the same problems as hkullana, the "error creating view" and problems creating projects.)

is it true that the "default" java must be sun-java instead of gnu-java, because i think that might still be my problem. i installed jre1.6.0_03 in /opt/java, and did all the stuff bertvanbrakel said, but when i type "eclipse" nothing happens, and when i type "java" it seems to want to use gij, which was what it said was my "1 program which provides java" when i typed "update-alternatives --config java"

thanks for reading...



EDIT:
nevermind, i got it working, it turns out my repositories in Synaptic were set all wrong. i had everything unchecked,

---

### Post by bertvanbrakel on 2008-02-21
what do the commands:

[INDENT]whereis java[/INDENT]

and

[INDENT]echo $JAVA_HOME[/INDENT]

and 

[INDENT]less /usr/bin/java[/INDENT]

produce?

---

### Post by ubestim on 2008-04-20
follow this link
[http://portal.chrost.com/index.php?view=article&id=5%3Arunning-eclipse-33-on-ubuntu-710-gutsy-gibbon&option=com_content&Itemid=17](http://portal.chrost.com/index.php?view=article&id=5%3Arunning-eclipse-33-on-ubuntu-710-gutsy-gibbon&option=com_content&Itemid=17)
It may work

---

### Post by ubestim on 2008-04-20
And this link
 [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

Ubuntu Linux Install Sun Java Development Kit ( JDK ) and Java Runtime Environment ( JRE )

---

